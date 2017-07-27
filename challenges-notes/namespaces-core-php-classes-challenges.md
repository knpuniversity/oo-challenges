### CHALLENGE 1

// note: update the SolidPlanet class to have this logic:

```class SolidPlanet
    public function __construct($radius, $hexColor, $dayLengthInHours = 24)
    {
        $this->radius = $radius;
        $this->hexColor = $hexColor;
        $this->dayLengthInHours = $dayLengthInHours;
    }
```

Then, include this code in `index.php` to remind/show people
how you work with PHP's DateTime object.

```
$planet = new SolidPlanet(100, 'ff00ff', 12);

// ...
// just an example of how to use the DateTime object
// $tomorrow = new DateTime();
// $tomorrow->modify('+24 hours');
?>

<h3>
    1 day from now:
    <?php echo $tomorrow->format('Y-m-d H:i:s'); ?>
</h3>
```

Question:

The length of a day on Earth is 24 hours, but other planets have
*drastically* different day lengths! No problem! We've already
added a new property to `SolidPlanet` - `dayLengthInHours` - to
help control this.

Now, we want to be able to print *when* one day from now will
be for a specific planet.

Steps

1) Add a new method to `SolidPlanet` called `getDateTimeOneDayFromNow`.

2) Inside, create a new `DateTime` object and add X hours to it,
where X is the value of the `dayLengthInHours` property. You can
use the commented-out `DateTime` code in `index.php` as a guide!

3) In `index.php`, call the new `getDateTimeOneDayFromNow()` method
and set it to a variable called `$tomorrow` so that it will be
rendered in the `h3` tag.

### CHALLENGE 2

Question:

Which of the following pieces of code would **not** work:

A)

```php
namespace Foo;

new \DateTime();
```

B)

```php
// not in a namespaced file

new DateTime();
```

C)

```php
namespace Foo;

new DateTime();
```

C)

```php
namespace Foo;
use DateTime;

new DateTime();
```

D) These would all work!

Correct: (C)

The best code is probably (A): `new \DateTime()`. This
wil *always* work, whether you're in a file with a namespace
or not.

If you simply say `new DateTime()`, this only *might* work.
If you're in a file whose namespace is `Foo`, then PHP thinks
you're referring to a class called `Foo\DateTime` (wrong!).
That's why adding the `\` in front is always best.

The final answer - with the `use DateTime` - looks a little
funky, but is also technically valid. A `use` statement always
anchors from the *root* of the namespace. In other words, even
though we type `use DateTime`, it means `use \DateTime`. So yes,
you actually *can* use `use` statements with core PHP classes.
