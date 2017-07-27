## static-vs-non-static-and-self

### Challenge 1

The intern is *loving* the idea of static properties, but I feel
like he's a little confused. But, he's got a good spirit! Let's
check out his code and offer him some advice:

```php
class SolidPlanet
{
    private $radius;

    private static $hexColor;

    private $hasBeenVisitedByAliens;

    private $numberOfHabitablePlanetsInUniverse;
}
```

Which of the following are true:

A) The `$hexColor` property should *not* be static
B) The `$radius` property should be static
C) The `$numberOfHabitablePlanetsInUniverse` should be static.
D) Both (A) and (C) are true!
E) Both (B) and (C) are true!

Answer: D

Explanation:

When determining static or non-static, ask yourself this question:

> Does *each* individual planet have its own value for this
> property? Or is there just one value for *all* planets?

Looking at each property, here's how it looks:

* `radius`: Each planet has a different radius: *not static*
* `hexColor`: Each planet also has its own color: *non static*
* `hasBeenVisitedByAliens`: Some planets may have been visited by aliens
  and others not: *non static*
* `$numberOfHabitablePlanetsInUniverse`: This is a global number,
  it applies to *all* planets: it's not a property of just one
  planet: *static*

When in doubt, use non-static!

### Challenge 2:

> Note: this is a continuation of the coding challenge in the
> previous chapter.

Question:

We're doing to much work by using the whole class name `GasPlanet`!

Steps:

1) Refactor `GasPlanet` to use `self` to reference the constants.
