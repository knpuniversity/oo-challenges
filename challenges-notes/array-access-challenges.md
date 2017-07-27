## Challenge 1

// note Create the following class:

class Meteoroid
{
    private $elements = [];

    private $name;

    public function __construct($name)
    {
        $this->name = $name;
    }

    public function addElement($name, $mass)
    {
        $this->elements[$name] = $mass;
    }

    public function getName()
    {
        return $this->name;
    }
}

// then in metor.php (leave index.php alone, we'll re-use
// our cool planets thing from earlier next), do this:

$meteoroid = new Meteoroid('Hoba');
$meteoroid->addElement('Iron', 45712);
$meteoroid->addElement('Nickel', 8707);
$meteoroid->addElement('Cobalt', 55);

<table>
    <thead>
        <tr>
            <th>Iron</th>
            <th>Nickel</th>
            <th>Cobalt</th>
        </tr>
    </thead>
    <tr>
        <td><!-- print iron --></td>
        <td><!-- print nickel --></td>
        <td><!-- print cobalt --></td>
    </tr>
</table>

Question:

Our app *also* deals with meteoroids: those cute
little flying rocks that occasionally threaten
life itself on Earth. Yay!

Since a meteoroid is just a chunk of different metals,
we've given it an `elements` property to hold whatever
metals it has. Let's print these... by treating this
class like an array!

Steps:

1) Implement the `ArrayAccess` interface and add the
4 methods you need to your class (sorry, PhpStorm can't
help you this one time!)

2) Fill in the logic for each method so that we can
access the `$elements` property like an array.

3) In `index.php`, print the `Iron`, `Nickel` and `Cobalt`
masses in the correct table boxes.

## CHALLENGE 2

Question:

Challenge! Check out the following code:

```php
// some code that you can't see!

echo $planet['radius']; // prints 50

echo $planet['atmosphere']->getMainElement(); // prints Nitrogen

echo $blackhole; // prints an empty string

$solarSystem[] = $planet;
```

Which of the following is **not** true:

A) `$planet` could be an array *or* an object
B) `$solarSystem` is definitely an array
C) `$blackHole` could be a string or an object
D) `$planet['atmosphere']` is definitely an object

Answer: B

Things are never as simple as they seem!

A) `$planet` is used like an array, but we know that this
could be because it's an array *or* an object that
implements `ArrayAccess`.

B) `$solarSystem` is *also* used like an array with the
`$solarSystem[] = $planet;` syntax. So this might *also*
be an object!

C) If `$blackHole` is an object that has a `__toString()`
method, then we could of course print this.

D) Because of the code `$planet['atmosphere']->getMainElement();`,
we know that `$planet['atmosphere']` must be an object. You
can *only* call a method on an object.
