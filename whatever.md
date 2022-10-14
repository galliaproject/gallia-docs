# "Whatever" construct

WIP

Meant to allow by-passing type indication in some (common) cases, for instance:

```.transform("age").using(_ + 1)```

Instead of:

```.transform(_.int("age")).using(_ + 1)```

## Technical notes

### Issue with operations order
<a name="220318114510"></a>

We do not support `Byte`, `Short` and `Float` in `Whatever` due to the fact that classes like `Int.scala` or `Double.scala` list overloaded operations in this order: `Byte < Short < Char < Int < Long < Float < Double`.
For instance `def *(x: Byte): Int` comes before `def *(x: Short): Int` and so on. As a result some of the implicit conversions incorrectly choose to transform `Whatever` into `Byte` where `Int` should be chosen (and the value may not fit a `Byte`).
