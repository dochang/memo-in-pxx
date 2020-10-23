---
title: "Rust 程序设计语言 1"
date: 2020-10-23T13:32:30+08:00
categories: [rust]
tags: [书摘, 语言]
draft: false
---

[The Rust Programming Language][trpl] [1.1 节][source]的摘要。

<!--more-->

# 安装

通过 rustup 工具安装。

rustup 是官方推荐的安装、管理 Rust 版本的工具。如果你需要使用其他的安装方式，请访问[此处][2]

## 在 Linux 或 macOS 上安装 rustup

```shell
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

有些通用 Rust 包依赖 C 代码。建议同时安装一套 C 语言的编译器和链接器。

## 在 Windows 上安装 rustup

请访问[此处][install]并根据说明安装 Rust 。在安装过程中，你可能会收到提示，告诉你需要安装 C++ build tools for Visual Studio 2013 或更高版本。最简单的方法是安装 [Build Tools for Visual Studio 2019][vs] 。当询问你安装哪些组件时，选择 "C++ build tools" ，该选项应包含 Windows 10 SDK 和英文资源包。

## 更新与卸载

更新

```shell
$ rustup update
```

要卸载 Rust 及 rustup ，执行

```shell
$ rustup self uninstall
```

## 常见故障排除

要确认 Rust 是否已正确安装，执行

```shell
$ rustc --version
```

应返回如下格式的信息：

```
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

如果无法运行 rust ，请至 Rust 官方社区寻求帮助。

## 本地文档

安装 Rust 会在本地安装一份完整的文档。执行 `rustup doc` 会自动打开浏览器，可离线阅读本书。

如果你希望了解标准库中的某个类型或函数，可以随时前往 API 文档查找。

[trpl]: https://doc.rust-lang.org/book/
[source]: https://doc.rust-lang.org/book/ch01-00-getting-started.html
[install]: https://www.rust-lang.org/tools/install
[vs]: https://visualstudio.microsoft.com/visual-cpp-build-tools/
