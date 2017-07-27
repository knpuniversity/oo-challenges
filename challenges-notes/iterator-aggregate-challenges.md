## Challenge 1

// note: create a SolarSystem class that has a `$planets`
// property. In index.php, pass all the 8 planets into this
// then, update the `foreach` to iterate over `$solarSystem`

class SolarSystem
{
    private $planets;

    public function __construct(array $planets)
    {
        $this->planets = $planets;
    }
}

Question:

Hey hey! Someone got fancy and created a new `SolarSystem`
class that holds all of the planets. Cool!

Just one problem: the page isn't working anymore! We're trying
to loop over the `$solarSystem` object, and that just isn't working.

Steps:

1) Add the IteratorAggregate interface to SolarSystem
2) Add the `getIterator()` method so that we can loop
over the `$planets` property.
3) Reload and enjoy the planets again!

## Challenge 2

// note: add this near the top of index.php

<h1>
    Showing <?php echo count($solarSystem); ?> Planets
</h1>

Since the number of planets apparently changes sometimes, we
want to print the current number of planets at the top of the
page.

We asked the intern to do it, but he couldn't figure it out.
Sure, we can *loop* over the `SolarSystem` object, but we can't
seem to count it (he tried in `index.php`).

Steps:

1) Add a new interface: Countable. This will allow
you to "count" an object.

2) Implement any method(s) that you need for this
interface (put on your Googling/Binging hat and research
the answer!)
