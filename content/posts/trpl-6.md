---
title: "Rust 程序设计语言 6"
date: 2020-10-27T18:33:09+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [1.3 节][source]第三部分的摘要。

<!--more-->

# 编写一个猜数字游戏

## 进行比较

```rust
use rand::Rng;
use std::cmp::Ordering;

// 一个枚举类型，用于测试比较的结果。

use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1, 101);

    println!("The secret number is: {}", secret_number);

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    let guess: u32 = guess.trim().parse().expect("Please type a number!");

    // Rust 允许我们用一个变量掩盖掉一个同名变量。

    // `parse` 可以将字符串解析为多种数字类型，所以需要指定 `guess` 的类型，比
    // 如 `let guess: u32` 表示新的 `guess` 变量是 `u32` 类型，即一个 32 位无符
    // 号整数。

    println!("You guessed: {}", guess);

    match guess.cmp(&secret_number) {
        Ordering::Less => println!("Too small!"),
        Ordering::Greater => println!("Too big!"),
        Ordering::Equal => println!("You win!"),
    }

    // `match` 用于分支判断，`match` 的分支称为 *arms* 。每一个 arm 由一个模式
    // 和对应要执行的代码组成。
}
```

[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html
