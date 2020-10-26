---
title: "Rust 程序设计语言 5"
date: 2020-10-26T18:44:36+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [第 2 章][source]第二部分的摘要。

<!--more-->

# 编写一个猜数字游戏

## 生成要猜的数字

### 使用 crate 得到更多功能

修改 `Cargo.toml` ，将 `rand` 加入依赖列表：

```toml
[dependencies]
rand = "0.5.5"
```

Rust 的依赖被称为 Crate 。一个 Crate 就是一个 Rust 源代码文件的集合。我们建立的项目用于生成可执行文件，因此是一个 binary crate 。`rand` 这样的依赖用于被其他程序使用，因此是一个 library crate 。

Cargo 使用[语义版本号][semver]规范。本例中，`0.5.5` 是 `^0.5.5` 的简写形式，表示“公共 API 兼容 0.5.5 版本的任何版本”。

Rust 社区的软件仓库位于 [Crates.io][crates]

#### 使用 `Cargo.lock` 确保可重现的构建

首次运行 `cargo build` 时会建立 `Cargo.lock` 文件，Cargo 会将所有依赖和他们的版本号写入 `Cargo.lock` 。第二次构建时，Cargo 会检查该文件是否存在，如果存在，就使用此文件中指定的版本，而不再计算各依赖对应的版本。这可以保证构建是可重现的。

#### 更新新版本的 Crate

使用 `cargo update` 可以根据 `Cargo.toml` 重新计算各依赖的版本并将结果更新到 `Cargo.lock` 中。

### 生成随机数

修改 `src/main.rs` ：

```rust
use rand::Rng;

// `rand::Rng` 是一个 trait

use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1, 101);

    // `rand::thread_rng` 返回一个在当前线程有效的随机数生成器，种子由操作系统提供。

    // `gen_range` 由 `Rng` trait 定义，由 `use rang::Rng` 引入到当前作用域。

    // 执行 `cargo doc` 会生成当前项目以及所有依赖的文档，位于 `target/doc` 。
    // 执行 `cargo doc --open` 会自动在浏览器中打开文档页面。

    println!("The secret number is: {}", secret_number);

    // 调试用

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {}", guess);
}
```

[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html
[semver]: https://semver.org/
[crates]: https://crates.io/
