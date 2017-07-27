### CHALLENGE 1

These `require` statements are *really* starting to cramp
my style! Start simple:

Steps:

1) Remove the `require` statement for `RandomlySizedPlanet.php`.

2) Add an autoloader function (spl_autoload_register) at the
top of `index.php`.

3) Inside that function, if the class equals `RandomlySizedPlanet`,
require that file.

4) Refresh to see everything working *without* the `require` statement!

### CHALLENGE 2

Question:

Ultimately - whether via a manual `require` statement written
by you or via an autoloader function - *something* needs to
require/include a file before we can use the class that lives
inside of it.

But, which option will give you better performance?

A) Autoloaders are *always* faster than manually having many
require statements.

B) Autoloaders are *usually* faster than having require
statements, because you don't need to include files that
you don't use.

C) Manual require statements are *always* faster than autoloaders.
Yes, they're annoying to write, but there is a lot of extra
overhead for calling the autoload function over and over again.

D) Manual require statements are *always* faster than an
autoloader function. By requiring all of the files in the
very beginning, your application can quickly reference any
class or function it needs.

Answer: (B)

Explanation:

Not only are autoloaders going to make your life simpler, they're
*faster* than manually writing require statements. Well, most of
the time :).

The big reason is that - with an autoload function - you only
include a file *if* you actually need it during a request. If
you never reference a class, then you never include its file
and never incur the added overhead of loading this class into
memory. Yay!

But to make this a reality, the *logic* inside of your autoloaders
needs to be fast! If your logic searches various files to look
for a class each time the autoloader is called, that will be *way*
slow!

That's why the autoloader we built in teh tutorial takes advantage
of a class's namespace to quickly locate it!
