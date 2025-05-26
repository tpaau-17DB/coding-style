<h1 align="center">
Coding Style: Rust
</h1>

Rust is rather strict about coding style, although it still allows developers
to customize how their code looks.


## Prefer Explicit Returns
Use explicit returns. Implicit returns make the code **unreadable**. They are
only fine when we are returning a value in constructors or in single-line match
arms, like so: 
```rust
match flag {
    true => String::from("true"),
    false => String::from("false"),
}
```

## Whitespace
Too much whitespace is better than too little, in my opinion. Code with too
little whitespace is hard to read. Use up to two newlines to separate code
blocks. Don't stack `if/else` blocks on each other with little newlines like
many LLMs do:
```rust
// This is insane
if some_condition {
    some_function();
} else {
    other_function();
}
```

I tend to add a newline character for every curly bracket, but Rust is a
*special* language. It looks cleaner to keep the opening curly bracket on the
same line:
```rust
if some_condition {
    some_function();
}
else {
    other_function();
}
```
Isn't this better?

For reference, here is an example of what I usually do in C-likes:
```c++
if (str == "asdfasdf")
{
    return true;
}
else
{
    return false;
}
```


## Imports
Don't use wildcards and don't rename imported libraries unless absolutely necessary:
```rust
// Bad:
use module::*;

// Good:
use module::{Element, function};
```


## Indentation
Use one tab.


## Line Length
No more than 80 characters. This is more of a guideline than a strict rule, it's OK to exceed the 80 character limit if necessary, for example in an inseparable string.
