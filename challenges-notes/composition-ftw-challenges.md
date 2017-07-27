## Challenge 1

Question:

Remember our trusty `PlanetRenderer` class? For this challenge,
pretend that you *cannot* edit it: because this is a class
from an external library that you're using.

But here's the challenge: the existing `PlanetRenderer` returns
a `div` with the planet inside of it. But to allow for some
styling, *we* need to add a class to this div `rendered-planet`.
Unfortunately, it doesn't look like there's any easy way to
configure this.

Let's fix this by overriding the class!

Steps:

1) Create a new `CustomPlanetRenderer` and make it extend
`PlanetRenderer`.

2) Call the [parent](http://knpuniversity.com/screencast/oo-ep3/parent)
method, but then wrap the string in a new div - something like this:

```php
$html = parent::render($planet);

return sprintf('<div class="rendered-planet">%s</div>', $html);
```

3) Change `index.php` to instantiate *our* class instead of the
normal one.

## Challenge 2

// note: Create a new PlanetRendererInterface
// and also a SolarSystemRenderer, which looks like this:

class SolarSystemRenderer
{
    private $planetRenderer;

    public function __construct(PlanetRendererInterface $planetRenderer)
    {
        $this->planetRenderer = $planetRenderer;
    }

    public function renderSolarSystem(SolarSystem $solarSystem)
    {
        foreach ($solarSystem as $planet) {
            echo $this->planetRenderer->render($planet);
        }
    }
}

Extending the class worked *just* fine. But let's try composition!
*If* the class you want to replace implements an interface or extends
a base class, then you can implement/extend *that* instead and
*wrap* the object you want to fake.

This is much more difficult at first - but is a great skill to
understand and master.

Steps:

1) Instead of extending `PlanetRenderer`, make `CustomPlanetRenderer`
implement the new `PlanetRendererInterface`

2) Allow the other `PlanetRenderer` object to be passed into
the `__construct()` method of `CustomPlanetRenderer`. In other
words, add a `__construct()` method that has a single `PlanetRendererInterface`
object and set this on a new `planetRenderer` property.

3) Update `CustomPlanetRenderer` to call `render()` on the new
`planetRenderer` property and *then* add the new div like normal.

4) Update `index.php`: When you instantiate your
`CustomPlanetRenderer`, you will now need to instantiate and
pass the normal one to it.

### Challenge 3

Question:

In the previous challenge, we changed from overriding a class
to using composition. It was honestly a bit more work! What
are the advantages?

A) Composition makes your execute faster: because calling
parent methods can be slow
B) There aren't any real advantages: both are valid ways
to override functionality.
C) With composition, your new class - `CustomPlanetRenderer`
can be used to decorate/enhance *any* other classes that
implement `PlanetRendererInterface`.

Answer: (C)

Explanation:

Don't get too excited or worried about composition. In most
cases, the advantages are small, and are most enjoyed by
third-party library creators, who use composition to add
extra flexiblity to their libraries that we may never need
in our application!

Just get used to seeing the pattern and understanding what
it means.
