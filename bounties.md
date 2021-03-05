# Bounties

- investigate possibility to offer bounties for the [examples](https://github.com/galliaproject/gallia-core/blob/init/README.md#examples) to be re-written in alternative technologies (libraries and/or languages)
- doing them myself would be problematic since:
  - I'm biased
  - I wouldn't be considered an expert in them
- would be interesting in order to:
  - showcase ways in which Gallia can be improved
  - showcase ways in which the alternatives themselves can be improved
  - see how the main three goals [practicality/readability/scalability](https://github.com/galliaproject/gallia-core/blob/init/README.md#introduction), and others factors such as speed/conciseness/… shift as a result of the choice
    - for instance, what would a pure _Spark DataFrame_ alternative to the [GeneMania re-processing](https://github.com/galliaproject/gallia-genemania/blob/master/src/main/scala/galliaexample/genemania/GeneMania.scala#L49) look like? especially [the nesting-related part](https://github.com/galliaproject/gallia-genemania/blob/master/src/main/scala/galliaexample/genemania/GeneMania.scala#L98-L113)
    - likewise for e.g. (not fleshed out!): _saddle/frameless (Scala), pandas/koalas (Python), dyplr/data.table (R), tablesaw (Java), krangl (Kotlin), deedle (.NET), ..._

