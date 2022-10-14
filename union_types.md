# Union Types

Support is very limited at the moment, and mostly consist of:
1. ability to specify union in schema, e.g. `cls("f".requiredUnion(string, int))`
2. ability to transform such a field, eg with `.increment("f")` - will be a no-op on string

Note that the above also stands for union involving nested entities, with the caveat that if there can be more than one nested entity, a hint must be provided (the simplest and recommended way being to provide a required field name unique to each nested schema - see "withFieldHint").

The best place to understand usage is the `galliatest.suites.sandbox.UnionTypeTest` (in gallia-testing)

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
