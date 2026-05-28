# Closures

In [Capturing References or Moving Ownership](https://doc.rust-lang.org/book/ch13-01-closures.html#capturing-references-or-moving-ownership)

It mentions:

Closures can capture values from their environment in three ways, which directly map to the three ways a function can take a parameter:

- borrowing immutably,
- borrowing mutably, and
- taking ownership.

The following example demonstrates these the first two ways:

```rust
fn main() {
    // 1. Define a mutable list
    let mut list = vec![1, 2, 3];
    println!("Before defining closure: {list:?}");

    // 2. Define a closure that only borrows the list
    let only_borrows = || println!("From closure: {list:?}");

    println!("Before calling closure: {list:?}");
    only_borrows();
    println!("After calling only_borrows closure: {list:?}");

    // 3. Define a closure that borrows mutably
    let mut borrows_mutably = || list.push(7);
    borrows_mutably();
    println!("After calling borrows_mutably closure: {list:?}");

    // 4. The closure _BORROWS_ the list, either mutably or immutably. It DOES NOT TAKE OWNERSHIP of the list.
}
```

The output of the program is:

```
Before defining closure: [1, 2, 3]
Before calling closure: [1, 2, 3]
From closure: [1, 2, 3]
After calling only_borrows closure: [1, 2, 3]
After calling borrows_mutably closure: [1, 2, 3, 7]
```
