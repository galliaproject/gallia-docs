# Data Modeling
WIP

Relates to [_json.md_](json.md)

## Guidelines
- only one way to express null/missing; consider forbidding even empty string [res]?
- no 2D (or more) arrays, use dedicated tensor objects if needed
- no maps (favor including key in object, so schemas can be defined against data); basically keys should always be enumerable
- flags: use optional boolean + 1 value for now
- keys:
  - keep keys simple: alphanumerical + underscore
  - keys to convey semantics if possible (relates to [semantics task](https://github.com/galliaproject/gallia-docs/blob/master/tasks.md#t210124100546))
