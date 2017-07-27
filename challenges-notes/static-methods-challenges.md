### CHALLENGE 1:

Question:

The gas planets are kind of pretty, so we want to render
*all* of them for the user to enjoy. Simple! By creating
one `GasPlanet` object for each possible element, we've
done it!

But, you know the problem: if we add *more* elements to
`GasPlanet`, we'll need to remember to come here and create
another object. Lame!

Steps:

1) Create a new *static* method called `getAllElements()`
that returns the 4 possible gas planet elements.

2) Call this from `index.php` and use a `foreach` to
render the 4 different gas planets.

### CHALLENGE 2

> Note: we'll add a new class like this, and render
> it in index.php (notice the purposeful problem: getRandomColor()
> should *not* be static.

```
class RandomlyColoredPlanet implements PlanetInterface
{
    private $color1;
    private $color2;

    public function __construct($color1, $color1)
    {
        $this->color1 = $color1;
        $this->color2 = $color2;
    }

    public static function getRandomColor()
    {
        $colors = [$this->color1, $this->color2];

        $randomKey = array_rand($colors);

        return $colors[$randomKey];
    }

    public function getHexColor()
    {
        return self::getRandomColor();
    }

    public function getRadius()
    {
        return 100;
    }
}

You take *one* day for a holiday, and the intern experimented
in the code and broke things! Now that you're back, well-rested
and with a nice tan, see if you can get the code working again.

Steps:

1) Render the page to see what the error is
2) Find the bug and squash it!

Explanation:

When deciding between making a method static or non-static,
one easy question to ask is:

> Does this method need to use the `$this` variable?

If it *does*, then it should *not* be static. Simple!

> note: we haven't ever yet included explanations for coding
> challenges, but I don't see why we shouldn't when it makes
> sense.

### CHALLENGE 3

Question:

We're building a new class of planets that *always* have the
same radius. We're in a heated (geeky) debate over whether or
not to make a method static. Here are the two options:

```php
// OPTION 1
class StaticallySizedPlanet
{
    public function getRadius()
    {
        return 250;
    }
}
```

```php
// OPTION 2
class StaticallySizedPlanet
{
    public static function getRadius()
    {
        return 250;
    }
}
```

Which would you recommend?

A) OPTION 1 (non-static): The "radius" of a planet is a
property that should really belong to each, individual planet.

B) OPTION 1 (non-static): "getter" functions like this
(e.g. `getRadius()`, `getName()`, etc) should always be non-static.

C) OPTION 2 (static): The method does not rely on the
`$this` variable, so we should make it static.

D) OPTION 2 (static): The method always returns a static,
or constant value. This is precisely when you should use
a static method.

Answer: A

Explanation:

This one is tough :).

Deciding whether or not to make a method static has *nothing*
to do with whether or not that method will return a "static"
(or constant value). And just because you *don't* need the
`$this` keyword does *not* automatically mean that you should
make something static (though the opposite *is* true: if you
need `$this`, make it non-static).

Instead, you need to ask yourself:

> When I call this method, am I calling this method on one
> individual "planet" object or on the StaticallySizedPlanet
> class in general?

In those case, both sound pretty reasonable: so both static
and non-static are *good* answers. However, if you're ever
not sure - or both options make sense - choose non-static.
Put simply: this will give you more flexibility in the future.
