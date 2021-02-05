#  backlog: t210121100050
<a name="t210121100050"></a>

===========================================================================
## remarks:
rk210127114128 - low tech for now (consider this as more of a quick brain dump);
	mostly to capture essential features that are missing or are currently subpar;
	will formalize process by increment (will turn into bona fide tasks that can be contributed to by others readily)
- task:
	rk210127114129 - "- pN -" indicates priority (5: low, to 1: high); if none specified, it's TBD
		rk210204193138 - more exclamation marks (!) -> more critical/difficult
		rk210204193139 - more stars (*) -> more work		
	rk210204093549 - it's generally implied that if not much detail is provided in the task, the ID should be searched for in the code
	rk210127194859 - not all tasks and ported to their corresponding place in the code yet, and vice versa
	rk210127114130 - there are a lot more "small" tasks in my notes: I'm in the process of porting them (about halfway done)
		rk210202163918 - this is in itself a big endeavor (thousands of lines of notes)
		rk210127114131 - sometimes the line between creating a task vs addressing the issue is a fine one...
rk210127114333 - for better or worse I try and ID tasks/remarks/assumptions/... as much as possible in order to make it possible to reference them elsewhere, as well as search for them; and yes, i do wake up at night screaming random timestamps.
rk210127114621 - most remarks in here will move over to the docs eventually (see t210127114652); some tags such as [mytag] are meant for me to find the relevant tag/keywords within my notes

===========================================================================
- admin: t210127114844
	- t210109164841 - determine funding mechanism going forward
	- t210109164840 - determine adequate license
	- t210127114653 - consider arxiv publication?
	- t210127133131 - switch dev environment to intellij IDEA rather than ScalaIDE? (relates to t210121165228)
	- t210129164800 - rename packages to "$TLD.gallia" once TLD is determined (see t210109164840 and t210109164841)
	- t210131152002 - p1 - go through all remaining ID-less "FIXME"s and either assign p1/p2 task or change to TODO

===========================================================================
- internals: t210205113857
	- t201223100652 - p4 - setup proper DI (eg for spark/mongodb); macwire maybe?
	- t210114111539 - p2 - @Narrow: identitify wrapped Us (z.map()) vs full on Zs, so can pinpoint problematic object for instance + provide index/_id; runtime errors can be hard to figure out otherwise
	- t210116153713 - p5 - homogenize ClassTag vs WeakTypeTag throughout (always use latter when possible? ie outside of spark)
	- t210129114731 - p5 - provide convenient diffing mechanism (relates to t210129114523), for both schema and data
	- t210127173933 - p2 - @Max3/@Max5 - add missing code (rationale for 3 or 5: if you need more than N, either you can use an intermediate state or you may just be doing something wrong)
	- t210122161652 - p1 - investigate grab/squash (orphan/combine) vs VO
	- heads:
		- t201007093053 - p4 - provide HeadPairO - forKeyPair, for group(_.firstKey).by(_.lastKey)
		- t201021120753 - p4 - provide HeadOptionO, eg as result of u.filter/u.find (see t201023083923)	
	- cleanup: t210202165641
		- t210124092716 - p3 - codegen (very boilerplaty) - using a lot of sed at the moment
		- t210110103720 - p4 - subclass Tq and Ttq rather than using "ev: X <:< Y"
		- t210128161046 - p3 - add/create @Wide annotations (@Narrow being implicit when not @Wide)
		- t210121170823 - p4 - use private whenever possible

===========================================================================
- DAG: t210205113853
	- t210116120349 - p5 - investigate existing graph libs rather
	- t210128152949 - p2 - add missing cycle detection
	- t210106101457 - p4 - meta-only run - may be great for the likes of t210115115736 (generate intermediate [dataclass])
	- t210106101459 - p5 - data-only run, requires standalone data version first (see t210104164037); may also be complicated by atoms that require pre/post schemata (eg _JsonObjectFileInputU, _SortByAll, ...)
	- meta:
		- t201214105653 - p4 - [hack] - address "resultCls" hack
		- t210114113316 - p5 - reenable graphviz dot's output
	- data:
		- t201027130649 - p4 - abstract runner strategy ("naive" strategy at the moment)
	 	- t210114125607 - p5 - improve "InputData" afterthoughts (meant to help with debugging)

