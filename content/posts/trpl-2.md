---
title: "Rust 程序设计语言 2"
date: 2020-10-23T18:39:39+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [1.2 节][source]的摘要。

<!--more-->

# Hello, World!

## 建立项目目录

```shell
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

## 编码和运行

Rust 代码文件名以 `.rs` 结尾，当文件名含有多个单词时，使用下划线分隔。例如，使用 `hello_world.rs` 而不是 `helloworld.rs` 。

建立文件 `main.rs`

```rust
fn main() {
    println!("Hello, world!");
}
```

保存、编译、执行：

```
$ rustc main.rs
$ ./main
Hello, world!
```

输出 `Hello, world!` 表示执行成功。

## 分析

```rust
fn main() {
}
```

`fn` 用于定义函数， `main` 函数是 Rust 程序的入口。Rust 的风格是 `{` 与 `fn` 放在一行。

使用 `rustfmt` 将你的代码格式化成 Rust 社区的标准风格。

Rust 的缩进风格是 4 个空格，不用 TAB 。

`println!` 是一个宏，如果没有 `!` ，比如 `println` ，则是一个函数。

使用 `rustc` 编译 `.rs` 文件。

[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch01-02-hello-world.html
