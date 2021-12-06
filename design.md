# Design

This is very early WIP

- mostly focusing on client interface/experience, the internals being more bare and subject to complete overhaul in the future except for a few concepts such as:
  - action+atom plan abstractions (to allow for future optimization)
  - TODO
- takes on boilerplate as much as possible, to free client from it
- opinionated where needs to be
- favor "fluency" over conciseness, eg: `.rename("foo").to("FOO")` rather than `%"foo"^"FOO"`
- not idiot-proof (nor evil-proof)
- TODO
