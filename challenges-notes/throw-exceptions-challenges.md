### CHALLENGE 1

// note: Update GasPlanet.php to *not* have
// the `default` part of the switch-case statement.
// We will now always
// require one of the 4 elements to be passed in.
// also, in index.php, create a new `$planet` variable
// that is a new GasPlanet object (using one of the valid
// elements). Render this like normal.

Question:

When you create a `GasPlanet`, you now *must* pass in one of
the 4 valid elements. If you don't, `getHexColor()` will fail
to return a color and weird things will happen!

Let's not let that weirdness happen

Steps:

1) In `GasPlanet::__construct()`, add an `if` statement to check
if the `$mainElement` argument is *not* one of the 4 valid values
(hint, you can use the getAllElements() methods to help)

2) If it is *not* valid, throw a new `Exception` object with
the message: `This is not a valid element!`.

3) In `index.php`, change the `$planet` variable to use am
invalid element - like `gold` (but wouldn't it be cool if
a planet were entirely gold!?).

4) Refresh to see the error!

### CHALLENGE 2

// note: Update PlanetRenderer::render() to throw a big
// Exception if the radius is 0 or less. Also update
// index.php to create 3 planet objects: 2 that have a valid
// radius, and one with a negative radius. Create a foreach
// over these and render them.
// btw, we could *not* use that Legacy class inside PlanetRenderer
// anymore (just move the <div> logic back here) - it might
// make things simpler

Question:

We've been having a problem with people creating planet objects
with a *negative* radius. At least as far as we humans understand
things like gravity and the space-time continuum, that's crazy!

To help, we've made the PlanetRenderer smarter: if a planet has
a negative radius, it will throw an exception. Currently, one
of our 3 planets is causing this exception to be thrown!

Instead of seeing this error, let's render a little error
message instead of the planet.

Steps:

1) In `index.php`, surround the line that may cause an exception
with a try-catch block

2) If rendering a planet causes an `Exception` to be thrown,
just print this message: `Planet cannot be rendered`.

### CHALLENGE 3

Question:

Is this code valid?

```php
throw new \DateTime();
```

A) No: you can only use `throw` with the `Exception` class
or one of its sub-classes

B) Yes: you can use *throw* with any object to stop execution
and show an error.

Answer: (A)

Explanation:

Plain and simple: the Exception class is special: it is the
*only* class that you can `throw`. Well, actually, you can
throw an `Exception` object or any class that extends it.
