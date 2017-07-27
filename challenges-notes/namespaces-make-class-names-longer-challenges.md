### CHALLENGE 1

Question:

Since we *love* long class names, so we're going to start giving
our classes namespaces?

(But seriously, I'll show you why namespaces are *actually* awesome
soon).

Steps:

1) Give `RandomlyColoredPlanet` a namespace of `Model\Planet`.

2) **Without using a `use` statement**, update `index.php` so
that everything still works.

### CHALLENGE 2

Question:

Even though we don't *need* to use `use` statements, we almost
always do.

1) Update `index.php` to use a `use` statement for the
`RandomlyColoredPlanet` class.

### CHALLENGE 3

> note: give the PlanetRenderer class a namespace of `Service`.
> But, forget to add the `use` statement to `index.php`.

Question:

Since you're feeling pretty comfortable with namespaces, you
decide to delegate the rest of the work to the intern. Nice
management move!

But, when you get the code back, things aren't *quite* right.

1) Load the page to see the error

2) Find the problem and fix it!

### Challenge 4

Question:

Look at the following class:

```php
namespace Model\Planet.

class RandomlyColoredPlanet
{
    // ...
}
```

Which of the following is *not* a valid way to reference
this class from inside `index.php`:

A)

```php
new Model\Planet\RandomlyColoredPlanet();
```

B)

```php
use Model\Planet;

new RandomlyColoredPlanet();
```

C)

```php
use Model\Planet;

new Planet\RandomlyColoredPlanet();
```

D) All of these are correct!

Answer: (B)

Explanation:

Trick question! Well, sort of :).

One of the most common errors with `use` statements is
to forget that you need to include the namespace *and* the
class name:

```php
use Model\Planet; // wrong
use Model\Planet\RandomlyColoredPlanet; // correct!

new RandomlyColoredPlanet();
```

This is because PHP sees `RandomlyColoredPlanet` and looks
for a `use` statement that *ends* with this string.

If you *do* forget the last part of the `use` statement
(e.g. `use Model\Planet`), you can technically get your
code to work by saying `new Planet\RandomlyColoredPlanet()`.
This is pretty rare to see in the wild.
