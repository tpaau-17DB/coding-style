<h1 align="center">
Coding Style: Rust
</h1>

Rust is rather strict about coding style, although it still allows developers
to customize how their code looks.


#### Prefer Explicit Returns
Use explicit returns. Implicit returns make the code **unreadable**. They are
only fine when we are returning a value in single-line match arms: 
```rust
fn check_condition(flag: bool) -> String {
    match flag {
        true => String::from("true"),
        false => String::from("false"),
    }
}
```

#### Whitespace
Too much whitespace is better than too little - in my opinion. Code with too
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

For reference, here is an example of what I usually do in C-likes:
```c++
bool some_function(string str)
{
    if (str == "asdfasdf")
    {
        return true;
    }
    else
    {
        return false;
    }
}
```


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
