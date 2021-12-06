# JSON flaws

WIP

- Was probably never meant to become the standard it has become
- Has no official notions of schema: JSON Schemas are an afterthought and unaffiliated(?)
- Ambiguity over the semantics of: `{"foo": "hello", "bar": null}` vs `{"foo": "hello", "bar": []}` vs `{"foo": "hello"}`; this means people choose one arbitrarily and sometimes imparts alternative semantics to each (and often do not document that)
- JSON array are painful to process when big, which is why "JSON Lines" (https://jsonlines.org/) prospered
- JSON aims to be part human friendly, part machine friendly; it is less human friendly than YAML or HOCON, and much less machine friendly than say alternatives like Avro, protobuf, etc; This isn't a problem in and of itself, only insofar as people use it for just about everything irrespective of who/what will consume it (human or machine)
- Data types:
  - It's dearly missing the Integer type (possibly my biggest pet peeve with it)
  - It's missing a "flag" type, which could be achieved with an optional "Unit" value; people resort to using a boolean which is wasteful if only one boolean value is ever used; flags are especially useful when extremely rare.
  - Some may argue a character type would have been useful too
- Keys:
  - Duplicate keys being allowed: `echo '{"foo":"hello", "foo":3}' | jq -c # returns {"foo":3}`
  - Key-quoting is mandatory, which seems wasteful most of the time
  - Keys are limited to strings, although this can be argued to be a good thing
- other misc oddness:
  - see the likes of [this SO comment](https://stackoverflow.com/questions/1580647/json-why-are-forward-slashes-escaped#comment14144177_1580682)
  - TODO: find more of the sort

