#  backlog: t210121100050
<a name="t210121100050"></a>

===========================================================================
## remarks:
- <a name="rk210127114128"></a>rk210127114128 - low tech for now (consider this as more of a quick brain dump);
	mostly to capture essential features that are missing or are currently subpar;
	will formalize process by increment (will turn into bona fide tasks that can be contributed to by others readily)
- task:
	- <a name="rk210127114129"></a>rk210127114129 - "- pN -" indicates priority (5: low, to 1: high); if none specified, it's TBD
		- <a name="rk210204193138"></a>rk210204193138 - more exclamation marks (!) -> more critical/difficult
		- <a name="rk210204193139"></a>rk210204193139 - more stars (*) -> more work		
	- <a name="rk210204093549"></a>rk210204093549 - it's generally implied that if not much detail is provided in the task, the ID should be searched for in the code
	- <a name="rk210127194859"></a>rk210127194859 - not all tasks and ported to their corresponding place in the code yet, and vice versa
	- <a name="rk210127114130"></a>rk210127114130 - there are a lot more "small" tasks in my notes: I'm in the process of porting them (about halfway done)
		- <a name="rk210202163918"></a>rk210202163918 - this is in itself a big endeavor (thousands of lines of notes)
		- <a name="rk210127114131"></a>rk210127114131 - sometimes the line between creating a task vs addressing the issue is a fine one...
