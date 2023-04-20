### Problem 01: Vector & Slice Manipulation ###

*벡터, 반복, 패스 바이 레퍼런스, 가변성, 함수 포인터.*

라이브러리에서 'problem1.rs' 안에 'problem1'이라는 이름의 새 모듈을 생성합니다.

기본 Rust를 처음 맛보려면 다음 세 가지 함수를 완성하세요.
이 함수는 모두 인수를 값으로 받는 것이 아니라 참조로 받습니다.
값으로 인수를 받습니다.

대상 동작을 구현하는 `Vec` 클래스의 표준 라이브러리 메서드는 사용하지 마세요.
표준 라이브러리 메서드를 사용하면 이 연습의 요점이 무색해지므로 사용하지 마십시오.
:). (하지만 `contains()` 및 `push()`와 같은 기본 함수는 괜찮습니다).



*Vectors, iteration, pass-by-ref, mutability, function pointers.*

Create a new module in your library named `problem1` inside `problem1.rs`.

To get a first taste of basic Rust, complete the following three functions.
Note that all of these functions take their arguments by reference, rather than
by value.

Don't use any of the standard library methods on the `Vec` class which implement
the target behavior, since using them would defeat the point of this exercise
:). (However, basic functions such as `contains()` and `push()` are fine).

```rust
/// Computes the sum of all elements in the input i32 slice named `slice`
pub fn sum(slice: &[i32]) -> i32 {
    // TODO
    unimplemented!();
}

/// Deduplicates items in the input vector `vs`. Produces a vector containing
/// the first instance of each distinct element of `vs`, preserving the
/// original order.
pub fn dedup(vs: &Vec<i32>) -> Vec<i32> {
    // TODO
    unimplemented!();
}

/// Filters a vector `vs` using a predicate `pred` (a function from `i32` to
/// `bool`). Returns a new vector containing only elements that satisfy `pred`.
pub fn filter(vs: &Vec<i32>, pred: &Fn(i32) -> bool) -> Vec<i32> {
    // TODO
    unimplemented!();
}
```

