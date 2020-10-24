---
title: "Rust 程序设计语言 3"
date: 2020-10-24T17:50:43+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [1.3 节][source]的摘要。

<!--more-->

# Hello, Cargo!

Cargo 是 Rust 的构建系统及包管理器。

如果你使用 rustup 安装 Rust ，那么 Cargo 会被一同安装。如果你使用其他方法安装 Rust ，请通过如下命令确认 Cargo 是否已被安装：

```shell
$ cargo --version
```

如果显示 Cargo 版本号，则表示 Cargo 已被安装。

## 建立新项目

```shell
$ cargo new hello_cargo
$ cd hello_cargo
```

Cargo 会为新项目生成两个文件：`Cargo.toml`, `src/main.rs` 。

Cargo 默认还会为项目初始化一份 Git 仓库。可以通过 `cargo new --vcs=[git|hg|pijul|fossil|none]` 改变这个行为。

`Cargo.toml` 的内容接近下面的示例：

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"

[dependencies]
```

`[package]` 一节用于配置包的基本信息。`edition` 表示使用哪个版本的 Rust ，详情见附录 E 。

Cargo 要求源代码文件放在 `src` 目录下。项目的顶层目录应该只存放 README ，许可证，项目配置或其他不与代码直接相关的文件。

## 构建和执行

```shell
$ cargo build
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
```

生成可执行文件位于 `target/debug/hello_cargo` 。

```shell
$ ./target/debug/hello_cargo # or .\target\debug\hello_cargo.exe on Windows
Hello, world!
```

首次执行 `cargo build` 还会在项目根目录建立 `Cargo.lock` 文件。这个文件用于跟踪当前各依赖的精确版本号。该文件由 Cargo 管理，你永远都不需要手工编辑这个文件。

可以用一句话编译并执行程序：

```
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.0 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

`cargo build` 默认不会重新编译未修改的源文件。

`cargo check` 用于检查代码并确保能够编译，但不会输出编译结果。此命令较 `cargo build` 更快，可用于在编码阶段定期对代码进行检查，当编码完成后再使用 `cargo build` 生成可执行文件。

## 构建 release 版本

使用 `cargo build --release` 。可执行文件位于 `target/release` 目录。


[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch01-03-hello-cargo.html
