### CHALLENGE 1

(this can only be done when we have the terminal ability)

Question:

Ok! Let's use Composer's autoloader instead of our, home-grown
code. Yay to less code!

1) Delete our `spl_autoload_register` function
2) Give `composer.json` the proper `autoload` section so
that it knows to find our classes in the `src/` directory
3) Run `composer install` so that it generates the
`vendor/autoload.php` file
4) Require `vendor/autoload.php` from `index.php` and make
sure everything still works!

### CHALLENGE 2

(this can only be done when we have the terminal ability)

// note: Create a new file - called LegacyHelper.php inside
// some "includes" directory, and give it a class: LegacyHelper
// and a static function createPlanetMarkup($radius, $hexColor)
// move the markup-creation from PlanetRenderer into that
// method and call that method from PlanetRenderer.

Question:

Oh no, we have a problem! Pretend that we're updating an old,
ugly, legacy application. This code contains a class called
`LegacyHelper`, but it doesn't have a namespace and doesn't
live in the `src/` directory. This means that the Composer
autoloader can't find it! And since we're trying to use it
from inside `PlanetRenderer`, our code is broke!

This *should* be easy to fix (just move the file and give the
class a namespace), but we *can't* modify the class: it's still
being used by an old legacy application that we can't touch.
Dang!

No problem - the Composer autoloader can still help us!

Steps:

1) If you have some classes that do *not* follow the nice
PSR-0 naming standard, Composer *can* still autoload these.
Google for "Composer classmap" to find out how.

2) Add the new `classmap` key in `composer.json` to
autoload all classes in the `include` directory.

3) Run `composer install` again to update the autoloader.

4) Refresh to see that we're using the new autoloading code!



