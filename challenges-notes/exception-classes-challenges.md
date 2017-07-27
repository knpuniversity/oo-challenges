### Challenge 1

We've improved the PlanetRenderer to throw an exception if
a planet has no hex color. Rejoice!

```php
// ...

class PlanetRenderer
{
    public function render(PlanetInterface $planet)
    {
        if ($planet->getRadius() < 0) {
            throw new \Exception('Invalid radius!');
        }

        if (!$planet->getHexColor()) {
            throw new \Exception('Missing hex color');
        }
    }
}
```

Can you use a `try-catch` block to *only* catch the
"Invalid radius!" exception?

A) Yes! Just mark that you want to catch the `(first)`
exception only:

```php
try {
    echo $renderer->render($planet);
} catch (\Exception (first) $e) {
    // here!
}
```

B) No. Well, only by checking the exception message,
which is really ugly and error-prone;

```php
try {
    echo $renderer->render($planet);
} catch (\Exception $e) {
    if ($e->getMessage() == 'Invalid radius!') {
        // here!
    }
}
```

Answer: (B)

Explanation:

Answer (A) is just ridiculous - that's *not* real code :).

You can catch different exception *classes*, but if 2 situations
both throw the *same* exception class, then it's basically
*not* possible to catch one exception, but not the other
(besides checking the exception message... which you should
*not* do - someone will eventually update that exception message
and break your code).

This is why it's sometimes important to throw different exception
classes in different situations. Let's try that in the next challenge...

### Challenge 2

// note: Create 2 new exception classes:
// InvalidRadiusException & MissingHexException
// throw these from inside PlanetRenderer.
// add a 4th planet to index.php that has a blank hex color

Question:

Oh yea! We just made the `PlanetRenderer` even smarter! By
creating our *own* 2 exception classes (yep, this is legal!),
we are throwing a different exception when the radius is negative
versus when the hex color is missing.

1) Update `index.php` to *only* catch the `InvalidRadiusException`

2) Add a *second* `catch` after the first `catch` (yes, this is
possible!) that will catch the `MissingHexException`. If this
happens, print the message "Planet has no color".

3) Reload the page to see it all working!
