# Semantics

## Obstacles
Difficult because of Gallia's focus on transformations. For instance, if we "fuse" a https://schema.org/givenName field with a https://schema.org/familyName field via concatenation with say comma, the resulting field will then be neither, 
and obviously Gallia won't automatically know the result is a "full name" (https://schema.org/name ?). 

Potential solution: We could still offer each `Fld` to be annotated, and offer `Cls`-level operations to set/reset semantics accoringly at the end of data transformations. Many fields will likely maintain their semantics anyway. TBD.

See [task](https://github.com/galliaproject/gallia-docs/blob/master/tasks.md#t210124100546)

