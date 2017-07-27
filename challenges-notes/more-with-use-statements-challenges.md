## CHALLENGE 1

// note: Move GasPlanet, PlanetInterface and PlanetRenderer
// (and anything else we use in this challenge that I'm not
// thinking of) into different directories.
// things like src/Model, src/Model/Ship and src/Service.
// But don't add namespaces or use statements anywhere
// In index.php, create an instance of each of
// GasPlanet and render it.
// also, add an spl_autoload_register() that looks like
// the one at the end of the `autoloading-awesomeness`
// chapter - the faked PSR-0-style autoloader :)

Question:

Time to remove *all* of the `require` statements! YES!

We made the intern work late last night, and he got us off
to a nice start: the classes now live in different directories
*and* our `spl_autoload_register` function is smart!

Steps:

1) Remove all of the require statements
2) Give each class a proper namespace so that the autoload
function can find them!
3) Fix anything else needed in the code after giving
the classes namespaces.

## CHALLENGE 2

// note: Put the GasPlanet in src/Model/Planet, but give
// it only the Model namespace (so, it's wrong). Render
// it in index.php

Question:

We *thought* we were done converting everything to have a
namespace, but now we're stuck on this error!

Steps:

1) Reload the page to see the error
2) Find the bug and squash it!

