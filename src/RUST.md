<h1 align="center">
Coding Style: Rust
</h1>

Rust is rather strict about coding style, although it still allows developers
to use a coding style they like. To maintain a consistent style over the entire
codebase, I listed all of my coding preferences for Rust in here.


#### Returns
Use explicit returns. Implicit returns make the code **unreadable**. Implicit
returns are only fine when we are returning a value as we are wrapping it in a
`Result` enum.

For example this is fine:
```rust
fn check_condition(flag: bool) -> Result<(), &'static str> {
    match flag {
        true => Ok(()),
        false => Err("Bad, bad bad!"),
    }
}
```
In this case we don't need to use the `return` keyword since we are returning
a value as we are wrapping it in a `Result`.

And this is not fine:
```rust
fn another_function(a: i32, b: i32) {
    a + b
}
```
Here we **must** use the `return` keyword as we are not wrapping the result in
`Result`.

So here is the corrected version of the second example:
```rust
fn corrected_function(a: i32, b: i32) {
    return a + b
}
```


#### Whitespace
Too much whitespace is better than too little, in my opinion. Code with too
little whitespace is hard to read. Use up to two newlines to separate a
function or a class from one another. Don't stack `if/else` blocks on
each other with little or no newlines like many LLMs do:
```rust
// This is insane
if some_condition {
    some_function();
} else {
    other_function();
}
```

I tend to add a newline character for every curly bracket like it's often done
in C-likes, but Rust is a *special* language. It looks cleaner to keep just the
opening curly bracket on the same line:
```rust
if some_condition {
    some_function();
}
else {
    other_function();
}
```
Isn't this better?


#### Imports
Don't use wildcards in imports unless you have something to hide:
```rust
// This is bad:
use module::*;

// This is the correct way:
use module::{element, function};
```


#### Indentation
Use one tab as a single indentation level. Regular space characters are
unacceptable as they make indentation level impossible to customize like
with tabs.


#### Line Length
Lines should be no more than 80 characters in length. In some rare cases this
limit can be exceeded, like when pasting an url or other string that can't be
broken up into several smaller strings.
