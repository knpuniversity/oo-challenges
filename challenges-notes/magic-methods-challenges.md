### Challenge 1

// note: Add a new getName() to PlanetInterface and
// update GasPlanet and SolidPlanet to have this method
// and a name property (we probably don't need to touch
// RandomColorPlanet, since we're not going to use it here
// Then, in index.php, let's create all 8 of the planets
// in our solar system and render them:

$planets = [
    new SolidPlanet('Mercury', 10, 'cccccc'),
    new SolidPlanet('Venus', 30, '29A1FF'),
    new SolidPlanet('Earth', 30, '0E1338'),
    new SolidPlanet('Mars', 15, 'DAA18A'),
    new GasPlanet('Jupiter', GasPlanet::ELEMENT_HYDROGEN, 139),
    new GasPlanet('Saturn', GasPlanet::ELEMENT_HYDROGEN, 120),
    new GasPlanet('Uranus', GasPlanet::ELEMENT_METHANE, 51),
];
$neptune = new GasPlanet('Neptune', GasPlanet::ELEMENT_HYDROGEN, 49);
$planets[] = $neptune;

// then, iterate over these and render them. But, before rendering
// each one, print the name (by printing the object - e.g.):

<h3><?php echo $planet; ?></h3>
<div>
    <?php echo $renderer->render($planet); ?>
</div>

Question:

Let's take our planet classes out for a real test drive: and
render the 8 (sorry Pluto) planets in our solar system!

Before doing this, we've given each class a `$name` property
so we can print it before rendering the planet. Everything
is *almost* working, but when we print the `$planet` variable,
it gives us an error!

1) Update both `GasPlanet` and `SolidPlanet` so that
when you print them, it prints the planet's name.

2) Refresh and enjoy the solar system :p

## Challenge 2

// note: index.php will change slightly:

$neptune = new GasPlanet('Neptune', GasPlanet::ELEMENT_HYDROGEN, 49);
$neptune->name = 'Nep-Toon!'; // this is a silly name
$planets[] = $neptune;

Question:

The `GasPlanet` has a private `$name` property, but it does *not*
have a `setName()` method. This means that the `$name` property
cannot be modified, which normally, is probably ok!

But, let's challenge ourselves! In `index.php`, we've added some
code that tries to change Neptune's name by referencing the property
directly. That won't work! Yet... Let's make this possible!

1) Keep the `$name` property private, but add
a magic `__set()` method that makes the code
in `index.php` work!

2) Reload and make sure it works!

## Challenge 3

Question:

We already know that you can create a method that will
be called whenever an object is instantiated/constructed.
This is called `__construct()`.

And while it's much less common, you can *also* create a
method whenever an object is *destructed*  - it's called
`__destruct()`. This is usually called at the very end of
your script, but made be called earlier - once you're done
working with your object.

Steps:

1) Add a `__destruct()` method to `GasPlanet`. Inside, just
`echo $this->name`.

2) Refresh to see if this method is called!
