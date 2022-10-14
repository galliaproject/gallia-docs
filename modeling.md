# Data Modeling in Gallia

This documents present the data model expected for manipulation with Gallia.
WIP

Relates to [_json.md_](json.md)

## Guidelines
- <a name="a210113121804"></a> No empty objects (use Option if may be missing)
- <a name="a201104150254"></a> No empty arrays (see next point)
- <a name="a211212171620"></a> Only one way to express null/missing; consider forbidding even empty string [res]?
- <a name="a211212171834"></a> No 2D (or more) arrays, use dedicated tensor objects if needed
- <a name="a220302154326"></a> Types:
  - TODO: add types (See BasicType.scala)
  - <a name="a210513114314"></a> Flags: use optional boolean + one value for now
  - <a name="a220302154350"></a> Binary data: use `_Binary` (introduced in `0.4.0`)
- <a name="a220104142115"></a> Keys:
  - <a name="a201026170344"></a> Keys for a given object level must be distinct
  - <a name="a220104142116"></a> Keep keys simple: alphanumerical + underscore
  - <a name="a220104142117"></a> Keys to convey semantics as much as possible (relates to [semantics task](./semantics.md)
  - <a name="a220104142114"></a> No "maps", favor including key in an object, so schemas can be defined against data; basically keys should not be arbitrary
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
