# Pragmatic Heterogeneous Proofread 💻 😫

## So, what is this?

First thing first, this is not supposed to be just slander about PHP ~like I am used to do~ but a comprehensive list of errors that are atributed to PHP and proof (or lack thereof) of those errors across multiple versions of PHP.
Also those errors will be compared to a correct design on other langs showing how those problems could be improved or so.

## Why proofread?

So, this is called a proofread mainly because it is a revision of an old post I usually link that was made on eevee blog talking about how bas the design of PHP is. you can see the post [here.](https://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/ "Not for the faint of heart")

And as they say on the blog we will check on how PHP is ~not~ a **predictable, consistent, concise, reliable, debuggable** lang.

## List of stuff we will be visiting

+ Searching arrays return false and false is converted to 0 so it will work as if you had found the item on the first index
+ `"foo" == TRUE` and `"foo" == 0` but `"TRUE" !=0`
+ `123=="123foo"` but `"123" != "123foo"`...huh
+ `6 == " 6"` and `"4.2" == "4.20"` and `"133" == "0133"` but `133 != 0133` because 0133 is octal. `"0x10" == 16` and `"1e3" == "1000"`
+ === compares object ande type expect for objects where === means that both are the same object and == compare value and type, which is what === does for other types.
+ `NULL < -1` and `NULL == 0`, so this can cause nondeterministic sorting
+ `"123" < "0124"` no matter what, even with casting
+ you can write `var[]` or `var{}` for indexing
+ if you use `[]` on a non-array it silently returns null
+ left associative `?:` that was later changed for non-associative by enforcing parenthesis on php8
+ no variable declaration, so if you need a global variable this could result into a local variable silently beign created, damaging the scoping of the lang.
+ function and class names are case insensitive while variables are.
+ `array()` or `list()` look like functions but are not functions, there are more stuff afected by this
+ the `(int)` casting looks like a casting from C but `int` does not actually exists, so this is a standalone token just to look like C, same goes for integer bool, boolean, float, double and real casting tokens.
+ `(array)` and `(object)` casting...huh, can someone explain?
+ `include()` just dumps the source from another file into your file, there is no real module system on PHP.
+ including a file adds alll of its variables into the current function scope and gives that file access to your variables too, but classes and functions are dumped into global scope. this is because there are not local functions or classes
+ appending to an array with `$foo[] = $bar`, i mean....lolz
+ `echo` is not a function, it is a _statement?_
+ `endif` but also brackets?
+ no stack tracer
+ HORRIBLE DEBBUGING EXPERIENCE [as expressed in this phpsadness post](http://phpsadness.com/sad/44)
+ ... I am done with the nonexisting error handling, there is more on the blog but it will all be tested
+ well, one more thing is that errors and exceptions are not the same so `try/catch` wont with errors and error handlers are not triggered by errors.



## The analogy


>    I can’t even say what’s wrong with PHP, because— okay. Imagine you have uh, a toolbox. A set of tools. Looks okay, standard stuff in there.
>
>    You pull out a screwdriver, and you see it’s one of those weird tri-headed things. Okay, well, that’s not very useful to you, but you guess it comes in handy sometimes.
>
>    You pull out the hammer, but to your dismay, it has the claw part on both sides. Still serviceable though, I mean, you can hit nails with the middle of the head holding it sideways.
>
>    You pull out the pliers, but they don’t have those serrated surfaces; it’s flat and smooth. That’s less useful, but it still turns bolts well enough, so whatever.
>
>    And on you go. Everything in the box is kind of weird and quirky, but maybe not enough to make it completely worthless. And there’s no clear problem with the set as a whole; it still has all the tools.
>
>    Now imagine you meet millions of carpenters using this toolbox who tell you “well hey what’s the problem with these tools? They’re all I’ve ever used and they work fine!” And the carpenters show you the houses they’ve built, where every room is a pentagon and the roof is upside-down. And you knock on the front door and it just collapses inwards and they all yell at you for breaking their door.
>
>    That’s what’s wrong with PHP.
- mel
