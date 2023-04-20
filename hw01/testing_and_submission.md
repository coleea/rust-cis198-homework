#### Testing

Before you move on, take a look at `tests_provided.rs`.

At the top of this file, there's a `#![cfg(test)]` attribute. `cfg`, short for
"configuration", is part of how Rust handles conditional compilation. This is
similar to (but way better than) the use of `#ifdef`s and include guards in C.
In this case, `#![cfg(test)]` tells the compiler that this module is not to be
compiled unless the `--test` flag is used with `rustc` (`cargo test` adds this
flag under the hood). This is handy because it means that you don't have to
waste time recompiling your tests every time you build unless you're actually
going to run them.

All of the functions in `test.rs` are annotated with the `#[test]` attribute;
this tells the compiler that they're tests. Test functions must have the
signature `fn() -> ()`, or else they will not compile. Tests will be run when
you invoke `cargo test`.

Any test which doesn't cause a `panic!` is considered to pass. You should use
[`assert!`][assert] or [`assert_eq!`][assert_eq] to check guarantees and
equality (respectively).

[assert]: https://doc.rust-lang.org/std/macro.assert!.html
[assert_eq]: https://doc.rust-lang.org/std/macro.assert_eq!.html

As an aside, the `cfg` attribute has many other uses, like knowing
which OS or architecture you're compiling for.

We have provided a few tests to start you off with. You should add at least one
non-trivial test for each function that you implement. Write these in a new
module, `tests_student.rs`, and declare the module in `lib.rs`.


## Submission

Commit and push your work to the master branch of your Classroom for Github
repository for this HW. **Make sure it is visible on Github!** This is your
submission. (Work must be in the master branch at the due time.)

Your repository should look like this:

```
[git root]
├── Cargo.toml
└── src
    ├── lib.rs
    ├── problem1.rs
    ├── problem2.rs
    ├── problem3.rs
    ├── problem4.rs
    ├── tests_provided.rs [same as given]
    └── tests_student.rs [your tests]
```

`cargo test` should run all of the tests in your homework. Make sure you have
written at least one test for each function you have written.