===========================================================================
- types: <a name="t210121124808"></a>t210121124808
	- t210115151942 - p1 - @TypeMatching/@PartialTypeMatching - to help find where types are being pattern-matched easily

	- t210110094829 - p1 - opaque nesting: accept Obj as value, albeit the standalone version (see t210104164037); do not limit types to [basictype]; could also help where need to provide newKeys (eg t210202172304)
	- t210110095252 - p5 - BLOB/CLOB (for now must use base64ed version)
		- t210128161507 - p5 - investigate typical unstructured data (videos, pix, ...) manipulations
	- t210115144940 - p5 - finalise "null" representation handling (null vs NaN vs [] vs None vs ...)
		- t210203124717 - NaN: tracking/support + check not in Obj (also see t210203124840, checking value types)
	- t210124153304 - p2 - add all the java.lang primitives, and the .sql ones; automatically convert to scala counterpart though?
	- t210108114447 - p5 - support own "flag" type? or just Option[Unit]?
	
	---------------------------------------------------------------------------
	- numbers: t210205113841
		- t201017102332 - p1 - @NumberAbstraction (formerly @IntDouble): so can locate places where Numbers need to be properly abstracted (especiall integer vs real); also see 210123095857@ReduceReturnType (unchanged/int/double)
		- t201209095425 - p3 - @IntSize: so can locate places with Int is used for size (as opposed to Long in Spark for instance, see t210122094438)
		- t210128162336 - p5 - offer a "dint" accessor, such that data.dint('foo) gives 3 (Int) from 3.0 (Double) - common enough
		- t210109142406 - p5 - n-dimensional arrays (including n=1)
			- t210127141259 - dedicated matrix/tensor object (dense/sparse)
			- t210127141258 - investigate existing libraries; are they all BLAS/LAPACK based? relates to t210121095207 (scala-native)

	---------------------------------------------------------------------------		
	- time: t210205113839
		- t210202160406 - p1 - [research] - keep time types (date/datetime) altogher? are they more a manipulation detail? e.g. {"date": "2021-02-05"}.read().transform(_.string('date)).using(_.parseIsoDate.getYear)); could also provide "overlay" shorthands, eg: e.g. ....transform(_.date('date) /* =.string+parse*/).using(_.getYear))
			- t210202160405 - p1 - [missing] - at the moment none of the serialization format support reading up time types as would be declared in schema
		- t210202160407 - p3 - provide <, <=, >, >= for time-related types as well
		- t210202124121 - p3 - need a way to abstract date/dateTime, eg both can have a day added to

	---------------------------------------------------------------------------
	- enums: t210205113844
			remarks:
			- a boolean can either be seen as 0/1 integers, or as a special kind of enum
			
		- t210201095414 - p2 - missing enum accessor support, eg _.enum[MyEnum]('f)
		- t210114093525 - p4 - capture enum values (will need to adapt serialization)
		- t210110095228 - p5 - also support scala enum (as opposed to enumeratum)
		- t210116114654 - p5 - double check ModifyObj behavior OK
		
	---------------------------------------------------------------------------		
	- Whatever: t210205113848
			remarks:
			- affects: transform, generate, fuse/fission, filter/findBy, pivot, removeIf;
			- keep to a minimum...
		- t210111135617 - p5 - add more common Seq/String/number operations for Whatever?			
		- t210202160537 - p2 - missing combinations of number types for plus/times
		- t210202160709 - p3 - more formatting value types
		- t210204170956 - create workaround for: def + (that: Int): TypedWhatever[Int] (can be Double); relates to t201017102332 (@NumberAbstraction)
		- t210113124437 - need to adapt mechanism to obtain 0 when missing; also "size" ambiguity (container vs length of seq/string)
		- t210204170740 - occurrences of "whatever0": need to determine if/when must use ContainedWhatever or if isWhatever okay
		- t210201164613 - p2 - [bug] - fix .transform(_.typed[Seq[_]]('f)).using(_.size), or provide .anys (if only need eg .size, or .slice(1, 3))

===========================================================================
- stats: t210128151632
	- t210115140107 - p5 - use dedicated lib? or just wrap commons'?
	- t210118083814 - p2 - new version (ReducingStats)
		- t201207170908 - p5 - stats [dataclass] mapping to/from; lite, full;
		- non-number stats:
			t201209145048 - p5 - string/enum/boolean stats: allow only doing top/bottom n
			t210118084833 - p2 - FIXME: dates, strings...
		- number stats:
			- t210204164412 - full vs light versions
			- t210118084355 - p5 - [feature] - add skewness, kurtosis, mode, IQR, more percentiles, median/mean absolute deviation (MAD), trimmed mean/median, geometric mean
			- t210118084356 - p5** - distribution guess scoring? (pretty costly...)
			- integers:
				- t201207134039 - p5 - rounding/floor/ceiling for int values (eg for mean, median, ...)

===========================================================================
- data: t210205113903
	- t210104164037 - p5 - standalone data-only version with most operations (relates to t210104164036)
		- t210104164038 - p5 - standalone json (gson) version for pre/post-processing (relates to input pre-processing: t210202112439)
	- t210107094213 - p5 - ensure if nested multiple elements then use List, not any Seq (especially not Stream)
	- t210125111144 - p3 - consider using an actual NonEmptyList class to represent Pes (such as cats') instead of Option[Seq]? [research]
	- t210114154924 - p5 - read first line (UrlLike.firstLine) - generalize to N lines + make optional + cache
	- t210128135801 - p5 - what would a columnar in memory counterpart look like? look into/integrate with Apache Arrow? [research]
	- t210129114523 - p5 - provide both sorted (via meta) and unsorted equals? [term]: "equality" is tricky, is foo=3+bar=baz the "same" as bar=baz;foo=3? (also see t210129114731)
	- t210110203020 - p3 - [bug] - contains needs to be able to deal with multiplicity in nesting(s) - paths.values.filter(!o.contains(_))
	- streamer: t210115115843
		- t210127193230 - p3 - externalize streamer as its own independent library
		- t210115104555 - p5 - fix Iterator version
			- t210116154537 - p5 - rereading
				- t210115103130 - p5 - resulting missing implementations
		- t210114145059 - p5 - generalize StreamerType enum: inMemory, iterator, RDD
		- t210117112314 - p5 - take/drop/sample/head/last + related (takeRight, ...) issue with @Distributivity
		- t210205121008 - p3 - offer a toIteratorAndCloseable: (Iterator[Obj], Closeable) + aptus.Closeabled; also for Streamer
		- t210204105730 - offer streamer find?
	- t210203124951:
		- t210110095425 - p5 - the Any part: consider a wrapping ADT (cost of wrapping vs pattern matching on Any)
		- t210203124840 - p1 - check value type is part of [basictype] (also see t210203124717)

===========================================================================
- target selection: t210205113906
	- t210107203932 - p5 - cleanup the big mess
	- untyped:
		:
	- typed:
		- t210113162449 - p5 - phase out legacy _explicit
		- t210113114451 - the likes of ifString  should also act as .string(...) since they can't be anything else
	- t210127195422 - p5 - allow an 1.2.1-like array notation?
	- t210127195627 - p5 - tupleN for key/path: eg for group x by y (Tuple2)

	- t210107203932 - p3 - cleanup and fine-tune selections (typed and untyped)
	- t210110094731 - p5 - offer more target "selection" when feasible (eg .convert(_.firstKey).toInt) (otherwise must rely more on forX mechanisms, which is more coarse)
	- t210110094730 - p5 - offer more for-each field operation shorthands (eg .convert('f, 'g, 'h).toInt) when practical; (otherwise must rely more on forX mechanisms, which is more coarse)

===========================================================================
- validation: [vldt] t210205113909
	- t201210104557 - p2 - all missing actions validations (lots)
	
	---------------------------------------------------------------------------
	- input: t210115153348
		- meta:
			- url-like:
				- t210115193904 - p3 - check URI, regular file vs symlink, ...						
			- RDBMS:
				- t210115205723 - p5 - validate URI earlier
				- t210114202848 - p5 - validate query earlier
			- mongo: 
				- t210114152901 - p5 - actually validate mongo query				

		- data: 
			- t210115153347 - p1* - missing input validation when schema is provided, as action; eg: RuntimeValidation.validate(c)(obj('f -> Seq(1, 2, 3), 'g -> new java.io.File("") ) ) -> Some(List(ValErr(19,'g,None,unrecognized type))) (see 210115153346@RuntimeValidation); 				

	---------------------------------------------------------------------------
	- output: t210205113916
		- t210204163720 - p3 - check writable
		
	---------------------------------------------------------------------------			
	- types: t210205113919
		- t210201103739 - p2 - validate T for .typed
		- t210201164749 - p2 - if ignoring container (eg .stringx('f)), validate not changing container type		
		- t210201164749 - p1 - transform Whatever to Whatever -> ensure not changing type (and container?)
		- transform x to v:
			- t210202155202 - p1 - verify result type (e.g if returns Char instead of String accidentally)
		- transform u to x: 
			- t210202155458 - p1 - verify input is indeed u
		- transform z to x:
			- t210202155459 - p1 - verify input is indeed z
			
	---------------------------------------------------------------------------			
	- errors: t210205113922
		- t210121101206 - p2 - homogenize the errors mechanism
			- t210121101207 - meta level
			- t210121101208 - data level
			- t210121101209 - other
		- warnings: t201204115411 - p4 - as separate mechanism, to be called indepently
	
	---------------------------------------------------------------------------	
	- key validation: t210127133546
		- t210128155944 - p2 - validate new key names for add/replace/underNewKey/pivot/untuplify2/...			
		- t210127133623 - p3 - special treatement for reserved keys such as '_group, '_left, ...
		- <a name="t210127134525"></a>t210127134525 - macro version if statically provided key (eg .remove('foo) vs .remove(myKeyArg) )
		
	---------------------------------------------------------------------------
	- actions: t210205113925		
		- unarray:
			- t210115175242 - p5 - unarray entries: add missing runtime validation of newKeys
		- zip strings:
			- check fields (container, exists)
			- check at least two

	---------------------------------------------------------------------------
	- misc:
		- t210128162901 - p5 - macros to check that eg data.add('p -> new java.io.File("/tmp/foo")) indeed uses a valid value type (basic type, [dataclass], opaque object, ... but not say java.io.File)
		- t210128153122 - p2 - prevent cycles in nested [dataclass] validations + set a max nesting

===========================================================================
- actions: t210204152754
		remarks:
		rk210204162927 - [fluency] conveying intent matters, e.g. add (must not already exist) vs replace (must already exist)
		
	- cross-cutting:		
		- t210110104437 - p1 - [hack][bug] - all the renFX/fromFX/fromsFX/explicitFX, eg: nest, unnest, ... -> where renaming is supposed to be possible
		- common:
			- t210126171839 - p3 - implement a "_then" for good measure and testing; eg data._then(_.rename('foo ~> 'FOO))
			- t210117110015 - p5 - move the likes of retainFirst and renameSoleKey to common, rather than duplicating them in each (may be tricky)
			- t210111095156 - p5 - [whatever] - separate all the Whatever (similar to cc); leverage 210122154401 (Quintuplet)
			- t210111095157 - p5 - [dataclass] - case-class versions: separate all the cc versions (similar to whatever)

	===========================================================================
	- v:
		- t210202154249 - p3 - operations like forceDistinct for Vs too?
		
	===========================================================================
	- z -> u:
		- t210131104517 - missing feature? an "unarrayUsing"? relates to pivoting (possibly to t210128161346); see more at 210131104800@w, see xml POC
			- t210131104518 - bobjs(bobj('f -> "f1", 'g -> "a"), bobj('f -> "f2", 'g -> "b")) -> ? -> bobj('f1 -> bobj('g -> "a"), 'f2 -> bobj('g -> "b"))
			- t210131104519 - bobjs(bobj('f -> "f1", 'g -> "a"), bobj('f -> "f2", 'g -> "b")) -> ? -> bobj('f1 ->            "a",  'f2 ->            "b") 				

	===========================================================================	
	- u: HeadO: t210205113934
		- t201023083923 - p5 - add find/filter to HeadO as well, to make it an "option" (relates to t201021120753)	

		---------------------------------------------------------------------------
		- basics:
		
			- inspect:
				- t210115180822 - p5 - homogenize "inspect" vs "show" schema; also [term]
				- t210115175106 - p5 - versions that allows more configuration
					- t210115180737 - schema: configurable
					- t210115180738 - data
			
			- add:
				- t210111113206 - p4 - support adding path, eg: .add('p |> 'f -> "foo") - denormalize if multiples along the way
				- t210127194716 - p2 - also support append/prepend field(s); maybe genelized as insertion index (including negative)?
				- t210128155501 - p5 - add a lazy version: => value; also for replace:x
			
			- retain:
				- t210128162442 - p5 - just implemented as remove all but? or has value as standalone? [research]
				- t201215121718 - p5 - [optim] - need more than one level for efficiency of retain multiple+path: case class RetainMapping(data: Map[Key, Option[KPathz]])
				- t210127193137 - p1 - retain to also reorder? or as separate action?

			- convert:
				- t210128152726 - p4 - [feature] - add missing convert('foo).toEnum[MyEnum]
				- t210128162159 - p4 - [feature] - convert from JSON string, eg .convert('foo).fromJsonString[MyDataClass]("""{"foo":1, "bar":"baz"}""") + convert('foo).fromJsonToObj (see t210110094829 opaqueness)

			- set default value:
				- t210129093607 - p4 - [feature] - offer shortcut setDefaults('foo -> 1, 'bar -> "baz", ...)
				
			- translate:
				- t210117125042 - p3 - rework translateAll, confusing as it is


		- transform-like:
			- fission/fuse:
				- t210115175745 - p2 - [hack][bug] - fission/fuse removals

			- generate:
				- t210202164324 - p2 - missing GenerateZV/UZ/V
			
			- shorthands:
				- t210205121240 - p3 - more convenience like: prepend, surround, addDay, ... (see aptus')
				- t210127164512 - missing shorthands: isPresent/isMissing/unquoteKeys
				- t210205122644 - more missing shorthands: addTo/transform{Group/Left/Right}/reformatTime    				
			
		- asserts:
			- t210129094319 - add assertIsDistinct

		
		- zip strings:
			- t210109142621 - p2 - [feature] - add unzipStrings operation (optionally with separator); zip/unzip can act as a form of tranpose; also see t210111113343 for unzip
			- t210111113343 - p5 - [feature] - add support for zip (non-strings) for consistency: bobj('f -> Seq("a", "b", "c"), 'g -> Seq("1", "2", "3").zip('f, 'g).underNewKey('p)
			- t210110101000 - p2 - [feature] - offer a [guaranteed] zip (if expect no missing fields)			
			
		- untuplify:
			- new keys:
				- t210117192142 - p5 - [feature] - add enum counterpart to provide newKeys, eg def asNewKeys[MyEnum] (also see t210117192141 for pivoting)
			
		- nesting-related:
			- t210109144926 - p5 - [feature] - generalize nest/unnest as "move"
			- t210109173114 - p5 - [feature] - renest just up to n levels?
			- t210109175621 - p5 - [feature] - reproduce the optional "as" mechanism: for renest (see t210116192032 for generalization)
			- t210122162650 - p2 - [bug] - meta nest into: handle optional the way nest-under does
			- renest: if all can be opt (see ?); relatest to [guaranteed]?

	===========================================================================
	- z: HeadS: t210205113938
	
		- misc:						
			- t210202114834 - p2 - [feature] - offer lookup outputs: eg .forceLookup(key = _.string(_id), value = _.int('myInt))): Map[String, Int]
			- t210116192032 - p3 - [internals] - generalize HasAs/chainzzWithAs mechanism (eg to help with t210109175621)?
			- t210127164715 - [bug?] - isEmpty/nonEmpty/if not top-level? (check missing will return size = 0)
			- t210205122151 - [feature] - offer toRddBased/toInMemoryBased
			- t210131110455 - p3 - [feature] - tabularize/untabularize
				- <a name="t210131110456"></a>t210131110456: tabularize (also see cartesianProduct); or "rectangularize"? [term]; mass flattening; default the likes of Seq(1, 2, 3) to "1|2|3" (configurable sep)
				- t210131110457: untabularize (also see reverseCartesianProduct) - reuse table parsing mechanis + mass renesting for common prefixes

		- set default:
			- t201005102404 - p3 - for multiple only: offer backfill/forward fill

		- distinct:
			- t210117113705 - p2 - add distinctByAdjacency: convenient if mostly grouped already; for distributivity, do at least per partition		

		- sorting:
			- t210127193358 - p4 - [fluency] - offer eg sort('f.reversed, 'g.reversed)
			- t210202164133 - p2 - [fluency] - forbid "missingLast" if not optional field

		- aggregating: t210127195238			
				- t210202163542 - p2 - address if no aggregation (in meta)
				- t210127195214 - p2 - [fluency] - forbid agg(_.foos('f)) -> notice the 's'; already the case in fluent interface?				
				- t210202163714 - p2 - [hack] data: address temporary hack (.get)
				- t210131141737 - p3 - [bug?] - .countEach('f, 'h).by('g); countCombos (see 210131141737@w)

			- grouping: t210127195236
				- DWH/MDX: t210124100722; add the likes of cascade, cube, rollups, grouping sets, ... e.g. .groupCascade('state %> 'cities, 'city %> 'zips) - see 201227150057

			- counting:					
				- t210131140932 - countBy needs to accept _.allKeys; then create shorthand countByAll = countBy(_.allKeys)

		- filter z:
			- t201021120752 - p4 - [hack] - address HasAsFind hack - (relates to t201021120753@proper HeadOptionU)
			- t201021120751 - p2 - [feature] - provide Wathever-based SQL-like shorthand for IN: .filter('color).in("blue", "white", "red")
	
		- flatten by:				
			- t210131101358 - p3 - simplify X in: [{"values":"g1;g2;g3", "bar": true}, {"values":"g4", "bar": false}] -> X -> [{"values":"g1", "bar": true}, {"values":"g2", "bar": true}, {"values":"g3", "bar": true}]; X=.transformString('values ~> 'value).using { _.splitBy(";").as.noneIf(_.size == 1) }.flattenBy('value).filterBy('value).isMissing	    	
			- t210131102306 - cascade if multiple?
			- t210131102354 - flattenAndUnnestBy{Group,Left,...} - common enough?

		- merging:
			- t210128130124 - p2 - [fluency] - allow explicit use of in-memory join if one side is small enough ("hash" join) 
			- t210117143536 - p5 - also handle union within merging conf?
			- t210124100649 - p4 - [feature] - add multi-joins
			- [guaranteed]:
				- t201124153838 - p3 - a bring "[guaranteed]" (no missing); or by default [research:x]?
				- t201124153839 - p3 - a join [guaranteed]? when not inner?				

		- reducing:
			- t210122151934 - p2 - ActionsUUReducer0: use newer reducer rather, instead of old ToArray/ToSize/ToSum
							
		- pivoting:
			- new keys:
				- t210117192142 - p4 - enum counterpart to provide newKeys, eg def asNewKeys[MyEnum] (also see t210117192142 for untuplify)
				- t210202172304 - p3 - unspecified: using opaque object as data (relates to t210110094829) - try
			- <a name="t210120171258"></a>t210120171258 - p2 - [feature] - add support for unpivoting
			- t210117192221 - p3 - configurable key separator	

===========================================================================
- schema: t210204152731
		remarks:
		rk210127114008 - a schema is really just data about data (hence "meta"-data);
		rk210127114009 - specifically a schema can be seen as coarse statistics about the data

	- io: see t210128103821
	
	- t210124100957 - p5 - a "confirm" schema action, e.g. [...].confirmSchema[MyDataClass] or .confirmSchema('foo.string, 'bar.int) or .confirmSchema("my/file")		
	- t210126173150 - p5** - ambitious "[backtracking]" mode [research], whereby no input schema is provided and instead each step ensure consistency with one another only (e.g. don't add a field that was already added in an earlier step); relates to t210118133408 [hettype]
	- t210128165110 - p5** - going to/from schema formats (relate to io's t210128103821 - generalize schema i/o for any schema-like format)
		JSON schema (see t210128163913), avro (see t210128163914), ES mappings (see t201028094710), ...

===========================================================================
- io: t210204152732

	- misc:
		- <a name="t210121160956"></a>t210121160956 - p3 - [feature] - checkpointing mechanism (relates to t201108093951 for z.writeJsons)
		- t210121171126 - p5 - provide Windows support? try a run (I suspect the likes of '\r' will trip it in local mode at least); support .ini files and so on; are there named pipes equivalent? GNU-sort?

		- schemas: t210128103821 - p5 - generalize schema i/o for any format schema-like that can be (reasonnably) parsed, may be useful to limit code duplication (also relates to t210128165110 - going to/from schema formats)								

		- pre/post processing: [preproc]/[postproc]: t210202113208				
			- [hettype] handling: see t210118133408@research
			- (for url-like only) allow pre-processing: t210202112203
				- pre-processing lines: t210202112245 - p3 - to e.g. skip lines, combine lines, ...
				- pre-processing line: t210202112246
					- json:
						- t210202112439 - p1 - allow gson pre-processing, eg .jsonNull('foo).as("null"), .emptyJsonArray('foo).as("empty"); see t210118133408@research for type heterogeneity [hettype]
				- (for tables only): pre-processing cells: t210202112247 - p3 - 

			- (for url-like only) allow post-processing: t210202112204
				- post-processing lines: t210202112255
				- post-processing line: t210202112256					
					- json:
						- t210202112440 - p2 - allow gson post-processing eg .toJsonNullIfMissing('foo), .toJsonArrayIfMissing('foo); see t210118133408@research for type heterogeneity [hettype] and t210104164038 for standalone json
				- (for tables only): post-processing cells: t210202112257 - p3 -

	===========================================================================
	- format support: t210204135415
	
		- file-based:
			- t210128163910 - GPPL classes source code (POJO/POCO/POKO/js/python/rust/...); also see t210117105638 for in-memory
				- t210115115736 - p2 - allow writing schema as scala [dataclass] hierarchy at any given step (using field name for nested class names by default, if ambiguous)
					may be convenient especially if run in meta-only mode (t210106101457), to provide both incoming/outgoing cc for a complicated transformation							
			- t201103114910 - config files: java properties file (eg config.properties: foo=bar\nbaz=3\n...), *nix config files (cat foo.conf -> #comment\nkey=value\n ...); will need charset support too
			- t210128160407 - p3 - handle XML (see PoC code)
			- t210128163914 - avro/thrift/protobuf
			- t210128163915 - parquet/ORC/RCFile/CarbonData (also look into feather?)
			- t210128160323 - p3 - excel (via apache POI), eg "/path/to/file.xlsx", use sole sheet or provide sheet name as "container"; see POC code
			- t201028110431 - pdf...? try and at least extract tables? probably tricky... https://stackoverflow.com/questions/3424588/programmatically-extract-pdf-tables
			
			- more:
				- t210204142554 - HDF/HDF5
				- t210204142555 - SequenceFile								

		---------------------------------------------------------------------------	  							
		- databases: t210205113943
		
			- 210204135028 - RDBMS:
				- schema: t210204135246
					- t210128163911 - in: JDBC (meta)
					- t210128164004 - out: DDL
				- data: t210204135245 - JDBC																							

			- t210128164010 - mongodb:														
				- t201223092203 - schema look into https://docs.mongodb.com/realm/mongodb/document-schemas
				- t210128164011 - data
					- t210110112325 - p5 - cleaner version of command parsing
					- t210114153517 - p5 - remove jongo reliance

			- t210128164016 - elasticsearch (ES):
				- schema: t201028094710 - offer schema via mappings							
				- data: t210204140033

			- more:
				- t210204140102 - neo4j (cypher); schemes: neo4j+s, bolt+routing?
				- t210204142939 - dynamoDB - see https://aws.amazon.com/getting-started/hands-on/create-manage-nonrelational-database-dynamodb/3/; table = dynamodb.Table('Books'); resp = table.get_item(Key={"Author": "John Grisham", "Title": "The Rainmaker"}) - no plain text QL?
			  	- t210204142940 - cassandra (CQL, via JDBC?)
				- t210204140103 - redis

		---------------------------------------------------------------------------								
		- in memory: t210205113946
			- t210128163912 - Spark Row
			- t210117105638 - [dataclass] - (see code 210117105638@w); also see t210128163910 for source code
				- in:
					(x:     MyCc ).read  ()
					(x: Seq[MyCc]).stream()
				- out: readCC/populateDC/writeCC + z
					val x: MyCC           = u.populate[MyCc]
					val x: Iterator[MyCC] = z.populate[MyCc] // or as Streamer

		---------------------------------------------------------------------------
		- schema-only: see t210204142528

		---------------------------------------------------------------------------
		- web: t210205113949
			- t210128163917 - GraphQL
			- t210128163918 - semantic web: OWL (schema/read/write) + SPARQL (read)
			- t210204142941 - REST architecture:
				- schema: varies... see swagger, raml, blueprint, JSON-LD, ...
				- data: at least provide very basics of GET, POST, PUT, ...
			- t210128165639 - p5 - what would support for WSDL/SOAP look like? (for legacy)						

		---------------------------------------------------------------------------
		- data-only: t210205113951
			- json:
				- t210204095517 - p5 - long term: replace gson with scala based json library			
			- t201028110434 - yaml				
			- t201028110435 - typesafe config (HOCON)
			- t201028110436 - MessagePack?  			
		
		---------------------------------------------------------------------------
		- schema-only: t210204142528
			- t210128163913 - JSON schema							
			- t210128163916 - swagger docs (see https://editor.swagger.io/)							
			- t210204135521 - serialization for gallia's own representation (coin [term])		
					x t210204135633 - pretty JSON (current default)
					- t210128164127 - compact-JSON/YAML/HOCON
					- t210204135644 - our BTON format (see 201230133034 for POC code)
					...			

		---------------------------------------------------------------------------
		- file systems: t210204143321			
			- <a name="t210120153618"></a>t210120153618 - p2 - hdfs
			- mongo: mongodb+srv?
			- more distributed FS: gluster (gluster://), IPFS (ipfs://), Alluxio/Tachyon (alluxio://), Swarm (decentralized)? ...
		  - object storage: t210204143322
				- t210120153619<a name="t210120153619"></a> - p2 - s3 support
				- more: google cloud storage, azure, openstack swift? IBM's?

		---------------------------------------------------------------------------
		- compression: t210118103219 - on top of gz/bz2
			- t210120153620	- lzo support
			- more: snappy, lz4, ZSTD

	===========================================================================
	- in: t210205114007
		- validation: vldt: see t210115153348

		- misc: t210205114028
			- t210114201159 - p5 - implement missing convenience creation methods (eg "hello world".content, ...)
			- t210114144622 - p5 - also allow iterator mode for both JDBC and mongodb
			
		- inferring: t210205114025
			- t210122135629 - p5 - [missing] - implement mirror index in IndexEntry
			- t210204151934 - p1 - [bug] - if file/url is empty
			- t210204120123 - p3 - [uexp] - improve error handling, especially around heterogeneous types [hettype] (e.g .int vs string)

		- url-like: t210205114024
			- t210122135525 - p1 - ignore trailing empty line by default if present at the end - very common (relates to t210202112245: pre-processing lines)
			- t210128160505 - p3 - make drop any empty line/row (post-trimming) be the default behavior?
			- t210202165017 - p3 - allow skipping first/last n lines explicitly (pretty common for table)

			- json: t210205114021
				- t210116150154 - p3 - [bug] - must remove nulls PRIOR to size
				- t201103154749 - p5 - gson: look into cost of reflection setAccessible(true)			
				- t201221175254 - p5 - array: stream rather than read all in memory

			- table: t210205114019
				- t201103174026 - p3 - [bug] - handle rarer case where columns names are repeated? use _1, or fail if values differ for two columns with the same name?
				- t201028110146 - a tsv/csv convention that allows providing basic types succinctly, eg in header 'age:integer' (instead of just 'age'), favorite_colors:strings(","), middle_name:string?(""), ...; [research]
				- t210116110159 - p5 - support header at more than n=0? or only as preproc? (relates to t210122135525)
				- inferring:
					- t210122135629 - p5 - implement mirror index in IndexEntry
					- t210204151934 - p1 - [bug] - if table is empty
				- fluency:
					- t210122162835 - p4 - if NoInferring, disallow .nullString and so on

		- RDBMS: t210205114014
			- t210115205609 - p5 - actual URI decoding
			- t201223092238 - p4 - [optim] - use JDBC meta  for schema instead of inferring (current)
			- t210114145431 - p3 - injection attack protection (use lib?)
			- t210128160241 - p2 - try with FileMaker (often used by labs along with excel) - jdbc:filemaker://localhost:2399/mydb

	===========================================================================
	- out: t210205114012
		- misc:
			- t210122140324 - p1! - [bug] - ensure sole or last leaf before running
				- closely related to t210121160956-checkpointing (and t201108093951-returning Unit or head)
				- delaying run causes issues for formatString that uses a StringWriter
				- 210205063004: would make the potentially problematic assumption that a fork isn't requested *after* one of the leaf has been acted upon
			- t210202165243 - p4 - [feature] - allow append as well		
			- t210204193417 - p3 - [feature] - for practicality, provide informal describe()/describeMeta()/describeData() (if no nesting then as formatted table, and so on)
		- json:
			- t201230133034 - p5 - redo the "more readable" json version (see 210204164133@w), and/or do a BTON equivalent

		- schema: t210205114016
			- t210115114631 - [feature] - possibly none (only writing data)
			- t210128164202 - [feature] - possibly more than one
			- t210115114509 - p5 - [feature] - configurable schema filename suffix (vs ".schema" in ".schema.json") to override default
			- t210128164040 - corresponding write [fluency] - eg schema(_.exclude), schema(_.json), schema(_.fileName("foo")), .schema(_.compression)

===========================================================================
- performance: [optim]: <a name="t210121095401"></a>t210121095401
	- t210121170923 - p5 - need some benchmarking numbers before optimizing, maybe use TCP-DS? (check license)
	- t210104164036 - p5 - UData as Vector[Seq[Any]] (relates to t210104164037)
	- t210110100144 - p5 - macros for [dataclass] to/from Obj + field names enum
	- t210115095741 - p2 - von neumann bottleneck: also give easy access to .par where applicable; for iterator: see t210115095742
	- t210115095838 - p5 - more reliance on meta to help with data, so as to minimize pattern matchings at runtime (eg see t201019110649 for reorderKeysRecursively, obj to gson, formatting value in table (array or not))
	- t210121095207 - p5 - look into scala-native (also see t210109142406 for matrices)
	- t210121170909 - p5 - add @inline, @switch, @tailrec, @specialized whenever relevant
	- opt-out:
		- t210107094406 - p5 - possibility to opt out of the checks like non empty object (for performance); worth it?
		- t210114143028 - p5 - opt out of util.Try for runtime; worth it?
	- specializations:
		- t210114170853 - p5 - grouping: separate at least 11/1N/N1/NN atoms?
		- t201019161520 - p5 - aggregation: specialized version of sumby/countby/... rather than combos
		- more optional vs [guaranteed] atoms version (formerly "A/B" versions): _FilterBy1, _AssertO1, ...		
	- t210106120036 - p5 - pointless as it is, point will be to project/retain *before* creating obj (data projection)		
	- t210121165741 - p5 - does -Xdisable-assertions also turns of require? if not, is it possible? [build]
	- plan: t210204112440
		- t210126171438 - atom plan optimization (also relates to t201027130649/abstract runner)
			- predicate push downs,
			- early pruning, ...
		- optimize traversal if dag is chain, especially if nested
		- plan caching?
	- spark: t210204112444
		- t210121164920 - p5 - delegate to spark SQL when feasible? might be tricky unless trivial; is Tungsten only used with spark SQL?
		- t210126171605 - provide Obj Encoder
		- t210204112431 - create an Array backed (at least initially) Objs due to prominence in spark?
		- t201126163157 - p5 - [optim] - ensure distinct: to avoid looping more than necessary, consider sort followed by rdd.mapPartitions(_.sliding(size, step), preservesPartitioning)?
		- t201126111306 - p5 - confirm no better way; no {left,right,inner}CoGroup available it seems; note: using the {left,right,inner}OuterJoin here would force us to redo an unncessary re-grouping         
		- t210122095106 - p5 - confirm no performance impact: .filter(_._2._1.nonEmpty).filter(_._2._2.nonEmpty) vs combined

===========================================================================
- spark: t210121164812
		remarks:
		- not a spark expert so probably a lot more can be done to better take advantage of it

	- indirection:
		- spilling: see t201131143901
		- optim: see t210204112444
	- fluency:			
		- t210122094521 - p5 - provide convenient access to setting numPartitions
		- t210121164813 - p5 - provide convenient to mapPartition [performance]
		- t210121164814 - p5 - provide convenient to partition combiner [performance]
	- i/o:
		- t210121164950 - p3 - [missing] - actually handle charset
		- t210121164951 - p3 - [missing] - actually handle compression
	- logging:
		- t210122092713 - p5 - proper logging mgmt
		- t210122092619 - p5 - hide "Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties" message
	- distributivity:		
		- t210123183101 - p4 - @Distributivity - all the spots where distributity might be an issue (eg .head does not make sense unless sorted first)
			- t210122094456 - p5 - take/drop/sample
	- misc:
		- t210121164949 - p5 - handle Serialization issues (likely will happen when)		
		- t210123183102 - p4 - @Scalability - places where scalability might be an issue, especially if processing all in-memory at the moment: eg cartesian product (and reverse), reductions, unarray, string formatting
		- t210122101756 - p2 - [hack] - address giant hack (setting StartReadFluencyRDD.streamLinesViaRDD(sc))
		- t210122101757 - p3 - [missing] - cache SparkContext
		- t210122102109 - p5 - flatMap: address casting .asInstanceOf[SparkColl[B]]
		- t210122094438 - p2 - change to Long for size by default? maybe offer sizeLong: Long and sizeInt: Int; relates to t201209095425 (@IntSize)
		- t201216101136 - p5 - [research] - try a org.apache.spark.sql.Dataset[Obj] counterpart; why is Dataset under sql?
		- t210204095516 - p4 - try spark 3.x
		- t201106123320 - catch error earlier (for _.rdd(...))
		- t210204110958 - actually try a reduce
		- t210204110959 - actually try a fork
		- t210204110908 - limit still around 2GB?		
		- t201101115807 - investigate "The iterator will consume as much memory as the largest partition in this RDD"
		- t201101121424 - confusing: `preservesPartitioning` indicates whether the input function preserves the partitioner, which should be `false` unless this is a pair RDD and the input function doesn't modify the keys.

===========================================================================
- build: t210121165130
		remarks:
		- semver: will be very liberal with my changes to PATCH version at least for the 0.0.x series, will then formalize process by increment
			
	- <a name="t210121101237"></a>t210121101237 - p3 - add support for 2.13
	- t210121165146 - p5 - add support cross-building (2.12 onward)
	- t210121101238 - p3 - prototype for scala 3.x					
	- t210121165120 - p5 - shade guava [spark]
	- t210121165147 - p5 - add support for test coverage
	- t210121165219 - p5 - address warnings / add more scalac options
	- t210121165228 - p5 - try intellij IDEA to find unused classes (relates to t210127133131)? or try with sculpt?
	- t210121165229 - p5 - automatic code formatting (allow override) (relates to t210124151701 - code style:x); may be too tricky to match current style enough though
	- executable:
		- t210204101108 - p2 - publish jars on maven central
		- t210121165247 - p5 - try bytecode optimiser(s)
		- t210115152435 - p1 - error origins when using jars shows "jrt:/java.base/jdk/internal/reflect/NativeMethodAccessorImpl.class(NativeMethodAccessorImpl.java:...)" instead of source -> change to "source unavailable" message							
	- t210204101632 - p3 - create a monorepo
	- t201022170436 - p5 - actually enfoce the likes of @aptus.fordevonly
	- t210121171033 - p5 - make sure instance of null are all legit (mark the legit ones so build can ignore)
	- t210125110147 - p3 - investigate sbt alternatives

===========================================================================
- testing: test: t210205114038
	- t210114171154 - p5** - port "quick tests" to actual tests

===========================================================================
- scala: t210121165423
	- t201213095810 - p5 - any way to what's in Unit_ to Predef if possible? implicit class doesn't seem to work
	- t210115142355 - p5 - investigate why += not appending for immutable.ListMap (see code)
	- t201123125604 - p5 - why implicit not picked up (HeadZPair)
	- t210116154010 - p5 - ideally would need to curry type args... or alternative?
	- t210116165405 - p5 - which is faster, ADT vs boolean pair pattern match?
	- t210117104246 - p5 - cannot use .tupled here?
	- t210117192437 - p5 - is it possible to do the negation of <:<?
	- t210118134814 - p5 - confirm runtime cost worth bothering?
	- t210124092916 - p2 - is there any way to summon a Numeric instance at runtime from Any? [numbers]
	- t201005145138	- p4 - is toString on a number always going to be compatible with most languages, eg R/python and so on (3e06 vs 3E06 and the likes for instance?)
	- t210125111338 - investigate union types (coming in scala 3?)

===========================================================================
- aptus: t210121165939
		remarks:
		- meant to be really to-the-point, easy to call utility methods
		- if anything more powerful is needed then must drop to full-on java/scala/guava/commons way
		- it can also be seen as a starting point, for someone to see what is used under the hood and expand from it if needed; eg: val content: String = "/my/file.txt".readFileContent()
	- t210116165619 - p5* - port the rest of aptus (much larger)
	- t210116165620 - p5 - externalize aptus in its own stand alone utility library
	- t210116165559 - p5 - rename ".as" to ".in"? [research]
	- t210123101634 - p2 - [bug] - significantFigures vs maxDecimal
	- t210204095900 - p4 - regexes could use a much more thorough treatment
	- t210125110827 - aliases: consider AnyVal-based wrappers rather than mere aliases? overkill?

===========================================================================
- docs: t210127114652
	- t210127125443 - bullet points version first
	- t210127125444 - create minimal scala learning resource (to help at least understand _client_ code)?
	- t210127163237 - describe assumptions (may in Obj.scala, eg a201104150252) and workarounds
		- null semantics: especially for overloaded null values (e.g. a middle name can legitimately be not applicable OR unknown)
		- 2+D arrays: generally forbidden as semantics are typically too unclear (outside of matrices/tensors)
	- style: t210124151646
		- scala:
			- t210124151701 - create basic scala coding style guide (look at existing code in the meantime) - relates to t210121165229 (automatic code formatting)
				- 210127125354 - vertical alignment: whatever can be done to lower cognitive burden
				- ...
			- t210127125056 - describe/provide IDE templates, such as '---'/"===" banners, "formatDefault", "enum", "caseopt", ...

	- terminology: <a name="t210124100007"></a>t210124100007
			remarks:
			- sometimes making up a temporary term is better than leaving ambiguity and polysemy
			- keep symbolism to a minimum, when really more convenient
		- <a name="t210127123739"></a>t210127123739 - describe symbolism (+ rationale), e.g. "|>", "~>", stringx (ignore container), string_ (because `string?` is ugly), .typed[String]('foo), ...
		- t210127123841 - describe abbrevations and acronyms, e.g. KVE (Key-Value Entry), NDT (NodeDataType), ASG (Afferent Sub Graph), ...
		- t210130091656 - describe common (hosting language) reserved keyword workarounds: dis (this), thn/zen (then), wit (with)
		- t210130091657 - describe gallia reserved keyword: _id, _group, _count, _tmp, ...; basically use them for unintended purposes at your own risk
		- t210127123840 - disambiguations (for consistency within project at least); to tackle synonyms and polysemes in particular
			e.g. "distinct" vs "unique", "head" vs "first"
			DSL may slightly differ, especially around reserved keywords for the hosting language
		- renamings: t210202165617
			- t210121105809 - p2 - rename HeadU/HeadZ to HeadO/HeadS			
			- t210205065320 - p2 - rename to .grab to .access or .orphan? .squash to .combine?

===========================================================================
- research:	t210205114050
	- t210202085958 - p2 - create a special action for simplest transform 1 to 1 that ignores requiredness; like "morph" for "transmute" (arbitrarily)	
	- t210128160642 - p4 - expect import gallia.local._ to unlock e.g. take/drop; pertains to @Distributivity (t210123183101); contrats with import gallia.spark._
	- t201108093951 - p3 - should z.writeJsons return unit or a z (may need to reread input) - has a big impact on [spark] (see checkpointing: t210121160956)
	- t210127193847 - p1 - make multiple keys selection (sequentially, for each) rely almost exclusively on forX mechanisms (except for most basic operations)? eg:
			aobj(cls('f.string_, 'g.string_, 'h.boolean))(obj('h -> true))                         .setDefaultFor('f, 'g).asValue("-") .test(bobj('f -> "-", 'g -> "-", 'h -> true))
			aobj(cls('f.string_, 'g.string_, 'h.boolean))(obj('h -> true)).forEachKey('f, 'g).zen(_.setDefaultFor(_)     .asValue("-")).test(bobj('f -> "-", 'g -> "-", 'h -> true))
		possibly even container type, eg: data.forKey(_.string_('f)).zen(_.transform(_).using(...)) - may be too coarse though
	- t210202094041 - p1 - semantic conflict for "commas": sometimes means EACH, sometimes means AND; maybe change one of them to always be myAction('f ~ 'g ~ 'h) instead of myAction('f, 'g, 'h)
	- t210128161346 - p1 - pivot: dissociate top-level groupBy ("rows") from the rest of the pivoting (also see former "pivone" feature)
	- t210202164007 - p3 - grouping: allow groupby with redundant keys in grouper/groupee?
	
	- dialects:
		- t210202113713 - p3 - consider providing "wrappers" for very at least basic queries people are familiar with such as: gallia.dialects.sql.select('foo, 'bar).from("jdbc://.../table1").where('baz == 3); mostly to help "port" code initially
		- t210128152716 - p3 - add "dialects" like R: gallia.dialects.R.unlist so people can see what it resolves to (+ to help migrations)
		
	- t210118133408 - p2 - [hettype] - type heterogeneity handling
		- t210202115959 - full-on support type heterogeneity [hettype]? big endeavor but may be worth the effort
		- t210202115958 - p2 - type heterogeneity [hettype] workaround (relatest to t210104164038 for json manip) - especially cases like:
					[{"foo": 1}            , {"foo": "10+"}]            -->  [{"foo":"1"},            {"foo": "10+"}]
					[{"foo": {"bar": "hi"}}, {"foo": "sup"}]            -->  [{"foo": {"bar": "hi"}}, {"foo": {"bar": "sup"}}}]
					[{"foo": "bar"}        , {"foo": ["bar1", "bar2"]}] -->  [{"foo":["bar"]},        {"foo": ["bar1", "bar2"]}
				or maybe just ability to rename fields like: 
					[{"foo": 1}, {"foo": "10+"}] --> [{"foo_int":1, "foo_string": null}, {"foo_int": null, "foo_string": "10+"}]

	- terminology: t210124100008
		- t210124100008 - p2 - change read()/stream() to readOne()/read()?
		- <a name="t210127124029"></a>t210127124029 - p4 - create OWL ontology?
		- t210124100009 - better names for: {A,B}Obj, CanForceAs{1,2}, potch, untuplify{1,2}{z,a,b}, asArray{1,2}, Whatever, "pairs", NonTable, Ttq{K,R}Path{z,}, reverseCartesianProduct
		- t210202100936 - p3 - field creators .date and .dateTime conflict with aptus' ... as date1/dateTime1?			
		- t210202101142 - p2 - keep "accessor" term (eg HeadZAccessors)?
		- target selection:
  			- t210201151634 - p2 - (target) replace "Query" with "Selection" throughout? 
  			- t210202090211 - p2 - homogenize across "target" and "selection" packages			
  			- t210202090526 - p2 - rename and homogenize the likes of "Duo", "HT", "HasType"

===========================================================================
- more: t210124100537
	
	- spilling: <a name="t210204111309"></a>t210204111309 - see PoC
		- t201131143901	- spark: make sure that we preserve order if data is small
	
	---------------------------------------------------------------------------
	- integration: t210124100540 - investigate dependencies first and foremost
		- indirection:
			- graph: see t210116120349 (for plan DAG)
			- RDBMS: see t210114145431
			- json: see t210204095517
			- spark: see t210204095516 for Spark 3.x			
		- t210204095519 - stats/linear algebra/scientific computing, math in general
			- look into these: breeze, saddle, spire
		- t210204095520 - low priority - visualization: look into vegas?

	---------------------------------------------------------------------------
	- scripting: t210124100126
		- make it easy to use gallia from script (eg bash); for improved performance, could look into nailgun or custom socket-based alternative?

	---------------------------------------------------------------------------
	- scientific computing: computational science:
			remarks:
			rk210127135755 - while not the primary goal, would be great to provide more					

		---------------------------------------------------------------------------
		- external tools: <a name="t210124092211"></a>t210124092211
				remarks:
				- pertains to the ability to wrap/call external tools (with performance hit), especially R/python/js/...; see POCs; for python, look at jep
				- great to showcase what features are useful and could benefit from being replicated in gallia
			- visualization: plotting: t210124092257
			- scientific computing: t210124092258

	---------------------------------------------------------------------------
	- notebooks: t210124092512
		- investigate integration with jupyter/google colab/...

	---------------------------------------------------------------------------
	- semantics: t210124100546
		- <a name="t210124095616"></a>t210124095616: may be tricky with transformations, eg if you fuse first and last name into name, how are the two "merged" as full name somehow? (eg with https://schema.org/givenName and https://schema.org/familyName)

	---------------------------------------------------------------------------
	- graph querying: t210124095504
		- see PoC (very bare)
		
	---------------------------------------------------------------------------
	- slicing & dicing: t210124100531 - (relates to [rereading]/[checkpoint] (see t210121160956)/[snapshot]/[persist]/[cache]/[demux]/[splice]/[partition])
		- see PoC

===========================================================================

