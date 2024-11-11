# JSON flaws

This document presents flaws with the JSON format, which are problematic given how ubiquitous the notation is.

Also see [_Gallia data modeling.md_](modeling.md)

- <a name="220104142500"></a>Was probably never meant to become the standard it has become
- <a name="220104142501"></a>Has no official notions of schema: JSON Schemas are an afterthought and unaffiliated(?)
- <a name="220104142502"></a>Ambiguity over the semantics of: `{"foo": "hello", "bar": null}` vs `{"foo": "hello", "bar": []}` vs `{"foo": "hello"}`; this means people choose one arbitrarily and sometimes imparts alternative semantics to each (and often do not comment on that fact); empty strings and zero values are also possibly problematic from that angle (TBD).
- <a name="220104142503"></a>JSON arrays at the top-level are painful to process when big, which is probably why "JSON Lines" (https://jsonlines.org/) prospered. I recommend avoiding them as much as possible.
- <a name="220104142504"></a>JSON aims to be part human friendly, part machine friendly; it is less human friendly than YAML or HOCON, and much less machine friendly than say alternatives like Avro, protobuf, etc; This isn't a problem in and of itself, only insofar as people use it for just about everything irrespective of who/what will consume it (human or machine)
- <a name="220104142505"></a>Data types:
  - <a name="220104142510"></a>It's dearly missing the Integer type (possibly my biggest pet peeve with it) - I refer to this as the "JSON number tax"
  - <a name="220104142511"></a>It's missing a "flag" type, which could be achieved with an optional "Unit" value; people resort to using a boolean which is wasteful if only one boolean value is ever used; flags are especially useful when extremely rare.
  - <a name="220104142512"></a>Some could argue a character type would have been useful too
- <a name="220104142506"></a>Keys:
  - <a name="220104142520"></a>Duplicate keys being allowed: `echo '{"foo":"hello", "foo":3}' | jq -c # returns {"foo":3}`
  - <a name="220104142521"></a>Key-quoting is mandatory, which seems wasteful most of the time
  - <a name="220104142522"></a>Keys are limited to strings, although this can be argued to be a good thing
  - <a name="220104142523"></a>Keys order is not guaranteed to be preserved
- <a name="241111153028"></a>File extensions:
  - Other than `.json`, and to an extent `.jsonl`, there is no common convention for what a file may actually contain: a single object? in compact form? pretty-printed? Multiple objects one-per-line? multiple objects in a JSON 'array', multiple objects pretty printed? It would certainly be useful to know that just from the filename. In my libraries (`Gallia` and `Aptus`), I assume: `.json` or `.jsono` for single object, `.jsonl` or `.jsons` for one-per-line, and `.jsona` for array
- <a name="220104142507"></a>other misc oddness:
  - <a name=""></a>see the likes of [this SO comment](https://stackoverflow.com/questions/1580647/json-why-are-forward-slashes-escaped#comment14144177_1580682)
  - <a name=""></a>TODO: find more of the sort

<a name="221014131702"></a>
Note that I am writing the specification for a JSON-like format that would address some of these concerns.
I will post it soon for feedback (bearing [this](https://xkcd.com/927/) in mind)
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
