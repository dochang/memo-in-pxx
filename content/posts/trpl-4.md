---
title: "Rust 程序设计语言 4"
date: 2020-10-25T17:54:10+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [第 2 章][source]第一部分的摘要。

<!--more-->

# 编写一个猜数字游戏

## 初始化项目

```shell
$ cargo new guessing_game
$ cd guessing_game
```

## 处理输入

修改 `src/main.rs`

```rust
use std::io;

// Rust 默认只会从 `std::prelude` 导入很少的内容到主程序中，其他类型需要使用
// `use` 显式导入。

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();

    // Rust 使用 `let` 声明变量，默认是*不可变*的，如果需要声明可变变量，使用
    // `let mut` 。

    // `String` 使用 UTF-8 编码。

    // `::` 表示 `new` 是 `String` 类型的_关联函数_。关联函数实现于类型之上，而
    // 非实例。某些语言称其为_静态方法_。

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    // `std::io::stdin` 函数返回 `std::io::Stdin` 的一个实例。

    // `&` 表示该参数为引用。引用默认是不可变的，如果需要可变引用，使用 `&mut` 。

    // `read_line` 的返回值为 `io::Result` 类型。Result 类型属于枚举。枚举就是
    // 值为固定集合的类型。

    // 对于 Result 类型来说，其值为 `Ok` 或 `Err` 。

    // 如果 `Err` 调用 `expect` ，会引起程序崩溃并将传入的参数作为错误信息输出。如果 `Ok` 调用 `expect` ，会返回 `Ok` 所持有的值。

    println!("You guessed: {}", guess);

    // `{}` 表示这里输出一个参数。`{}` 可以使用多次来表示多个参数，按顺序对应。
}
```

[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html