- <a name="rk210127114333"></a>rk210127114333 - for better or worse I try and ID tasks/remarks/assumptions/... as much as possible in order to make it possible to reference them elsewhere, as well as search for them; and yes, i do wake up at night screaming random timestamps.
- <a name="rk210127114621"></a>rk210127114621 - most remarks in here will move over to the docs eventually (see [t210127114652](#t210127114652)); some tags such as [mytag] are meant for me to find the relevant tag/keywords within my notes

===========================================================================
- admin: <a name="admin"></a><a name="t210127114844"></a>t210127114844
	- <a name="t210109164841"></a>t210109164841 - determine funding mechanism going forward
	- <a name="t210109164840"></a>t210109164840 - determine adequate license
	- <a name="t210127114653"></a>t210127114653 - consider arxiv publication?
	- <a name="t210127133131"></a>t210127133131 - switch dev environment to intellij IDEA rather than ScalaIDE? (relates to [t210121165228](#t210121165228))
	- <a name="t210129164800"></a>t210129164800 - rename packages to "$TLD.gallia" once TLD is determined (see [t210109164840](#t210109164840) and <a name="t210109164841"></a>t210109164841)
	- <a name="t210131152002"></a>t210131152002 - p1 - go through all remaining ID-less "FIXME"s and either assign p1/p2 task or change to TODO

===========================================================================
- internals: <a name="internals"></a><a name="t210205113857"></a>t210205113857
	- <a name="t201223100652"></a>t201223100652 - p4 - setup proper DI (eg for spark/mongodb); macwire maybe?
	- <a name="t210114111539"></a>t210114111539 - p2 - @Narrow: identitify wrapped Us (z.map()) vs full on Zs, so can pinpoint problematic object for instance + provide index/_id; runtime errors can be hard to figure out otherwise
	- <a name="t210116153713"></a>t210116153713 - p5 - homogenize ClassTag vs WeakTypeTag throughout (always use latter when possible? ie outside of spark)
	- <a name="t210129114731"></a>t210129114731 - p5 - provide convenient diffing mechanism (relates to [t210129114523](#t210129114523)), for both schema and data
	- <a name="t210127173933"></a>t210127173933 - p2 - @Max3/@Max5 - add missing code (rationale for 3 or 5: if you need more than N, either you can use an intermediate state or you may just be doing something wrong)
	- <a name="t210122161652"></a>t210122161652 - p1 - investigate grab/squash (orphan/combine) vs VO
	- heads:
		- <a name="t201007093053"></a>t201007093053 - p4 - provide HeadPairO - forKeyPair, for group(_.firstKey).by(_.lastKey)
		- <a name="t201021120753"></a>t201021120753 - p4 - provide HeadOptionO, eg as result of u.filter/u.find (see [t201023083923](#t201023083923))	
	- cleanup: <a name="t210202165641"></a>t210202165641
		- <a name="t210124092716"></a>t210124092716 - p3 - codegen (very boilerplaty) - using a lot of sed at the moment
		- <a name="t210110103720"></a>t210110103720 - p4 - subclass Tq and Ttq rather than using "ev: X <:< Y"
		- <a name="t210128161046"></a>t210128161046 - p3 - add/create @Wide annotations (@Narrow being implicit when not @Wide)
		- <a name="t210121170823"></a>t210121170823 - p4 - use private whenever possible

===========================================================================
- DAG: <a name="DAG"></a><a name="t210205113853"></a>t210205113853
	- <a name="t210116120349"></a>t210116120349 - p5 - investigate existing graph libs rather
	- <a name="t210128152949"></a>t210128152949 - p2 - add missing cycle detection
	- <a name="t210106101457"></a>t210106101457 - p4 - meta-only run - may be great for the likes of <a name="t210115115736"></a>t210115115736 (generate intermediate [dataclass])
	- <a name="t210106101459"></a>t210106101459 - p5 - data-only run, requires standalone data version first (see [t210104164037](#t210104164037)); may also be complicated by atoms that require pre/post schemata (eg _JsonObjectFileInputU, _SortByAll, ...)
	- meta:
		- <a name="t201214105653"></a>t201214105653 - p4 - [hack] - address "resultCls" hack
		- <a name="t210114113316"></a>t210114113316 - p5 - reenable graphviz dot's output
	- data:
		- <a name="t201027130649"></a>t201027130649 - p4 - abstract runner strategy ("naive" strategy at the moment)
	 	- <a name="t210114125607"></a>t210114125607 - p5 - improve "InputData" afterthoughts (meant to help with debugging)

===========================================================================
- types: <a name="types"></a><a name="t210121124808"></a>t210121124808
	- <a name="t210115151942"></a>t210115151942 - p1 - @TypeMatching/@PartialTypeMatching - to help find where types are being pattern-matched easily

	- <a name="t210110094829"></a>t210110094829 - p1 - opaque nesting: accept Obj as value, albeit the standalone version (see [t210104164037](#t210104164037)); do not limit types to [basictype]; could also help where need to provide newKeys (eg <a name="t210202172304"></a>t210202172304)
	- <a name="t210110095252"></a>t210110095252 - p5 - BLOB/CLOB (for now must use base64ed version)
		- <a name="t210128161507"></a>t210128161507 - p5 - investigate typical unstructured data (videos, pix, ...) manipulations
	- <a name="t210115144940"></a>t210115144940 - p5 - finalise "null" representation handling (null vs NaN vs [] vs None vs ...)
		- <a name="t210203124717"></a>t210203124717 - NaN: tracking/support + check not in Obj (also see [t210203124840](#t210203124840), checking value types)
	- <a name="t210124153304"></a>t210124153304 - p2 - add all the java.lang primitives, and the .sql ones; automatically convert to scala counterpart though?
	- <a name="t210108114447"></a>t210108114447 - p5 - support own "flag" type? or just Option[Unit]?
	
	---------------------------------------------------------------------------
	- numbers: <a name="t210205113841"></a>t210205113841
		- <a name="t201017102332"></a>t201017102332 - p1 - @NumberAbstraction (formerly @IntDouble): so can locate places where Numbers need to be properly abstracted (especiall integer vs real); also see 210123095857@ReduceReturnType (unchanged/int/double)
		- <a name="t201209095425"></a>t201209095425 - p3 - @IntSize: so can locate places with Int is used for size (as opposed to Long in Spark for instance, see [t210122094438](#t210122094438))
		- <a name="t210128162336"></a>t210128162336 - p5 - offer a "dint" accessor, such that data.dint('foo) gives 3 (Int) from 3.0 (Double) - common enough
		- <a name="t210109142406"></a>t210109142406 - p5 - n-dimensional arrays (including n=1)
			- <a name="t210127141259"></a>t210127141259 - dedicated matrix/tensor object (dense/sparse)
			- <a name="t210127141258"></a>t210127141258 - investigate existing libraries; are they all BLAS/LAPACK based? relates to [t210121095207](#t210121095207) (scala-native)

	---------------------------------------------------------------------------		
	- time: <a name="t210205113839"></a>t210205113839
		- <a name="t210202160406"></a>t210202160406 - p1 - [research] - keep time types (date/datetime) altogher? are they more a manipulation detail? e.g. {"date": "2021-02-05"}.read().transform(_.string('date)).using(_.parseIsoDate.getYear)); could also provide "overlay" shorthands, eg: e.g. ....transform(_.date('date) /* =.string+parse*/).using(_.getYear))
			- <a name="t210202160405"></a>t210202160405 - p1 - [missing] - at the moment none of the serialization format support reading up time types as would be declared in schema
		- <a name="t210202160407"></a>t210202160407 - p3 - provide <, <=, >, >= for time-related types as well
		- <a name="t210202124121"></a>t210202124121 - p3 - need a way to abstract date/dateTime, eg both can have a day added to

	---------------------------------------------------------------------------
	- enums: <a name="t210205113844"></a>t210205113844
		- _remarks_:
			- a boolean can either be seen as 0/1 integers, or as a special kind of enum			
		- <a name="t210201095414"></a>t210201095414 - p2 - missing enum accessor support, eg _.enum\[MyEnum\]('f)
		- <a name="t210114093525"></a>t210114093525 - p4 - capture enum values (will need to adapt serialization)
		- <a name="t210110095228"></a>t210110095228 - p5 - also support scala enum (as opposed to enumeratum)
		- <a name="t210116114654"></a>t210116114654 - p5 - double check ModifyObj behavior OK
		
	---------------------------------------------------------------------------		
	- Whatever: <a name="t210205113848"></a>t210205113848
		- _remarks_:
			- affects: transform, generate, fuse/fission, filter/findBy, pivot, removeIf;
			- keep to a minimum...
		- <a name="t210111135617"></a>t210111135617 - p5 - add more common Seq/String/number operations for Whatever?			
		- <a name="t210202160537"></a>t210202160537 - p2 - missing combinations of number types for plus/times
		- <a name="t210202160709"></a>t210202160709 - p3 - more formatting value types
		- <a name="t210204170956"></a>t210204170956 - create workaround for: def + (that: Int): TypedWhatever\[Int\] (can be Double); relates to [t201017102332](#t201017102332) (@NumberAbstraction)
		- <a name="t210113124437"></a>t210113124437 - need to adapt mechanism to obtain 0 when missing; also "size" ambiguity (container vs length of seq/string)
		- <a name="t210204170740"></a>t210204170740 - occurrences of "whatever0": need to determine if/when must use ContainedWhatever or if isWhatever okay
		- <a name="t210201164613"></a>t210201164613 - p2 - [bug] - fix .transform(_.typed\[Seq\[_\]\]('f)).using(_.size), or provide .anys (if only need eg .size, or .slice(1, 3))

===========================================================================
- stats: <a name="stats"></a><a name="t210128151632"></a>t210128151632
	- <a name="t210115140107"></a>t210115140107 - p5 - use dedicated lib? or just wrap commons'?
	- <a name="t210118083814"></a>t210118083814 - p2 - new version (ReducingStats)
		- <a name="t201207170908"></a>t201207170908 - p5 - stats [dataclass] mapping to/from; lite, full;
		- non-number stats:
			<a name="t201209145048"></a>t201209145048 - p5 - string/enum/boolean stats: allow only doing top/bottom n
			<a name="t210118084833"></a>t210118084833 - p2 - FIXME: dates, strings...
		- number stats:
			- <a name="t210204164412"></a>t210204164412 - full vs light versions
			- <a name="t210118084355"></a>t210118084355 - p5 - [feature] - add skewness, kurtosis, mode, IQR, more percentiles, median/mean absolute deviation (MAD), trimmed mean/median, geometric mean
			- <a name="t210118084356"></a>t210118084356 - p5** - distribution guess scoring? (pretty costly...)
			- integers:
				- <a name="t201207134039"></a>t201207134039 - p5 - rounding/floor/ceiling for int values (eg for mean, median, ...)

===========================================================================
- data: <a name="data"></a><a name="t210205113903"></a>t210205113903
	- <a name="t210104164037"></a>t210104164037 - p5 - standalone data-only version with most operations (relates to [t210104164036](#t210104164036))
		- <a name="t210104164038"></a>t210104164038 - p5 - standalone json (gson) version for pre/post-processing (relates to input pre-processing: <a name="t210202112439"></a>t210202112439)
	- <a name="t210107094213"></a>t210107094213 - p5 - ensure if nested multiple elements then use List, not any Seq (especially not Stream)
	- <a name="t210125111144"></a>t210125111144 - p3 - consider using an actual NonEmptyList class to represent Pes (such as cats') instead of Option[Seq]? [research]
	- <a name="t210114154924"></a>t210114154924 - p5 - read first line (UrlLike.firstLine) - generalize to N lines + make optional + cache
	- <a name="t210128135801"></a>t210128135801 - p5 - what would a columnar in memory counterpart look like? look into/integrate with Apache Arrow? [research]
	- <a name="t210129114523"></a>t210129114523 - p5 - provide both sorted (via meta) and unsorted equals? [term]: "equality" is tricky, is foo=3+bar=baz the "same" as bar=baz;foo=3? (also see [t210129114731](#t210129114731))
	- <a name="t210110203020"></a>t210110203020 - p3 - [bug] - contains needs to be able to deal with multiplicity in nesting(s) - paths.values.filter(!o.contains(_))
	- streamer: <a name="t210115115843"></a>t210115115843
		- <a name="t210127193230"></a>t210127193230 - p3 - externalize streamer as its own independent library
		- <a name="t210115104555"></a>t210115104555 - p5 - fix Iterator version
			- <a name="t210116154537"></a>t210116154537 - p5 - rereading
				- <a name="t210115103130"></a>t210115103130 - p5 - resulting missing implementations
		- <a name="t210114145059"></a>t210114145059 - p5 - generalize StreamerType enum: inMemory, iterator, RDD
		- <a name="t210117112314"></a>t210117112314 - p5 - take/drop/sample/head/last + related (takeRight, ...) issue with @Distributivity
		- <a name="t210205121008"></a>t210205121008 - p3 - offer a toIteratorAndCloseable: (Iterator[Obj], Closeable) + aptus.Closeabled; also for Streamer
		- <a name="t210204105730"></a>t210204105730 - offer streamer find?
	- <a name="t210203124951"></a>t210203124951:
		- <a name="t210110095425"></a>t210110095425 - p5 - the Any part: consider a wrapping ADT (cost of wrapping vs pattern matching on Any)
		- <a name="t210203124840"></a>t210203124840 - p1 - check value type is part of [basictype] (also see [t210203124717](#t210203124717))

===========================================================================
- target selection: <a name="target-selection"></a><a name="t210205113906"></a>t210205113906
	- <a name="t210107203932"></a>t210107203932 - p5 - cleanup the big mess
	- untyped:
		:
	- typed:
		- <a name="t210113162449"></a>t210113162449 - p5 - phase out legacy _explicit
		- <a name="t210113114451"></a>t210113114451 - the likes of ifString  should also act as .string(...) since they can't be anything else
	- <a name="t210127195422"></a>t210127195422 - p5 - allow an 1.2.1-like array notation?
	- <a name="t210127195627"></a>t210127195627 - p5 - tupleN for key/path: eg for group x by y (Tuple2)

	- <a name="t210107203932"></a>t210107203932 - p3 - cleanup and fine-tune selections (typed and untyped)
	- <a name="t210110094731"></a>t210110094731 - p5 - offer more target "selection" when feasible (eg .convert(_.firstKey).toInt) (otherwise must rely more on forX mechanisms, which is more coarse)
	- <a name="t210110094730"></a>t210110094730 - p5 - offer more for-each field operation shorthands (eg .convert('f, 'g, 'h).toInt) when practical; (otherwise must rely more on forX mechanisms, which is more coarse)

===========================================================================
- validation: [vldt] <a name="validation"></a><a name="vldt"></a><a name="t210205113909"></a>t210205113909
	- <a name="t201210104557"></a>t201210104557 - p2 - all missing actions validations (lots)
	
	---------------------------------------------------------------------------
	- input: <a name="t210115153348"></a>t210115153348
		- meta:
			- url-like:
				- <a name="t210115193904"></a>t210115193904 - p3 - check URI, regular file vs symlink, ...						
			- RDBMS:
				- <a name="t210115205723"></a>t210115205723 - p5 - validate URI earlier
				- <a name="t210114202848"></a>t210114202848 - p5 - validate query earlier
			- mongo: 
				- <a name="t210114152901"></a>t210114152901 - p5 - actually validate mongo query				

		- data: 
			- <a name="t210115153347"></a>t210115153347 - p1* - missing input validation when schema is provided, as action; eg: RuntimeValidation.validate(c)(obj('f -> Seq(1, 2, 3), 'g -> new java.io.File("") ) ) -> Some(List(ValErr(19,'g,None,unrecognized type))) (see 210115153346@RuntimeValidation); 				

	---------------------------------------------------------------------------
	- output: <a name="t210205113916"></a>t210205113916
		- <a name="t210204163720"></a>t210204163720 - p3 - check writable
		
	---------------------------------------------------------------------------			
	- types: <a name="t210205113919"></a>t210205113919
		- <a name="t210201103739"></a>t210201103739 - p2 - validate T for .typed
		- <a name="t210201164749"></a>t210201164749 - p2 - if ignoring container (eg .stringx('f)), validate not changing container type		
		- <a name="t210201164749"></a>t210201164749 - p1 - transform Whatever to Whatever -> ensure not changing type (and container?)
		- transform x to v:
			- <a name="t210202155202"></a>t210202155202 - p1 - verify result type (e.g if returns Char instead of String accidentally)
		- transform u to x: 
			- <a name="t210202155458"></a>t210202155458 - p1 - verify input is indeed u
		- transform z to x:
			- <a name="t210202155459"></a>t210202155459 - p1 - verify input is indeed z
			
	---------------------------------------------------------------------------			
	- errors: <a name="t210205113922"></a>t210205113922
		- <a name="t210121101206"></a>t210121101206 - p2 - homogenize the errors mechanism
			- <a name="t210121101207"></a>t210121101207 - meta level
			- <a name="t210121101208"></a>t210121101208 - data level
			- <a name="t210121101209"></a>t210121101209 - other
		- warnings: <a name="t201204115411"></a>t201204115411 - p4 - as separate mechanism, to be called indepently
	
	---------------------------------------------------------------------------	
	- key validation: <a name="t210127133546"></a>t210127133546
		- <a name="t210128155944"></a>t210128155944 - p2 - validate new key names for add/replace/underNewKey/pivot/untuplify2/...			
		- <a name="t210127133623"></a>t210127133623 - p3 - special treatement for reserved keys such as '_group, '_left, ...
		- <a name="t210127134525"></a>t210127134525 - macro version if statically provided key (eg .remove('foo) vs .remove(myKeyArg) )
		
	---------------------------------------------------------------------------
	- actions: <a name="t210205113925"></a>t210205113925		
		- pivot:
			- <a name="t210115175242"></a>t210115175242 - p2 - add missing runtime validation of newKeys
			- <a name="t210303101704"></a>t210303101704 - p2 - check reasonnably "to-textable" value
		- zip strings:
			- check fields (container, exists)
			- check at least two

	---------------------------------------------------------------------------
	- misc:
		- <a name="t210128162901"></a>t210128162901 - p5 - macros to check that eg data.add('p -> new java.io.File("/tmp/foo")) indeed uses a valid value type (basic type, [dataclass], opaque object, ... but not say java.io.File)
		- <a name="t210128153122"></a>t210128153122 - p2 - prevent cycles in nested [dataclass] validations + set a max nesting

===========================================================================
- actions: <a name="actions"></a><a name="t210204152754"></a>t210204152754
	-remarks:
		- <a name="rk210204162927"></a>rk210204162927 - [fluency] conveying intent matters, e.g. add (must not already exist) vs replace (must already exist)		
	- cross-cutting:		
		- <a name="t210110104437"></a>t210110104437 - p1 - [hack][bug] - all the renFX/fromFX/fromsFX/explicitFX, eg: nest, unnest, ... -> where renaming is supposed to be possible
		- common:
			- <a name="t210126171839"></a>t210126171839 - p3 - implement a "_then" for good measure and testing; eg data._then(_.rename('foo ~> 'FOO))
			- <a name="t210117110015"></a>t210117110015 - p5 - move the likes of retainFirst and renameSoleKey to common, rather than duplicating them in each (may be tricky)
			- <a name="t210111095156"></a>t210111095156 - p5 - [whatever] - separate all the Whatever (similar to cc); leverage 210122154401 (Quintuplet)
			- <a name="t210111095157"></a>t210111095157 - p5 - [dataclass] - case-class versions: separate all the cc versions (similar to whatever)

	===========================================================================
	- v:
		- <a name="t210202154249"></a>t210202154249 - p3 - operations like forceDistinct for Vs too?
		
	===========================================================================
	- z -> u:
		- <a name="t210131104517"></a>t210131104517 - missing feature? an "unarrayUsing"? relates to pivoting (possibly to <a name="t210128161346"></a>t210128161346); see more at 210131104800@w, see xml POC
			- <a name="t210131104518"></a>t210131104518 - bobjs(bobj('f -> "f1", 'g -> "a"), bobj('f -> "f2", 'g -> "b")) -> ? -> bobj('f1 -> bobj('g -> "a"), 'f2 -> bobj('g -> "b"))
			- <a name="t210131104519"></a>t210131104519 - bobjs(bobj('f -> "f1", 'g -> "a"), bobj('f -> "f2", 'g -> "b")) -> ? -> bobj('f1 ->            "a",  'f2 ->            "b") 				

	===========================================================================	
	- u: HeadO: <a name="t210205113934"></a>t210205113934
		- <a name="t201023083923"></a>t201023083923 - p5 - add find/filter to HeadO as well, to make it an "option" (relates to [t201021120753](#t201021120753))	

		---------------------------------------------------------------------------
		- basics:
		
			- inspect:
				- <a name="t210115180822"></a>t210115180822 - p5 - homogenize "inspect" vs "show" schema; also [term]
				- <a name="t210115175106"></a>t210115175106 - p5 - versions that allows more configuration
					- <a name="t210115180737"></a>t210115180737 - schema: configurable
					- <a name="t210115180738"></a>t210115180738 - data
			
			- add:
				- <a name="t210111113206"></a>t210111113206 - p4 - support adding path, eg: .add('p |> 'f -> "foo") - denormalize if multiples along the way
				- <a name="t210127194716"></a>t210127194716 - p2 - also support append/prepend field(s); maybe genelized as insertion index (including negative)?
				- <a name="t210128155501"></a>t210128155501 - p5 - add a lazy version: => value; also for replace:x
			
			- retain:
				- <a name="t210128162442"></a>t210128162442 - p5 - just implemented as remove all but? or has value as standalone? [research]
				- <a name="t201215121718"></a>t201215121718 - p5 - [optim] - need more than one level for efficiency of retain multiple+path: case class RetainMapping(data: Map[Key, Option[KPathz]])
				- <a name="t210127193137"></a>t210127193137 - p1 - retain to also reorder? or as separate action?

			- convert:
				- <a name="t210128152726"></a>t210128152726 - p4 - [feature] - add missing convert('foo).toEnum[MyEnum]
				- <a name="t210128162159"></a>t210128162159 - p4 - [feature] - convert from JSON string, eg .convert('foo).fromJsonString\[MyDataClass\]("""{"foo":1, "bar":"baz"}""") + convert('foo).fromJsonToObj (see [t210110094829](#t210110094829) opaqueness)

			- set default value:
				- <a name="t210129093607"></a>t210129093607 - p4 - [feature] - offer shortcut setDefaults('foo -> 1, 'bar -> "baz", ...)
				
			- translate:
				- <a name="t210117125042"></a>t210117125042 - p3 - rework translateAll, confusing as it is


		- transform-like:
			- fission/fuse:
				- <a name="t210115175745"></a>t210115175745 - p2 - [hack][bug] - fission/fuse removals

			- generate:
				- <a name="t210202164324"></a>t210202164324 - p2 - missing GenerateZV/UZ/V
			
			- shorthands:
				- <a name="t210205121240"></a>t210205121240 - p3 - more convenience like: prepend, surround, addDay, ... (see aptus')
				- <a name="t210127164512"></a>t210127164512 - missing shorthands: isPresent/isMissing/unquoteKeys
				- <a name="t210205122644"></a>t210205122644 - more missing shorthands: addTo/transform{Group/Left/Right}/reformatTime    				
			
		- asserts:
			- <a name="t210129094319"></a>t210129094319 - add assertIsDistinct

		
		- zip strings:
			- <a name="t210109142621"></a>t210109142621 - p2 - [feature] - add unzipStrings operation (optionally with separator); zip/unzip can act as a form of tranpose; also see [t210111113343](#t210111113343) for unzip
			- <a name="t210111113343"></a>t210111113343 - p5 - [feature] - add support for zip (non-strings) for consistency: bobj('f -> Seq("a", "b", "c"), 'g -> Seq("1", "2", "3").zip('f, 'g).underNewKey('p)
			- <a name="t210110101000"></a>t210110101000 - p2 - [feature] - offer a [guaranteed] zip (if expect no missing fields)			
			
		- untuplify:
			- new keys:
				- <a name="t210117192142"></a>t210117192142 - p5 - [feature] - add enum counterpart to provide newKeys, eg def asNewKeys\[MyEnum\] (also see [t210117192141](#t210117192141) for pivoting)
			
		- nesting-related:
			- <a name="t210109144926"></a>t210109144926 - p5 - [feature] - generalize nest/unnest as "move"
			- <a name="t210109173114"></a>t210109173114 - p5 - [feature] - renest just up to n levels?
			- <a name="t210109175621"></a>t210109175621 - p5 - [feature] - reproduce the optional "as" mechanism: for renest (see [t210116192032](#t210116192032) for generalization)
			- <a name="t210122162650"></a>t210122162650 - p2 - [bug] - meta nest into: handle optional the way nest-under does
			- renest: if all can be opt (see ?); relate to [guaranteed]?

	===========================================================================
	- z: HeadS: <a name="t210205113938"></a>t210205113938
	
		- misc:						
			- <a name="t210202114834"></a>t210202114834 - p2 - [feature] - offer lookup outputs: eg .forceLookup(key = _.string(_id), value = _.int('myInt))): Map[String, Int]
			- <a name="t210116192032"></a>t210116192032 - p3 - [internals] - generalize HasAs/chainzzWithAs mechanism (eg to help with <a name="t210109175621"></a>t210109175621)?
			- <a name="t210127164715"></a>t210127164715 - [bug?] - isEmpty/nonEmpty/if not top-level? (check missing will return size = 0)
			- <a name="t210205122151"></a>t210205122151 - [feature] - offer toRddBased/toInMemoryBased
			- <a name="t210131110455"></a>t210131110455 - p3 - [feature] - tabularize/untabularize
				- <a name="t210131110456"></a>t210131110456: tabularize (also see cartesianProduct); or "rectangularize"? [term]; mass flattening; default the likes of Seq(1, 2, 3) to "1|2|3" (configurable sep)
				- <a name="t210131110457"></a>t210131110457: untabularize (also see reverseCartesianProduct) - reuse table parsing mechanis + mass renesting for common prefixes

		- set default:
			- <a name="t201005102404"></a>t201005102404 - p3 - for multiple only: offer backfill/forward fill

		- distinct:
			- <a name="t210117113705"></a>t210117113705 - p2 - add distinctByAdjacency: convenient if mostly grouped already; for distributivity, do at least per partition		

		- sorting:
			- <a name="t210127193358"></a>t210127193358 - p4 - [fluency] - offer eg sort('f.reversed, 'g.reversed)
			- <a name="t210202164133"></a>t210202164133 - p2 - [fluency] - forbid "missingLast" if not optional field

		- aggregating: <a name="t210127195238"></a>t210127195238			
				- <a name="t210202163542"></a>t210202163542 - p2 - address if no aggregation (in meta)
				- <a name="t210127195214"></a>t210127195214 - p2 - [fluency] - forbid agg(_.foos('f)) -> notice the 's'; already the case in fluent interface?				
				- <a name="t210202163714"></a>t210202163714 - p2 - [hack] data: address temporary hack (.get)
				- <a name="t210131141737"></a>t210131141737 - p3 - [bug?] - .countEach('f, 'h).by('g); countCombos (see 210131141737@w)
				- <a name="t210304115503"></a>t210304115503 - p3 - [feature] - offer a pre-sorted version (also for merging)

			- grouping: <a name="t210127195236"></a>t210127195236
				- DWH/MDX: <a name="t210124100722"></a>t210124100722; add the likes of cascade, cube, rollups, grouping sets, ... e.g. .groupCascade('state %> 'cities, 'city %> 'zips) - see 201227150057				

			- counting:					
				- <a name="t210131140932"></a>t210131140932 - countBy needs to accept _.allKeys; then create shorthand countByAll = countBy(_.allKeys)

		- filter z:
			- <a name="t201021120752"></a>t201021120752 - p4 - [hack] - address HasAsFind hack - (relates to [t201021120753](#t201021120753)@proper HeadOptionU)
			- <a name="t201021120751"></a>t201021120751 - p2 - [feature] - provide Wathever-based SQL-like shorthand for IN: .filter('color).in("blue", "white", "red")
	
		- flatten by:				
			- <a name="t210131101358"></a>t210131101358 - p3 - simplify X in: `[{"values":"g1;g2;g3", "bar": true}, {"values":"g4", "bar": false}] -> X -> [{"values":"g1", "bar": true}, {"values":"g2", "bar": true}, {"values":"g3", "bar": true}]`; X=.transformString('values ~> 'value).using { _.splitBy(";").as.noneIf(_.size == 1) }.flattenBy('value).filterBy('value).isMissing	    	
			- <a name="t210131102306"></a>t210131102306 - cascade if multiple?
			- <a name="t210131102354"></a>t210131102354 - flattenAndUnnestBy{Group,Left,...} - common enough?

		- merging:
			- <a name="t210128130124"></a>t210128130124 - p2 - [fluency] - allow explicit use of in-memory join if one side is small enough ("hash" join) 
			- <a name="t210117143536"></a>t210117143536 - p5 - also handle union within merging conf?
			- <a name="t210124100649"></a>t210124100649 - p4 - [feature] - add multi-joins
			- <a name="t210304115502"></a>t210304115502 - p3 - [feature] - offer a pre-sorted version (also for grouping)
			- [guaranteed]:
				- <a name="t201124153838"></a>t201124153838 - p3 - a bring "[guaranteed]" (no missing); or by default [research:x]?
				- <a name="t201124153839"></a>t201124153839 - p3 - a join [guaranteed]? when not inner?				

		- reducing:
			- <a name="t210122151934"></a>t210122151934 - p2 - ActionsUUReducer0: use newer reducer rather, instead of old ToArray/ToSize/ToSum
							
		- pivoting: <a name="pivoting"></a><a name="pivot"></a><a name="t210304120525"></a>t210304120525
			- new keys:
				- <a name="t210117192142"></a>t210117192142 - p4 - enum counterpart to provide newKeys, eg def asNewKeys\[MyEnum\] (also see [t210117192142](#t210117192142) for untuplify)
				- <a name="t210202172304"></a>t210202172304 - p3 - unspecified: using opaque object as data (relates to [t210110094829](#t210110094829)) - try
			- <a name="t210120171258"></a>t210120171258 - p2 - [feature] - add support for unpivoting
			- <a name="t210117192221"></a>t210117192221 - p3 - configurable key separator	
			- "pivone":
				- <a name="t210303111953"></a>t210303111953: use different structure now
				- <a name="t210303102200"></a>t210303102200: also allow selection for keyKey

===========================================================================
- schema: <a name="schema"></a><a name="t210204152731"></a>t210204152731
	- _remarks_:
		- <a name="rk210127114008"></a>rk210127114008 - a schema is really just data about data (hence "meta"-data);
		- <a name="rk210127114009"></a>rk210127114009 - specifically a schema can be seen as coarse statistics about the data
	- io: see [t210128103821](#t210128103821)	
	- <a name="t210124100957"></a>t210124100957 - p5 - a "confirm" schema action, e.g. [...].confirmSchema[MyDataClass] or .confirmSchema('foo.string, 'bar.int) or .confirmSchema("my/file")		
	- <a name="t210126173150"></a>t210126173150 - p5** - ambitious "[backtracking]" mode [research], whereby no input schema is provided and instead each step ensure consistency with one another only (e.g. don't add a field that was already added in an earlier step); relates to [t210118133408](#t210118133408) [hettype]
	- <a name="t210128165110"></a>t210128165110 - p5** - going to/from schema formats (relate to io's <a name="t210128103821"></a>t210128103821 - generalize schema i/o for any schema-like format)
		JSON schema (see [t210128163913](#t210128163913)), avro (see [t210128163914](#t210128163914)), ES mappings (see [t201028094710](#t201028094710)), ...

===========================================================================
- io: <a name="io"></a><a name="t210204152732"></a>t210204152732
	- misc:
		- <a name="t210121160956"></a>t210121160956 - p3 - [feature] - checkpointing mechanism (relates to [t201108093951](#t201108093951) for z.writeJsons)
		- <a name="t210121171126"></a>t210121171126 - p5 - provide Windows support? try a run (I suspect the likes of '\r' will trip it in local mode at least); support .ini files and so on; are there named pipes equivalent? GNU-sort?

		- schemas: <a name="t210128103821"></a>t210128103821 - p5 - generalize schema i/o for any format schema-like that can be (reasonnably) parsed, may be useful to limit code duplication (also relates to [t210128165110](#t210128165110) - going to/from schema formats)								

		- pre/post processing: [preproc]/[postproc]: <a name="t210202113208"></a>t210202113208				
			- [hettype] handling: see [t210118133408](#t210118133408)@research
			- (for url-like only) allow pre-processing: <a name="t210202112203"></a>t210202112203
				- pre-processing lines: <a name="t210202112245"></a>t210202112245 - p3 - to e.g. skip lines, combine lines, ...
				- pre-processing line: <a name="t210202112246"></a>t210202112246
					- json:
						- <a name="t210202112439"></a>t210202112439 - p1 - allow gson pre-processing, eg .jsonNull('foo).as("null"), .emptyJsonArray('foo).as("empty"); see [t210118133408](#t210118133408)@research for type heterogeneity [hettype]
				- (for tables only): pre-processing cells: <a name="t210202112247"></a>t210202112247 - p3 - 

			- (for url-like only) allow post-processing: <a name="t210202112204"></a>t210202112204
				- post-processing lines: <a name="t210202112255"></a>t210202112255
				- post-processing line: <a name="t210202112256"></a>t210202112256					
					- json:
						- <a name="t210202112440"></a>t210202112440 - p2 - allow gson post-processing eg .toJsonNullIfMissing('foo), .toJsonArrayIfMissing('foo); see [t210118133408](#t210118133408)@research for type heterogeneity [hettype] and <a name="t210104164038"></a>t210104164038 for standalone json
				- (for tables only): post-processing cells: <a name="t210202112257"></a>t210202112257 - p3 -

	===========================================================================
	- format support: <a name="t210204135415"></a>t210204135415
	
		- file-based:
			- <a name="t210128163910"></a>t210128163910 - GPPL classes source code (POJO/POCO/POKO/js/python/rust/...); also see [t210117105638](#t210117105638) for in-memory
				- <a name="t210115115736"></a>t210115115736 - p2 - allow writing schema as scala [dataclass] hierarchy at any given step (using field name for nested class names by default, if ambiguous)
					may be convenient especially if run in meta-only mode (<a name="t210106101457"></a>t210106101457), to provide both incoming/outgoing cc for a complicated transformation							
			- <a name="t201103114910"></a>t201103114910 - config files: java properties file (eg config.properties: foo=bar\nbaz=3\n...), *nix config files (cat foo.conf -> #comment\nkey=value\n ...); will need charset support too
			- <a name="t210128160407"></a>t210128160407 - p3 - handle XML (see PoC code)
			- <a name="t210128163914"></a>t210128163914 - avro/thrift/protobuf
			- <a name="t210128163915"></a>t210128163915 - parquet/ORC/RCFile/CarbonData (also look into feather?)
			- <a name="t210128160323"></a>t210128160323 - p3 - excel (via apache POI), eg "/path/to/file.xlsx", use sole sheet or provide sheet name as "container"; see POC code
			- <a name="t201028110431"></a>t201028110431 - pdf...? try and at least extract tables? probably tricky... https://stackoverflow.com/questions/3424588/programmatically-extract-pdf-tables
			
			- more:
				- <a name="t210204142554"></a>t210204142554 - HDF/HDF5
				- <a name="t210204142555"></a>t210204142555 - SequenceFile								

		---------------------------------------------------------------------------	  							
		- databases: <a name="t210205113943"></a>t210205113943
		
			- 210204135028 - RDBMS:
				- schema: <a name="t210204135246"></a>t210204135246
					- <a name="t210128163911"></a>t210128163911 - in: JDBC (meta)
					- <a name="t210128164004"></a>t210128164004 - out: DDL
				- data: <a name="t210204135245"></a>t210204135245 - JDBC																							

			- <a name="t210128164010"></a>t210128164010 - mongodb:														
				- <a name="t201223092203"></a>t201223092203 - schema look into https://docs.mongodb.com/realm/mongodb/document-schemas
				- <a name="t210128164011"></a>t210128164011 - data
					- <a name="t210110112325"></a>t210110112325 - p5 - cleaner version of command parsing
					- <a name="t210114153517"></a>t210114153517 - p5 - remove jongo reliance

			- <a name="t210128164016"></a>t210128164016 - elasticsearch (ES):
				- schema: <a name="t201028094710"></a>t201028094710 - offer schema via mappings							
				- data: <a name="t210204140033"></a>t210204140033

			- more:
				- <a name="t210204140102"></a>t210204140102 - neo4j (cypher); schemes: neo4j+s, bolt+routing?
				- <a name="t210204142939"></a>t210204142939 - dynamoDB - see https://aws.amazon.com/getting-started/hands-on/create-manage-nonrelational-database-dynamodb/3/; table = dynamodb.Table('Books'); resp = table.get_item(Key={"Author": "John Grisham", "Title": "The Rainmaker"}) - no plain text QL?
			  	- <a name="t210204142940"></a>t210204142940 - cassandra (CQL, via JDBC?)
				- <a name="t210204140103"></a>t210204140103 - redis

		---------------------------------------------------------------------------								
		- in memory: <a name="t210205113946"></a>t210205113946
			- <a name="t210128163912"></a>t210128163912 - Spark Row
			- <a name="t210117105638"></a>t210117105638 - [dataclass] - (see code 210117105638@w); also see [t210128163910](#t210128163910) for source code
				- in:```
					(x:     MyCc ).read  ()
					(x: Seq[MyCc]).stream()```
				- out: readCC/populateDC/writeCC + z; ```
					val x: MyCC           = u.populate[MyCc]
					val x: Iterator[MyCC] = z.populate[MyCc] // or as Streamer```

		---------------------------------------------------------------------------
		- schema-only: see [t210204142528](#t210204142528)

		---------------------------------------------------------------------------
		- web: <a name="t210205113949"></a>t210205113949
			- <a name="t210128163917"></a>t210128163917 - GraphQL
			- <a name="t210128163918"></a>t210128163918 - semantic web: OWL (schema/read/write) + SPARQL (read)
			- <a name="t210204142941"></a>t210204142941 - REST architecture:
				- schema: varies... see swagger, raml, blueprint, JSON-LD, ...
				- data: at least provide very basics of GET, POST, PUT, ...
			- <a name="t210128165639"></a>t210128165639 - p5 - what would support for WSDL/SOAP look like? (for legacy)						

		---------------------------------------------------------------------------
		- data-only: <a name="t210205113951"></a>t210205113951
			- json:
				- <a name="t210204095517"></a>t210204095517 - p5 - long term: replace gson with scala based json library			
			- <a name="t201028110434"></a>t201028110434 - yaml				
			- <a name="t201028110435"></a>t201028110435 - typesafe config (HOCON)
			- <a name="t201028110436"></a>t201028110436 - MessagePack?  			
		
		---------------------------------------------------------------------------
		- schema-only: <a name="t210204142528"></a>t210204142528
			- <a name="t210128163913"></a>t210128163913 - JSON schema							
			- <a name="t210128163916"></a>t210128163916 - swagger docs (see https://editor.swagger.io/)							
			- <a name="t210204135521"></a>t210204135521 - serialization for gallia's own representation (coin [term])		
					x <a name="t210204135633"></a>t210204135633 - pretty JSON (current default)
					- <a name="t210128164127"></a>t210128164127 - compact-JSON/YAML/HOCON
					- <a name="t210204135644"></a>t210204135644 - our BTON format (see 201230133034 for POC code)
					...			

		---------------------------------------------------------------------------
		- file systems: <a name="t210204143321"></a>t210204143321			
			- <a name="t210120153618"></a>t210120153618 - p2 - hdfs
			- mongo: mongodb+srv?
			- more distributed FS: gluster (gluster://), IPFS (ipfs://), Alluxio/Tachyon (alluxio://), Swarm (decentralized)? ...
		  - object storage: <a name="t210204143322"></a>t210204143322
				- <a name="t210120153619"></a>t210120153619 - p2 - s3 support
				- more: google cloud storage, azure, openstack swift? IBM's?

		---------------------------------------------------------------------------
		- compression: <a name="t210118103219"></a>t210118103219 - on top of gz/bz2
			- <a name="t210120153620"></a>t210120153620	- lzo support
			- more: snappy, lz4, ZSTD

	===========================================================================
	- in: <a name="in"></a><a name="t210205114007"></a>t210205114007
		- validation: vldt: see [t210115153348](#t210115153348)

		- misc: <a name="t210205114028"></a>t210205114028
			- <a name="t210114201159"></a>t210114201159 - p5 - implement missing convenience creation methods (eg "hello world".content, ...)
			- <a name="t210114144622"></a>t210114144622 - p5 - also allow iterator mode for both JDBC and mongodb
			
		- inferring: <a name="t210205114025"></a>t210205114025
			- <a name="t210122135629"></a>t210122135629 - p5 - [missing] - implement mirror index in IndexEntry
			- <a name="t210204151934"></a>t210204151934 - p1 - [bug] - if file/url is empty
			- <a name="t210204120123"></a>t210204120123 - p3 - [uexp] - improve error handling, especially around heterogeneous types [hettype] (e.g .int vs string)

		- url-like: <a name="t210205114024"></a>t210205114024
			- <a name="t210122135525"></a>t210122135525 - p1 - ignore trailing empty line by default if present at the end - very common (relates to [t210202112245](#t210202112245): pre-processing lines)
			- <a name="t210128160505"></a>t210128160505 - p3 - make drop any empty line/row (post-trimming) be the default behavior?
			- <a name="t210202165017"></a>t210202165017 - p3 - allow skipping first/last n lines explicitly (pretty common for table)

			- json: <a name="t210205114021"></a>t210205114021
				- <a name="t210116150154"></a>t210116150154 - p3 - [bug] - must remove nulls PRIOR to size
				- <a name="t201103154749"></a>t201103154749 - p5 - gson: look into cost of reflection setAccessible(true)			
				- <a name="t201221175254"></a>t201221175254 - p5 - array: stream rather than read all in memory

			- table: <a name="t210205114019"></a>t210205114019
				- <a name="t201103174026"></a>t201103174026 - p3 - [bug] - handle rarer case where columns names are repeated? use _1, or fail if values differ for two columns with the same name?
				- <a name="t201028110146"></a>t201028110146 - a tsv/csv convention that allows providing basic types succinctly, eg in header 'age:integer' (instead of just 'age'), favorite_colors:strings(","), middle_name:string?(""), ...; [research]
				- <a name="t210116110159"></a>t210116110159 - p5 - support header at more than n=0? or only as preproc? (relates to [t210122135525](#t210122135525))
				- inferring:
					- <a name="t210122135629"></a>t210122135629 - p5 - implement mirror index in IndexEntry
					- <a name="t210204151934"></a>t210204151934 - p1 - [bug] - if table is empty
				- fluency:
					- <a name="t210122162835"></a>t210122162835 - p4 - if NoInferring, disallow .nullString and so on

		- RDBMS: <a name="t210205114014"></a>t210205114014
			- <a name="t210115205609"></a>t210115205609 - p5 - actual URI decoding
			- <a name="t201223092238"></a>t201223092238 - p4 - [optim] - use JDBC meta  for schema instead of inferring (current)
			- <a name="t210114145431"></a>t210114145431 - p3 - injection attack protection (use lib?)
			- <a name="t210128160241"></a>t210128160241 - p2 - try with FileMaker (often used by labs along with excel) - jdbc:filemaker://localhost:2399/mydb

	===========================================================================
	- out: <a name="out"></a><a name="t210205114012"></a>t210205114012
		- misc:
			- <a name="t210122140324"></a>t210122140324 - p1! - [bug] - ensure sole or last leaf before running
				- closely related to <a name="t210121160956"></a>t210121160956-checkpointing (and <a name="t201108093951"></a>t201108093951-returning Unit or head)
				- delaying run causes issues for formatString that uses a StringWriter
				- 210205063004: would make the potentially problematic assumption that a fork isn't requested *after* one of the leaf has been acted upon
			- <a name="t210202165243"></a>t210202165243 - p4 - [feature] - allow append as well		
			- <a name="t210204193417"></a>t210204193417 - p3 - [feature] - for practicality, provide informal describe()/describeMeta()/describeData() (if no nesting then as formatted table, and so on)
		- json:
			- <a name="t201230133034"></a>t201230133034 - p5 - redo the "more readable" json version (see 210204164133@w), and/or do a BTON equivalent

		- schema: <a name="t210205114016"></a>t210205114016
			- <a name="t210115114631"></a>t210115114631 - [feature] - possibly none (only writing data)
			- <a name="t210128164202"></a>t210128164202 - [feature] - possibly more than one
			- <a name="t210115114509"></a>t210115114509 - p5 - [feature] - configurable schema filename suffix (vs ".schema" in ".schema.json") to override default
			- <a name="t210128164040"></a>t210128164040 - corresponding write [fluency] - eg schema(_.exclude), schema(_.json), schema(_.fileName("foo")), .schema(_.compression)

===========================================================================
- performance: [optim]: <a name="performance"></a><a name="optim"></a><a name="t210121095401"></a>t210121095401
	- <a name="t210121170923"></a>t210121170923 - p5 - need some benchmarking numbers before optimizing, maybe use TCP-DS? (check license)
	- <a name="t210104164036"></a>t210104164036 - p5 - UData as Vector\[Seq\[Any\]\] (relates to [t210104164037](#t210104164037))
	- <a name="t210110100144"></a>t210110100144 - p5 - macros for [dataclass] to/from Obj + field names enum
	- <a name="t210115095741"></a>t210115095741 - von neumann bottleneck: also give easy access to .par where applicable; for iterator: see [t210115095742](#t210115095742)
		- <a name="t210115095740"></a>t210115095740 - p2 - Seq version
		- <a name="t210304124932"></a>t210304124932 - p2 - Iterator version
			- ~~<a name="t210304125018"></a>t210304125018 - naive `.grouped` version~~ - see 210303141926 in the code for first pass
			- <a name="t210303144449"></a>t210303144449 - investigate Future.traverse approach (trickier)			
	- <a name="t210115095838"></a>t210115095838 - p5 - more reliance on meta to help with data, so as to minimize pattern matchings at runtime (eg see [t201019110649](#t201019110649) for reorderKeysRecursively, obj to gson, formatting value in table (array or not))
	- <a name="t210121095207"></a>t210121095207 - p5 - look into scala-native (also see [t210109142406](#t210109142406) for matrices)
	- <a name="t210121170909"></a>t210121170909 - p5 - add @inline, @switch, @tailrec, @specialized whenever relevant
	- opt-out:
		- <a name="t210107094406"></a>t210107094406 - p5 - possibility to opt out of the checks like non empty object (for performance); worth it?
		- <a name="t210114143028"></a>t210114143028 - p5 - opt out of util.Try for runtime; worth it?
	- specializations:
		- <a name="t210114170853"></a>t210114170853 - p5 - grouping: separate at least 11/1N/N1/NN atoms?
		- <a name="t201019161520"></a>t201019161520 - p5 - aggregation: specialized version of sumby/countby/... rather than combos
		- more optional vs [guaranteed] atoms version (formerly "A/B" versions): _FilterBy1, _AssertO1, ...		
	- <a name="t210106120036"></a>t210106120036 - p5 - pointless as it is, point will be to project/retain *before* creating obj (data projection)
	- <a name="t210121165741"></a>t210121165741 - p5 - does -Xdisable-assertions also turns of require? if not, is it possible? [build]
	- plan: <a name="t210204112440"></a>t210204112440
		- <a name="t210126171438"></a>t210126171438 - atom plan optimization (also relates to [t201027130649](#t201027130649)/abstract runner)
			- predicate push downs,
			- early pruning,
			- code generation
			- ...
		- optimize traversal if dag is chain, especially if nested
		- plan caching?
	- spark: <a name="t210204112444"></a>t210204112444
		- <a name="t210121164920"></a>t210121164920 - p5 - delegate to spark SQL when feasible? might be tricky unless trivial; is Tungsten only used with spark SQL?
		- <a name="t210126171605"></a>t210126171605 - provide Obj Encoder
		- <a name="t210204112431"></a>t210204112431 - create an Array backed (at least initially) Objs due to prominence in spark?
		- <a name="t201126163157"></a>t201126163157 - p5 - [optim] - ensure distinct: to avoid looping more than necessary, consider sort followed by rdd.mapPartitions(_.sliding(size, step), preservesPartitioning)?
		- <a name="t201126111306"></a>t201126111306 - p5 - confirm no better way; no {left,right,inner}CoGroup available it seems; note: using the {left,right,inner}OuterJoin here would force us to redo an unncessary re-grouping         
		- <a name="t210122095106"></a>t210122095106 - p5 - confirm no performance impact: .filter(_._2._1.nonEmpty).filter(_._2._2.nonEmpty) vs combined

===========================================================================
- spilling: <a name="spilling"></a> <a name="poor-man-scaling"></a><a name="t210204111309"></a>t210204111309
	- _remarks_:
		- <a name="rk210304115313"></a>rk210304115313 - this is basically a hack, but well, this isn't called the rich-man scaling after all
	- ~~<a name="t210304134747"></a>t210304134747 - p1 - GnuSortByFirstFieldHack~~
	- ~~<a name="t210304134748"></a>t210304134748 - p1 - GnuJoinByFirstFieldHack~~	
	- <a name="t210304094613"></a>t210304094613 - p3 - add missing GnuSortHack, wrapping eg: sort -t$'\t' -k1n,2,3r
	- <a name="t210304095420"></a>t210304095420 - p3 - try Windows: looks like GNU sort can be installed for windows as well: same options?
	- <a name="t210304134826"></a>t210304134826 - p3 - confirm mac ok as-is
	- <a name="t210304095755"></a>t210304095755 - p3 - simplying locale setting

===========================================================================
- spark: <a name="spark"></a><a name="t210121164812"></a>t210121164812
	- _remarks_:
		- not a spark expert so probably a lot more can be done to better take advantage of it
	- indirection:
		- spilling: see [t201131143901](#t201131143901)
		- optim: see [t210204112444](#t210204112444)
	- fluency:
		- <a name="t210122094521"></a>t210122094521 - p5 - provide convenient access to setting numPartitions
		- <a name="t210121164813"></a>t210121164813 - p5 - provide convenient to mapPartition [performance]
		- <a name="t210121164814"></a>t210121164814 - p5 - provide convenient to partition combiner [performance]
	- i/o:
		- <a name="t210121164950"></a>t210121164950 - p3 - [missing] - actually handle charset
		- <a name="t210121164951"></a>t210121164951 - p3 - [missing] - actually handle compression
	- logging:
		- <a name="t210122092713"></a>t210122092713 - p5 - proper logging mgmt
		- <a name="t210122092619"></a>t210122092619 - p5 - hide "Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties" message
	- distributivity:
		- <a name="t210123183101"></a>t210123183101 - p4 - @Distributivity - all the spots where distributity might be an issue (eg .head does not make sense unless sorted first)
			- <a name="t210122094456"></a>t210122094456 - p5 - take/drop/sample
	- misc:
		- <a name="t210121164949"></a>t210121164949 - p5 - handle Serialization issues (likely will happen when)		
		- <a name="t210123183102"></a>t210123183102 - p4 - @Scalability - places where scalability might be an issue, especially if processing all in-memory at the moment: eg cartesian product (and reverse), reductions, unarray, string formatting
		- <a name="t210122101756"></a>t210122101756 - p2 - [hack] - address giant hack (setting StartReadFluencyRDD.streamLinesViaRDD(sc))
		- <a name="t210122101757"></a>t210122101757 - p3 - [missing] - cache SparkContext
		- <a name="t210122102109"></a>t210122102109 - p5 - flatMap: address casting .asInstanceOf[SparkColl[B]]
		- <a name="t210122094438"></a>t210122094438 - p2 - change to Long for size by default? maybe offer sizeLong: Long and sizeInt: Int; relates to [t201209095425](#t201209095425) (@IntSize)
		- <a name="t201216101136"></a>t201216101136 - p5 - [research] - try a org.apache.spark.sql.Dataset[Obj] counterpart; why is Dataset under sql?
		- <a name="t210204095516"></a>t210204095516 - p4 - try spark 3.x
		- <a name="t201106123320"></a>t201106123320 - catch error earlier (for _.rdd(...))
		- <a name="t210204110958"></a>t210204110958 - actually try a reduce
		- <a name="t210204110959"></a>t210204110959 - actually try a fork
		- <a name="t210204110908"></a>t210204110908 - limit still around 2GB?		
		- <a name="t201101115807"></a>t201101115807 - investigate "The iterator will consume as much memory as the largest partition in this RDD"
		- <a name="t201101121424"></a>t201101121424 - confusing: `preservesPartitioning` indicates whether the input function preserves the partitioner, which should be `false` unless this is a pair RDD and the input function doesn't modify the keys.

===========================================================================
- build: <a name="build"></a><a name="t210121165130"></a>t210121165130
	- _remarks_:
		- semver: will be very liberal with my changes to PATCH version at least for the 0.0.x series, will then formalize process by increment			
	- <a name="t210121101237"></a>t210121101237 - p1 - 2.13 support
		- ~~make it compile~~
		- address resulting new warnings
		- replace all instances of aptus' `thn` with new `pipe` mechanism (and `sideEffect` with `tap`)
	- <a name="t210121165146"></a>~~t210121165146 - p2 - cross-building support (2.12 onward)~~
		- ~~hacky support (see 210214150322)~~
		- ~~proper support~~
	- <a name="t210121101238"></a>t210121101238 - p3 - prototype for scala 3.x
	- <a name="t210121165120"></a>t210121165120 - p5 - shade guava [spark]
	- <a name="t210121165147"></a>t210121165147 - p5 - add support for test coverage
	- <a name="t210121165219"></a>t210121165219 - p5 - address warnings / add more scalac options
	- <a name="t210121165228"></a>t210121165228 - p5 - try intellij IDEA to find unused classes (relates to [t210127133131](#t210127133131))? or try with sculpt?
	- <a name="t210121165229"></a>t210121165229 - p5 - automatic code formatting (allow override) (relates to [t210124151701](#t210124151701) - code style:x); may be too tricky to match current style enough though
	- executable:
		- <a name="t210204101108"></a>t210204101108 - p2 - publish jars on maven central
		- <a name="t210121165247"></a>t210121165247 - p5 - try bytecode optimiser(s)
		- <a name="t210115152435"></a>t210115152435 - p1 - error origins when using jars shows "jrt:/java.base/jdk/internal/reflect/NativeMethodAccessorImpl.class(NativeMethodAccessorImpl.java:...)" instead of source -> change to "source unavailable" message							
	- <a name="t210204101632"></a>t210204101632 - p3 - create a monorepo
	- <a name="t201022170436"></a>t201022170436 - p5 - actually enfoce the likes of @aptus.fordevonly
	- <a name="t210121171033"></a>t210121171033 - p5 - make sure instance of null are all legit (mark the legit ones so build can ignore)
	- <a name="t210125110147"></a>t210125110147 - p3 - investigate sbt alternatives

===========================================================================
- testing: test: <a name="testing"></a><a name="test"></a><a name="t210205114038"></a>t210205114038
	- <a name="t210114171154"></a>t210114171154 - p5** - port "quick tests" to actual tests

===========================================================================
- scala: <a name="scala"></a><a name="t210121165423"></a>t210121165423
	- <a name="t201213095810"></a>t201213095810 - p5 - any way to what's in Unit_ to Predef if possible? implicit class doesn't seem to work
	- <a name="t210115142355"></a>t210115142355 - p5 - investigate why += not appending for immutable.ListMap (see code)
	- <a name="t201123125604"></a>t201123125604 - p5 - why implicit not picked up (HeadZPair)
	- <a name="t210116154010"></a>t210116154010 - p5 - ideally would need to curry type args... or alternative?
	- <a name="t210116165405"></a>t210116165405 - p5 - which is faster, ADT vs boolean pair pattern match?
	- <a name="t210117104246"></a>t210117104246 - p5 - cannot use .tupled here?
	- <a name="t210117192437"></a>t210117192437 - p5 - is it possible to do the negation of <:<?
	- <a name="t210118134814"></a>t210118134814 - p5 - confirm runtime cost worth bothering?
	- <a name="t210124092916"></a>t210124092916 - p2 - is there any way to summon a Numeric instance at runtime from Any? [numbers]
	- <a name="t201005145138"></a>t201005145138	- p4 - is toString on a number always going to be compatible with most languages, eg R/python and so on (3e06 vs 3E06 and the likes for instance?)
	- <a name="t210125111338"></a>t210125111338 - investigate union types (coming in scala 3?)

===========================================================================
- aptus: <a name="aptus"></a><a name="t210121165939"></a>t210121165939
	- _remarks_:
		- meant to be really to-the-point, easy to call utility methods
		- if anything more powerful is needed then must drop to full-on java/scala/guava/commons way
		- it can also be seen as a starting point, for someone to see what is used under the hood and expand from it if needed; eg: val content: String = "/my/file.txt".readFileContent()
	- <a name="t210116165619"></a>t210116165619 - p5* - port the rest of aptus (much larger)
	- <a name="t210116165620"></a>t210116165620 - p5 - externalize aptus in its own stand alone utility library
	- <a name="t210116165559"></a>t210116165559 - p5 - rename ".as" to ".in"? [research]
	- <a name="t210123101634"></a>t210123101634 - p2 - [bug] - significantFigures vs maxDecimal
	- <a name="t210204095900"></a>t210204095900 - p4 - regexes could use a much more thorough treatment
	- <a name="t210125110827"></a>t210125110827 - aliases: consider AnyVal-based wrappers rather than mere aliases? overkill?

===========================================================================
- docs: <a name="docs"></a><a name="t210127114652"></a>t210127114652
	- <a name="t210127125443"></a>t210127125443 - bullet points version first
	- <a name="t210127125444"></a>t210127125444 - create minimal scala learning resource (to help at least understand _client_ code)?
	- <a name="t210127163237"></a>t210127163237 - describe assumptions (may in Obj.scala, eg a201104150252) and workarounds
		- null semantics: especially for overloaded null values (e.g. a middle name can legitimately be not applicable OR unknown)
		- 2+D arrays: generally forbidden as semantics are typically too unclear (outside of matrices/tensors)
	- style: <a name="t210124151646"></a>t210124151646
		- scala:
			- <a name="t210124151701"></a>t210124151701 - create basic scala coding style guide (look at existing code in the meantime) - relates to [t210121165229](#t210121165229) (automatic code formatting)
				- 210127125354 - vertical alignment: whatever can be done to lower cognitive burden
				- ...
			- <a name="t210127125056"></a>t210127125056 - describe/provide IDE templates, such as '---'/"===" banners, "formatDefault", "enum", "caseopt", ...
	- terminology: <a name="terminology"></a><a name="t210124100007"></a>t210124100007
			remarks:
			- sometimes making up a temporary term is better than leaving ambiguity and polysemy
			- keep symbolism to a minimum, when really more convenient
		- <a name="t210127123739"></a>t210127123739 - describe symbolism (+ rationale), e.g. "|>", "~>", stringx (ignore container), string_ (because `string?` is ugly), .typed\[String\]('foo), ...
		- <a name="t210127123841"></a>t210127123841 - describe abbrevations and acronyms, e.g. KVE (Key-Value Entry), NDT (NodeDataType), ASG (Afferent Sub Graph), ...
		- <a name="t210130091656"></a>t210130091656 - describe common (hosting language) reserved keyword workarounds: dis (this), thn/zen (then), wit (with)
		- <a name="t210130091657"></a>t210130091657 - describe gallia reserved keyword: _id, _group, _count, _tmp, ...; basically use them for unintended purposes at your own risk
		- <a name="t210127123840"></a>t210127123840 - disambiguations (for consistency within project at least); to tackle synonyms and polysemes in particular
			e.g. "distinct" vs "unique", "head" vs "first"
			DSL may slightly differ, especially around reserved keywords for the hosting language
		- renamings: <a name="t210202165617"></a>t210202165617
			- <a name="t210121105809"></a>t210121105809 - p2 - rename HeadU/HeadZ to HeadO/HeadS			
			- <a name="t210205065320"></a>t210205065320 - p2 - rename to .grab to .access or .orphan? .squash to .combine?

===========================================================================
- research:	<a name="research"></a><a name="t210205114050"></a>t210205114050
	- <a name="t210202085958"></a>t210202085958 - p2 - create a special action for simplest transform 1 to 1 that ignores requiredness; like "morph" for "transmute" (arbitrarily)	
	- <a name="t210128160642"></a>t210128160642 - p4 - expect import gallia.local._ to unlock e.g. take/drop; pertains to @Distributivity (<a name="t210123183101"></a>t210123183101); contrats with import gallia.spark._
	- <a name="t201108093951"></a>t201108093951 - p3 - should z.writeJsons return unit or a z (may need to reread input) - has a big impact on [spark] (see checkpointing: <a name="t210121160956"></a>t210121160956)
	- <a name="t210127193847"></a>t210127193847 - p1 - make multiple keys selection (sequentially, for each) rely almost exclusively on forX mechanisms (except for most basic operations)? eg:
			aobj(cls('f.string_, 'g.string_, 'h.boolean))(obj('h -> true))                         .setDefaultFor('f, 'g).asValue("-") .test(bobj('f -> "-", 'g -> "-", 'h -> true))
			aobj(cls('f.string_, 'g.string_, 'h.boolean))(obj('h -> true)).forEachKey('f, 'g).zen(_.setDefaultFor(_)     .asValue("-")).test(bobj('f -> "-", 'g -> "-", 'h -> true))
		possibly even container type, eg: data.forKey(_.string_('f)).zen(_.transform(_).using(...)) - may be too coarse though
	- <a name="t210202094041"></a>t210202094041 - p1 - semantic conflict for "commas": sometimes means EACH, sometimes means AND; maybe change one of them to always be myAction('f ~ 'g ~ 'h) instead of myAction('f, 'g, 'h)
	- <a name="t210128161346"></a>t210128161346 - p1 - pivot: dissociate top-level groupBy ("rows") from the rest of the pivoting (also see former "pivone" feature)
	- <a name="t210202164007"></a>t210202164007 - p3 - grouping: allow groupby with redundant keys in grouper/groupee?
	
	- dialects:
		- <a name="t210202113713"></a>t210202113713 - p3 - consider providing "wrappers" for very at least basic queries people are familiar with such as: gallia.dialects.sql.select('foo, 'bar).from("jdbc://.../table1").where('baz == 3); mostly to help "port" code initially
		- <a name="t210128152716"></a>t210128152716 - p3 - add "dialects" like R: gallia.dialects.R.unlist so people can see what it resolves to (+ to help migrations)
		
	- <a name="t210118133408"></a>t210118133408 - p2 - [hettype] - type heterogeneity handling
		- <a name="t210202115959"></a>t210202115959 - full-on support type heterogeneity [hettype]? big endeavor but may be worth the effort
		- <a name="t210202115958"></a>t210202115958 - p2 - type heterogeneity [hettype] workaround (relates to [t210104164038](#t210104164038) for json manip) - especially cases like:```
					[{"foo": 1}            , {"foo": "10+"}]            -->  [{"foo":"1"},            {"foo": "10+"}]
					[{"foo": {"bar": "hi"}}, {"foo": "sup"}]            -->  [{"foo": {"bar": "hi"}}, {"foo": {"bar": "sup"}}}]
					[{"foo": "bar"}        , {"foo": ["bar1", "bar2"]}] -->  [{"foo":["bar"]},        {"foo": ["bar1", "bar2"]}```
				or maybe just ability to rename fields like:```
					[{"foo": 1}, {"foo": "10+"}] --> [{"foo_int":1, "foo_string": null}, {"foo_int": null, "foo_string": "10+"}]```

	- terminology: <a name="t210124100008"></a>t210124100008
		- <a name="t210124100008"></a>t210124100008 - p2 - change read()/stream() to readOne()/read()?
		- <a name="t210127124029"></a>t210127124029 - p4 - create OWL ontology?
		- <a name="t210124100009"></a>t210124100009 - better names for: {A,B}Obj, CanForceAs{1,2}, potch, untuplify{1,2}{z,a,b}, asArray{1,2}, Whatever, "pairs", NonTable, Ttq{K,R}Path{z,}, reverseCartesianProduct
		- <a name="t210202100936"></a>t210202100936 - p3 - field creators .date and .dateTime conflict with aptus' ... as date1/dateTime1?			
		- <a name="t210202101142"></a>t210202101142 - p2 - keep "accessor" term (eg HeadZAccessors)?
		- target selection:
  			- <a name="t210201151634"></a>t210201151634 - p2 - (target) replace "Query" with "Selection" throughout? 
  			- <a name="t210202090211"></a>t210202090211 - p2 - homogenize across "target" and "selection" packages			
  			- <a name="t210202090526"></a>t210202090526 - p2 - rename and homogenize the likes of "Duo", "HT", "HasType"

===========================================================================
- more: <a name="more"></a><a name="t210124100537"></a>t210124100537
	
	- integration: <a name="integration"></a><a name="t210124100540"></a>t210124100540 - investigate dependencies first and foremost
		- indirection:
			- graph: see [t210116120349](#t210116120349) (for plan DAG)
			- RDBMS: see [t210114145431](#t210114145431)
			- json: see [t210204095517](#t210204095517)
			- spark: see [t210204095516](#t210204095516) for Spark 3.x			
		- <a name="t210204095519"></a>t210204095519 - stats/linear algebra/scientific computing, math in general
			- look into these: breeze, saddle, spire
		- <a name="t210204095520"></a>t210204095520 - low priority - visualization: look into vegas?

	---------------------------------------------------------------------------
	- scripting: <a name="scripting"></a><a name="t210124100126"></a>t210124100126
		- make it easy to use gallia from script (eg bash); for improved performance, could look into nailgun or custom socket-based alternative?

	---------------------------------------------------------------------------
	- scientific computing: computational science:
		- _remarks_:
			- <a name="rk210127135755"></a>rk210127135755 - while not the primary goal, would be great to provide more					

		---------------------------------------------------------------------------
		- external tools: <a name="t210124092211"></a>t210124092211
			- _remarks_:
				- pertains to the ability to wrap/call external tools (with performance hit), especially R/python/js/...; see POCs; for python, look at jep
				- great to showcase what features are useful and could benefit from being replicated in gallia
			- visualization: plotting: <a name="t210124092257"></a>t210124092257
			- scientific computing: <a name="t210124092258"></a>t210124092258

	---------------------------------------------------------------------------
	- notebooks: <a name="t210124092512"></a>t210124092512
		- investigate integration with jupyter/google colab/...

	---------------------------------------------------------------------------
	- semantics: <a name="t210124100546"></a>t210124100546
		- <a name="t210124095616"></a>t210124095616: may be tricky with transformations, eg if you fuse first and last name into name, how are the two "merged" as full name somehow? (eg with https://schema.org/givenName and https://schema.org/familyName)

	---------------------------------------------------------------------------
	- graph querying: <a name="t210124095504"></a>t210124095504
		- see PoC (very bare)
		
	---------------------------------------------------------------------------
	- slicing & dicing: <a name="t210124100531"></a>t210124100531 - (relates to [rereading]/[checkpoint] (see [t210121160956](#t210121160956))/[snapshot]/[persist]/[cache]/[demux]/[splice]/[partition])
		- see PoC

===========================================================================
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
