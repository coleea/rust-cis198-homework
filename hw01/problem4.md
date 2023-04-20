### Problem 04: Towers of Hanoi ###

*Mutability, type aliases, vecs, tuples, enums.*

[The Towers of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi) is a
classical mathematics and computer science puzzle. Imagine you have three pegs,
one of which holds a stack of discs in increasing size from bottom to top. Your
goal is to move all of the discs from the first peg to the third peg, using the
second peg as an intermediate. Your only restrictions are that you may only
move one disc at a time, and a disc may only be placed on a disc larger than it
(or on an empty peg). Check out the Wikipedia page for more details and snazzy
animations.

In this instance, we've provided you with an enum type containing the possible
names of `Peg`s and a type alias defining a move between two pegs.

This function will take in a number of discs, and the names of the three
pegs, and return a vector of `Move`s.

```rust
/// #[derive(...)] statements define certain properties on the enum for you for
/// free (printing, equality testing, the ability to copy values). More on this
/// when we cover Enums in detail.

/// You can use any of the variants of the `Peg` enum by writing `Peg::B`, etc.
#[derive(Clone, Copy, Debug, Eq, PartialEq)]
pub enum Peg {
    A,
    B,
    C,
}

/// A move between two pegs: (source, destination).
pub type Move = (Peg, Peg);

/// Solves for the sequence of moves required to move all discs from `src` to
/// `dst`.
pub fn hanoi(num_discs: u32, src: Peg, aux: Peg, dst: Peg) -> Vec<Move> {
    // TODO
    unimplemented!();
}
```