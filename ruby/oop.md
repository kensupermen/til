- Problem with module
  - If `module A` and `module B` have 2 method with same name. When you include 2 method to a class, ruby will get module included lastest.
  - `module A` and `module B` included `module C` with `methodC`. Then `module D` included `module A` and `module B`. What happend when you call `methodC`. Ruby will get module included lastest.