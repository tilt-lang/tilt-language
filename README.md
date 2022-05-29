# Tilt

*It's like Tcl, but more comfortable.*


Tilt syntax is based on [Til](https://til-lang.github.io/til/), but
instead of implementing *everything* from the ground up, it relies on
**Tcl** to execute most of the hard work.


As in Til, a program is a set of Pipelines, each containing one or more
CommandCalls, that in turn are command names followed by "things" that
eventually evaluate to
[Tcl_Obj](https://www.tcl.tk/man/tcl8.6/TclLib/Object.html).


Commands can be executed directly by Tilt, but if the implementation is
not found "internally", such command call is simply passed to a Tcl
interpreter.

## It is not an alternative Tcl implementation

Running unaltered Tcl scripts is **not** the goal of Tilt. Tilt is its own
language, syntax-wise.

What we try to achieve here is a form of DRY: Tcl is a great language with
amazing features and tons of work already by thousands of contributors
worldwide, not only in the standard library, but also in thousands of
packages already written. The language is also easy to embed -- by design,
so let's make use of this great asset!

## But isn't Tcl enough?

Maybe. But there's a lot of *discomfort*, still. For instance:

```tcl
set x [llength [lindex $argv 1]]
```

is hard on the eyes, let's be honest. But:

```tcl
length <$argv 1> | as x
```

is already better -- at least in my opinion. That's why I'm writing *yet
another language*.

(I also abhor seeing `::` *anywhere*, and specially when it's
*everywhere*.)
