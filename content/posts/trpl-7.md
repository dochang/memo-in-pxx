---
title: "Rust 程序设计语言 7"
date: 2020-10-28T18:48:09+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [第 2 章][source]第四部分的摘要。

<!--more-->

# 编写一个猜数字游戏

## 实现循环猜测

```rust
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1, 101);

    loop {
        // `loop` 关键字用于建立一个无限循环。

        println!("Please input your guess.");

        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        // 为了避免用户输入的字符串转换数字失败导致程序退出循环，这里使用
        // `match` 代替 `expect` 。

        // `num` 为实际转换后的值，保存在 `Ok` 中。

        // `_` 表示匹配任何 `Err` 。`continue` 表示结束当前循环，开始下一次循环。

        println!("You guessed: {}", guess);

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
                // 当用户猜中数字时退出循环。因为循环是程序的最后一个部分，因此
                // 退出循环也就退出了程序。
            }
        }
    }
}
```

## 总结

通过实际编写猜数字这个项目，我们了解了 Rust 带来的一些新的概念： `let` 、 `match` 、方法、关联函数、 crate 等等。在接下来的几章中，我们将更详细的学习这些信息。第三章涵盖了大多数语言都有的概念，例如变量、数据类型、函数。第四章解释了所有权，一个令 Rust 有别于其他语言的特色。第五章讨论了结构体和方法。第六章解释了枚举是如何工作的。

[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html
