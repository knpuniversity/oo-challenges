## Challenge 1

Question:

// note: Add getName() and setName() to both Planet classes,
// and make sure there's any weird __set() stuff gone.

Check out `GasPlanet` and `SolidPlanet`: they have a bit
of duplication! Each has a `$name` property, a `getName()`
function and a `setName()` function.

I hate duplication!

1) Create a new trait: `NameableItemTrait`.

2) Move the `$name` property and the 2 duplicated methods
into this trait.

3) Use the trait from both planet classes and delete that
duplicated code!

## Challenge 2

In the previous challenge, we created a `NameableItemTrait`
and used it inside of `GasPlanet` and `SolidPlanet`.

But, there was another option: create a new `AbstractPlanet`
class, move the logic there, and then *extend* this class.

In this situation, what was a better option: using a `trait`
or extending a base `class`?

A) The trait is better because it would allow us to add
this trait to *other* future classes that have a name, but
aren't planets (e.g. the `Meteoroid` class).

B) The abstract class is better: these are both *planets*,
so it makes sense to give these the same base `AbstractPlanet`
class.

C) Both of these are correct!

Correct: (C)

Explanation:

Traits versus extending a class: the correct answer always depends
on your situation. If both classes are modeling the same type
of thing (e.g. a Planet), then extending a base class may make
sense. If not, definitely use a `trait`.

And if you want, you could do both! Use a trait inside of the
base class!

```php
abstract class AbstractPlanet implements PlanetInterface
{
    use NameableItemTrait;
}
```
