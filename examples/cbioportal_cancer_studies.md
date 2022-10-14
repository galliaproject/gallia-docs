<a name="210429153512"></a><a name="cbio-studies-summary"></a>
# Web application server logic: Cbioportal's _"studies summary"_

Reproducing response for the call to obtain a summary of all studies on [cbioportal](https://www.cbioportal.org/),
arguably the most commonly used web portal for cancer data.
This is actually the very first API call made upon loading the portal's [main page](https://www.cbioportal.org/), and it is specified on their [swagger page](https://www.cbioportal.org/api/swagger-ui.html#/Studies/getAllStudiesUsingGET]).

### Original code
Flow for the code underlying the portal's actual call for _v3.6.13_ (a mix of _Java/MyBatis XML_):
- __GET__: `https://www.cbioportal.org/api/studies?projection=SUMMARY`
  - __controller__: [StudyController.java](https://github.com/cBioPortal/cbioportal/blob/v3.6.13/web/src/main/java/org/cbioportal/web/StudyController.java#L83-L126), notably: [`studyService.getAllStudies(...)`](https://github.com/cBioPortal/cbioportal/blob/v3.6.13/web/src/main/java/org/cbioportal/web/StudyController.java#L123)
    - __service__: [StudyServiceImpl.java](https://github.com/cBioPortal/cbioportal/blob/v3.6.13/service/src/main/java/org/cbioportal/service/impl/StudyServiceImpl.java#L34-L56), notably: [`studyRepository.getAllStudies(...)`](https://github.com/cBioPortal/cbioportal/blob/v3.6.13/service/src/main/java/org/cbioportal/service/impl/StudyServiceImpl.java#L37)
      - __repository__: [mybatis/StudyMapper.xml](https://github.com/cBioPortal/cbioportal/blob/v3.6.13/persistence/persistence-mybatis/src/main/resources/org/cbioportal/persistence/mybatis/StudyMapper.xml#L71-L99), basically a parameterized SQL query with JOINs+GROUP BY

### Gallia counterpart

This Gallia countpart produces the same response (web-handling excluded):

```scala		
import gallia._
import java.time.format.DateTimeFormatter
import com.google.common.base.CaseFormat

// ---------------------------------------------------------------------------
object CbioportalCancerStudies {

  def main(args: Array[String]): Unit = {
    apply(s"jdbc:mysql://localhost:3306/cbioportal?user=<MY-USER>&password=<MY-PWD>&serverTimezone=UTC")
      .take(10) // show first 10 only
      .printJsonl
  }

  // ---------------------------------------------------------------------------
  def apply(url: String): HeadS =
    url
      .streamContainer("cancer_study") // could also pass schema
      .remove("CANCER_STUDY_ID") // not used
      .transform(_.localDateTime("IMPORT_DATE"))
        .using(_.format(DateTimeFormatter.ISO_DATE_TIME).replace("T", " "))
      .rename(
          "CANCER_STUDY_IDENTIFIER" ~> "STUDY_ID",
          "PUBLIC"                  ~> "PUBLIC_STUDY",
          "TYPE_OF_CANCER_ID"       ~> "CANCER_TYPE_ID")
      .rename(CaseFormat.UPPER_UNDERSCORE.to(CaseFormat.LOWER_CAMEL, _))
      .bringAll(
        (  url
              .streamContainer("sample_list").toViewBased
              .filterBy(_.string("STABLE_ID"))
                .matches(_.endsWith("_all"))
              .retain("STABLE_ID", "LIST_ID"),
            url
              .streamContainer("sample_list_list").toViewBased
              .count("SAMPLE_ID" ~> "allSampleCount").by("LIST_ID"))
          .innerJoinOnCommonKey
          .remove("LIST_ID")
          .transformString("STABLE_ID" ~> "studyId")
            .using(_.stripSuffix("_all")) )
}

```

Of course in practice this big query could - and should - be split up into reusable components.
In the present case that would involve refactoring parts of the query into separate methods so that other endpoints may benefit from common processing.
This is the significant advantage of not switching over to an entirely different language/dialect: being able to leverage the host language's constructs as-is.

Also, given the fact that the underlying data does not change often, it would be beneficial to cache some of the lookups involved at runtime (or provide an endpoint to refresh such caches). Note that this only true for this particular application, not in general.

### Response (output)

Both produce the following response (there are ~250 such studies):

```json
[
  {
    // mostly from `cancer_study` table
	  "name": "Acute Myeloid Leukemia (TCGA, NEJM 2013)",
	  "shortName": "AML (TCGA pub)",
	  "description": "Whole-genome or whole-exome sequencing [...]",
	  "publicStudy": true,
	  "pmid": "23634996",
	  "citation": "TCGA, NEJM 2013",
	  "groups": "PUBLIC",
	  "status": 0,
	  "importDate": "2020-12-08 00:00:00",
	  "studyId": "laml_tcga_pub",
	  "cancerTypeId": "aml",
	
	// aggregated from `sample_list` table (via many-to-many `sample_list_list` table)
	"allSampleCount": 200
  },
  ...
]
```

### Origin data (database)

Schemas:

```
mysql> DESC `cancer_study`;
+-------------------------+---------------+------+-----+---------+----------------+
| Field                   | Type          | Null | Key | Default | Extra          |
+-------------------------+---------------+------+-----+---------+----------------+
| CANCER_STUDY_ID         | int           | NO   | PRI | NULL    | auto_increment |
| CANCER_STUDY_IDENTIFIER | varchar(255)  | YES  | UNI | NULL    |                |
| TYPE_OF_CANCER_ID       | varchar(63)   | NO   | MUL | NULL    |                |
| NAME                    | varchar(255)  | NO   |     | NULL    |                |
| SHORT_NAME              | varchar(64)   | NO   |     | NULL    |                |
| DESCRIPTION             | varchar(1024) | NO   |     | NULL    |                |
| PUBLIC                  | tinyint(1)    | NO   |     | NULL    |                |
| PMID                    | varchar(1024) | YES  |     | NULL    |                |
| CITATION                | varchar(200)  | YES  |     | NULL    |                |
| GROUPS                  | varchar(200)  | YES  |     | NULL    |                |
| STATUS                  | int           | YES  |     | NULL    |                |
| IMPORT_DATE             | datetime      | YES  |     | NULL    |                |
```

```
mysql> DESC `sample_list`;
+-----------------+--------------+------+-----+---------+----------------+
| Field           | Type         | Null | Key | Default | Extra          |
+-----------------+--------------+------+-----+---------+----------------+
| LIST_ID         | int          | NO   | PRI | NULL    | auto_increment |
| STABLE_ID       | varchar(255) | NO   | UNI | NULL    |                |
| CATEGORY        | varchar(255) | NO   |     | NULL    |                |
| CANCER_STUDY_ID | int          | NO   | MUL | NULL    |                |
| NAME            | varchar(255) | NO   |     | NULL    |                |
| DESCRIPTION     | mediumtext   | YES  |     | NULL    |                |
```

```
mysql> DESC `sample_list_list`;
+-----------+------+------+-----+---------+-------+
| Field     | Type | Null | Key | Default | Extra |
+-----------+------+------+-----+---------+-------+
| LIST_ID   | int  | NO   | PRI | NULL    |       |
| SAMPLE_ID | int  | NO   | PRI | NULL    |       |
```

Data:

```
mysql> SELECT * FROM `cancer_study` LIMIT 1;
+-----------------+-------------------------+-------------------+------------------------------------------+----------------+------------------------------------+--------+----------+-----------------+--------+--------+---------------------+
| CANCER_STUDY_ID | CANCER_STUDY_IDENTIFIER | TYPE_OF_CANCER_ID | NAME                                     | SHORT_NAME     | DESCRIPTION                        | PUBLIC | PMID     | CITATION        | GROUPS | STATUS | IMPORT_DATE         |
+-----------------+-------------------------+-------------------+------------------------------------------+----------------+------------------------------------+--------+----------+-----------------+--------+--------+---------------------+
|             791 | laml_tcga_pub           | aml               | Acute Myeloid Leukemia (TCGA, NEJM 2013) | AML (TCGA pub) | TCGA Acute Myeloid Leukemia, [...] |      1 | 23634996 | TCGA, NEJM 2013 | PUBLIC |      0 | 2017-11-14 00:00:00 |
```

```
mysql> SELECT * FROM `sample_list` LIMIT 1;
+---------+---------------------------------+---------------------------------+-----------------+---------------------------------------------+---------------------------------------------------------+
| LIST_ID | STABLE_ID                       | CATEGORY                        | CANCER_STUDY_ID | NAME                                        | DESCRIPTION                                             |
+---------+---------------------------------+---------------------------------+-----------------+---------------------------------------------+---------------------------------------------------------+
|    3511 | laml_tcga_pub_methylation_hm450 | all_cases_with_methylation_data |             791 | Tumor Samples with methylation data (HM450) | All samples with methylation (HM450) data (194 samples) |
```

```
mysql> SELECT * FROM `sample_list_list` LIMIT 3; -- e.g. there are 200 rows for laml_tcga_pub_all
+---------+-----------+
| LIST_ID | SAMPLE_ID |
+---------+-----------+
|    3511 |    341080 |
|    3512 |    341080 |
|    3513 |    341080 |
```

