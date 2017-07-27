## class-constants

### CHALLENGE 1

> Note: update index.php to use the GasPlanet class. For example,
    create 2 gas planets with ammonia and methane and then
    use use the PlanetRenderer to print them.
    Also, at this point, the user does not know to use
    self::, so they will probably say GasPlanet::, even from
    inside that class. Allow either :).

Question:

Our cool `GasPlanet` class is smart! We tell it what
"main element" the planet is made out of (e.g. ammonia),
and `getHexColor()` tells us the color of the planet.

But, it's too easy to make a typo - e.g. `amonia` - when
passing in the element.

Steps:
1) Add 4 new constants to GasPlanet - one for each of
the 4 materials. Give them descriptive names, like
`MATERIAL_AMMONIA`.

2) Ok! Replace the strings in your code with these
constants.

### CHALLENGE 2

Question:

Why are constants always upper-case (e.g. `MATERIAL_AMMONIA`)?

A) It's just a standard: constants don't *need* to be upper-case

B) The upper-case characters distinguishes them from normal properties

C) Upper-case class constants are used so that they don't conflict
with core PHP constants

D) The upper-case characters help keep memory usage lower

Correct: A

Explanation:

The upper-casing of constants is just a standard, but standards
are good to following! A constant is distinguished from a property
by their keyword and the use of a `$`: `const PIZZA` versus `private $pizza`.

### CHALLENGE 3

Question:

Suppose you want to change the value of a constant.
Check out the following code:

```php
class GasPlanet
{
    const MATERIAL_AMMONIA = 'ammonia';
}
```

```php
<?php
// ...

GasPlanet::MATERIAL_AMMONIA = 'helium';
```

Is this legal?

A) Yes, but it's not recommended. Constants are values that
are not *meant* to be modified.

B) No, unless you removed the `const MATERIAL_AMMONIA = 'ammonia';`
from `GasPlanet`. Constants can only be set *once* either via
the `const` keyword, or by setting them from outside the class.

C) Nope - changing constants is totally *not* allowed, ever.

D) Yes, though it's recommended to change constants from inside
the class where they are declared (i.e. `GasPlanet`).

Correct: C

Explanation:

Constants can *never* be changed - that's the whole point! And
they *must* be declared inside of the class with the `const` keyword.

If you need a value that *changes*, then you don't need a constant,
you need a *property*. And as you'll learn in a few minutes, properties
can be static (like constants) or non-static (stay-tuned!).

### CHALLENGE 4

Question:

The intern has gone *crazy* with constants, by even making the
hex strings into constants:

```php
class GasPlanet implements PlanetInterface
{
    // ...

    const COLOR_BROWN_ISH = '663300';
    const COLOR_BLUE_BRIGHT = '0066FF';
    const COLOR_GRAY_DARK = '464646';
    // ...

    public function getHexColor()
    {
        // a "fake" map of elements to colors
        switch ($this->mainElement) {
            case GasPlanet::MATERIAL_AMMONIA:
                return GasPlanet::COLOR_BROWN_ISH;
            case GasPlanet::MATERIAL_METHANE:
                return GasPlanet::COLOR_BLUE_BRIGHT;
            default:
                return GasPlanet::COLOR_GRAY_DARK;
        }
    }
}
```

Is this a good step forward?

A) Not really. These hex colors aren't used outside of this
class ever (or even multiple times *inside* of this class),
so there's no advantage to making these constants.

B) Absolutely: it's important to make all static strings into
constants.

C) No: the hex colors shouldn't be constants, in case we need
to change them later.

Answer: (A)

Explanation:

Not *all* strings or numbers should be turned into constants.
If you're thinking about making something a constant, ask yourself:

A) Are these strings used multiple times?
B) Are these strings used from *outside* of the class?
C) If someone makes a minor typo, will the result be drastically different?
D) Is it important for us to have a list of all of these
possible values in one spot.

In this case, the answer is no to *all* of these questions. For
example, if we typo `ammonia` as `amonia`, the planet would have
a drastically different color. But if we typo `663300` as `663301`,
that won't make much difference, because the hex values are not
being used as *exact keys* to decide how the code behaves.
