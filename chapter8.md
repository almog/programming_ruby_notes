# More about methods

* It's convention to start a ethod name with an Upper case letter if it's used for type conversion (e.g. `integer`).
* Parentheses around a method parametrs are optional.
* It's possible to use parametrs value in default values

## Variable-Length Argument Lists
 * It is a convention to use splat as to mark the parameters not in use by a method (by such that might be used by the corresponding superclass's method)
 * Calling `super` without paretheses and without params passes all the parameters that were given to the original method.
 * It is possible to splat the unused params without a parametr to reference them.
 * It is possible to specify extra params after the splat.
 * No default values are allowed for regular parameters that are preceded by a splat.

## Calling a method
  * When the message receiver is omitted, it's default to self.
  * Private methods cannot be called with a message receiver.
  * Some people refer to paretheses-less method calls as "commands"
  * You _can_ use multiple splate when expanding arrays in a method call.

### Making blocks more dynamic
  * ampersand before the last parameter to a function, tells ruby that it is a proce, and ruby in turn, converts it to the associated method's block. what happens if we passed a block as well?

## Keyword Argument Lists
  * When a function contains keyword arguments, An ArgumentError is raised if unmatched keys are passed.
  * It's possible to collect extra hash arguments that are not part of the keyword arguments using a double-splat
