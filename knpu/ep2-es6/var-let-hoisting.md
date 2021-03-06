# var Versus let: Hoisting!

There's one other reason to use `let` instead of `var`. Top understand it, we need
to get really nerdy and talk about something with a cool name: variable hoisting!

At the top of the play file, do something terrible: `console.log(bar)`. I know!
This doesn't even make sense - there is no variable `bar`! When we try it, we get:

> ReferenceError: "bar is not defined."

Ok, no surprise, this is a legitimate *error*. If we try to log `aGreatNumber`, the
same thing happens! The variable has not been initialized yet.

Ready for things to get weird? Change the `let` to `var`. And all of a sudden, it
does *not* break. It simply says that that value is `undefined`.

## Hello Mr Variable Hoisting

The reason for this is something called variable hoisting, a term you'll see a lot
around JavaScript... I think mostly because it has a cool name. It's not that important,
but I want to tell you a little bit about it and so you don't have to worry about
it ever again.

In PHP, we never need to initialize a variable with a special keyword. We don't say
`var $aGreatNumber = 10`, we just say `aGreatNumber = 10` and we're good to go. But
in many other languages, including JavaScript, you must *initialize* a variable first
with a keyword.

When you use `var` to initialize a variable, when JavaScript executes, it basically
finds all of your `var` variables, goes to the top of that variable's scope - usually
the top of whatever function we're inside of, but in this case, it's the top of the
file - and effectively does this: `var aGreatNumber`. That initializes the variable,
but doesn't set it to any value. This is called variable hoisting: and it's the reason
that we get *undefined* instead of an error when we try to use a variable declared
with `var`... before it's actually declared.

But when we change this to `let`, we know that this *does* throw a `ReferenceError`.
And that's kinda great! I mean, isn't that what we would expect to happen when we
reference a variable that hasn't been created yet!

So with `var`, variables are *hoisted* to the top. But with `let`, that doesn't
happen, and that's kinda cool. Well, technically, `let` also has variable hoisting,
but thanks to something called the "temporal dead zone" - also an awesome name -
`let` acts normal: as if its variables are *not* hoisted.

Since `let` seems to behave more predictably, let's go into `RepLogApp` and change
all of these "vars" to `let`. Find all "var space" and replace with "let space".
And kust to make sure that our code doesn't have any edge cases where `var` and `let`
behave differently, try out our app! Yea! Everything looks like it's working just
fine.

Now, what about the new `const` keyword?