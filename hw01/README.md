# Homework 01: Rust Finger Exercises

## Overview ##

writing some short functions in a Rust library, building and testing using Cargo, and writing modules. 

이 연습은 러스트 에코시스템에 익숙해 지는것을 목표로 한다

#### Classroom for GitHub

## Provided Code ##

Just one file, `tests_provided.rs`, which contains several test cases. We're
asking you to write everything else from scratch, but we'll give you function
signatures below, as a starting point.

## Part 01: Cargo ##

Don't clone your GitHub repository just yet.
To start off, let's create a new Rust library: `cargo new hw01`.

If you are not already in a git repository when you create your project, Cargo
will create a git repository (and `.gitignore`) for you. Then, you can add this
your GitHub repository as a git remote, with something like:

```
git remote add origin git@github.com:cis198-2016s/hw01-<username>.git
git push -u origin master
```

(If you're not using SSH for GitHub, you need to use the HTTPS URL of your
repository.)

Cargo creates this directory structure for you:

```
hw01
├── .git/
├── .gitignore
├── Cargo.toml
└── src
    └── lib.rs
```

You can build this project from anywhere in the project tree with
`cargo build`. Remember to compile periodically as you work.

### Modules ###

더 진행하기 전에 모듈과 상자에 대해 한 마디 하겠습니다.

크레이트는 모든 Rust 라이브러리 또는 패키지입니다. 모듈은 상자의 내부 논리 섹션
입니다.

상자의 각 섹션을 다른 모듈로 구성해야 합니다,
소비자는 필요한 부분만 가져올 수 있습니다. 다음에서 이 작업을 수행할 수 있습니다.

Before you go any further, a word on modules and crates.

Crates are any Rust library or package. Modules are the inner logical sections
of a crate.

You will want to organize each section of your crate into a different module,
so consumers can only import the parts that they need. You could do this in
`lib.rs`:

```rust
pub mod problem1 {
}

pub mod problem2 {
}

pub mod problem3 {
}

pub mod problem4 {
}

// ...
```

But this gets unwieldy pretty fast. You can instead put these modules in
separate files:

```
hw01
├── Cargo.toml
└── src
    ├── problem1.rs
    ├── problem2.rs
    ├── problem3.rs
    ├── problem4.rs
    └── lib.rs
```

Every `.rs` file defines a module that is the same as its filename, so
`problem1.rs` implicitly defines the module `problem1`.

Crates are organized into trees of files, where one file is the root, typically
`src/lib.rs` (or `src/main.rs`). To include a module, you need to declare it in
the crate root. To add `problem1` as a module, add the line `pub mod problem1;`
to the top of `src/lib.rs`. (This is equivalent to defining a module in the
file itself, with `pub mod problem1 { ... }`.) Until you add this directive,
Cargo will not try to build `problem1` part of your crate. The `pub` keyword in
this directive exposes the module `problem1` to any other crate that imports
your library. You can omit `pub` to leave modules private; however, if a
function is not exported or used internally, it will emit a dead code warning.

Within a module, all members (functions, types, submodules) are private by
default. The `pub` keyword can also be used to make any of these available from
outside of the module.

모든 `.rs` 파일은 해당 파일 이름과 동일한 모듈을 정의합니다.
문제1.rs`는 암시적으로 모듈 `problem1`을 정의합니다.

크레이트는 파일 트리로 구성되며, 일반적으로 하나의 파일이 루트입니다.
src/lib.rs`(또는 `src/main.rs`). 모듈을 포함하려면 모듈을 상자 루트인
에 선언해야 합니다. 문제1`을 모듈로 추가하려면 `pub mod problem1;` 줄을 추가합니다.
줄을 `src/lib.rs` 상단에 추가합니다. (이는 파일 자체에 모듈을 정의하는 것과 동일합니다.
파일 자체에 모듈을 정의하는 것과 같습니다(`pub mod problem1 { ... }`.) 이 지시어를 추가하기 전까지는,
카고는 크레이트의 `problem1` 부분을 빌드하려고 시도하지 않습니다. 이 지시어의 `pub` 키워드는
이 지시어는 `problem1` 모듈을 라이브러리를 임포트하는 다른 모든 크레이트에
모듈을 노출한다. 모듈을 비공개로 유지하려면 `pub`을 생략할 수 있지만, 모듈을 내보내지 않거나
함수를 내보내거나 내부적으로 사용하지 않으면 데드 코드 경고가 표시됩니다.

모듈 내에서 모든 멤버(함수, 타입, 서브모듈)는 기본적으로 비공개입니다.
기본적으로 비공개입니다. 'pub` 키워드를 사용하여 모듈 외부에서
모듈 외부에서도 사용할 수 있습니다.

Translated with www.DeepL.com/Translator (free version)

```rust
// problem1.rs

/// Functions are private (only available to this module) by default.
/// Use the `pub` keyword to mark this function as public.
pub fn sum(slice: &[i32]) -> i32 {
    // ...
}
```

다른 모듈에서 항목을 가져오는 방법에는 몇 가지가 있습니다:

1. 파일 범위에 '합계'를 추가하려면 파일 상단에 'use problem1::합계'라는 줄을
   줄을 추가합니다. sum()`으로 함수를 호출할 수 있습니다. 사용해야 하는 부분만
   만 가져오세요.

2. 모듈에서 여러 항목을 가져오려면 중괄호를 사용합니다:
   `use problem1::{sum, dedup};`

3. 모듈에서 모든 항목을 가져오려면 `use problem1::*`를 작성합니다.

4. 전체 모듈을 가져오려면 `use problem1;`을 작성합니다. 이 양식을 사용하려면 다음을 수행해야 합니다.
   모듈 이름으로 모듈의 멤버를 한정해야 합니다(예: `problem1::sum()`).
   이 방법은 더 장황하지만 범위의 네임스페이스를 오염시키지 않습니다.

시작하기 위해 몇 가지 테스트 케이스가 포함된 `tests_provided.rs` 파일을 제공했습니다.
파일을 제공했습니다. 이 파일을 라이브러리에 별도의 모듈로 추가해야 합니다.
모듈과 마찬가지로 라이브러리에 별도의 모듈로 추가해야 합니다(하지만 테스트가 반드시 `pub`일 필요는 없습니다).

모듈에 대한 자세한 내용은 Rust 책에서 확인할 수 있습니다.
[여기](https://doc.rust-lang.org/book/crates-and-modules.html).


Translated with www.DeepL.com/Translator (free version)
There are a few different ways to import items from a different module:

1. To add `sum` to the scope of a file, add the line `use problem1::sum` to the
   top of the file. You can call the function with `sum()`. Try to import only
   what you need to use.

2. To import multiple things from a module, use curly braces:
   `use problem1::{sum, dedup};`

3. To import all items from a module, write `use problem1::*`.

4. To import an entire module, write `use problem1;`. This form requires you to
   qualify members of the module with the module name (e.g. `problem1::sum()`).
   This is more verbose but does not pollute the namespace of your scope.

We provided a `tests_provided.rs` file with a few test cases to start you off
with. You should add this to your library as a separate module, as you did with
each `problemX` module (but the tests don't need to be `pub`).

You can read more about modules in the Rust book
[here](https://doc.rust-lang.org/book/crates-and-modules.html).
