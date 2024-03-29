# 安装rust 
- 官方下载： https://www.rust-lang.org/tools/install
- 下载rust init  Terminal安装 （默认安装即可）

# 什么是rust工具链：
- Rust 工具链是一组工具和组件的集合，用于开发、构建和管理 Rust 项目。这个工具链包括 Rust 编译器、包管理工具（Cargo）、标准库、文档生成工具等，提供了一套完整的工具集，使得 Rust 开发变得简单和一致
    - <font color="#00BFFF">Rust 编译器 (rustc) </font> ： Rust 编译器负责将 Rust 代码翻译成目标平台的机器码，从而生成可执行文件。
    - <font color="#00BFFF">包管理工具（Cargo）</font>： Cargo 是 Rust 的官方包管理工具，用于构建、测试和发布 Rust 项目。它简化了依赖管理、构建过程以及与 crates.io（Rust 包的注册中心）的交互。

    - <font color="#00BFFF">Rust 标准库</font>： Rust 标准库是一组 Rust 提供的核心功能和数据结构，用于支持常见的编程任务，例如字符串处理、文件操作、多线程编程等。

    - <font color="#00BFFF">Rustup</font>： Rustup 是一个用于安装、管理和升级 Rust 工具链的工具。它可以让你轻松切换 Rust 的不同版本和工具链。

    - <font color="#00BFFF">文档生成工具</font>： Rust 的文档工具 (rustdoc) 可以从代码中提取文档注释，并生成项目的文档。这有助于创建清晰的文档，使得项目更易于理解和使用。

# vscode - rust 必要插件： rust-analyzer

# 创建rust项目：
- Terminal >>
    - cd path_to_projects
    - cargo new test_pro  // rust 建议项目用蛇形命名
        - (cargo new 默认情况下会为新建的rust初始化一个git仓库  如果不想创建git可以通过添加<font color="#00BFFF"> --vcs </font>  // 例如： cargo new test_pro --vcs none)
    - cd test_pro
    - code .

# 编译运行（需要已安装MSVC/TMD-GCC 等编译器）
- cargo run

# MSVC与GNU
- “GNU”指的是 GNU 工具集，这是一个由自由软件基金会（Free Software Foundation，FSF）开发和维护的一组工具，其中包括 GCC（GNU Compiler Collection）等工具。这组工具以自由软件授权许可发布，允许用户自由使用、修改和传播。
    - rust 默认编译器是MSVC  即： **stable-msvc**
    - 也可以使用GNU  即：**stable-gnu**
    - 如果使用TMD-GCC则可以切换到 **stable-gnu 工具链**
    - 切换命令：**<font color="#00BFFF" >rustup default stable-gnu</font>**

# 显示当前工具链的详细信息： **<font color="#00BFFF" >rustup show </font>** or **<font color="#00BFFF" >rustup toolchain list</font>**
- Default host：指定了默认的目标主机（target host）。  <architecture>-<vendor>-<system>  CPU架构-硬件厂商-操作系统
- rustup home：显示了 rustup 工具本身的安装路径。
- installed toolchains：列出了已安装的 Rust 工具链，包括稳定版和夜版（nightly）。
- active toolchain：显示了当前活跃的工具链，包括默认工具链的版本信息。

# 更新Rust和工具链： rustup update

# 重新生成Cargo.lock文件：
- 有时候重新生成Cargo.lock文件可能有助于解决依赖关系的问题。你可以尝试删除Cargo.lock文件，然后再次运行 cargo build。

# 构建项目
- cargo build  // 将在 target/debug/ 目录下生成可执行文件
- cargo build --release  // 将在 target/release/ 目录下生成优化过的可执行文件
- Cargo 会自动处理依赖关系、编译和链接过程，使得整个过程非常简单。如果需要进一步自定义构建过程，你可以编辑项目的 Cargo.toml 文件



# 清理并重新构建
- cargo clean
- cargo build


# crates.io 是 Rust 编程语言的包管理器，类似于其他语言中的包管理系统（如 Python 的 PyPI、JavaScript 的 npm）。它是 Rust 社区共享、发现和使用代码包的中心平台。


Rust 不直接提供类似于 C++ 中 system("pause") 的系统调用来暂停控制台窗口。Rust 更倾向于跨平台性和安全性，而不鼓励使用依赖于特定平台的系统调用。

在 Rust 中，你可以使用标准库中的 std::io::stdin().read_line() 来等待用户的输入，以实现控制台窗口的暂停。下面是一个简单的例子：

# 安装maturin

- 如果使用TDM-GCC 可能会报错找不到gcc
    - set CC=D:/tdmgcc/TDM-GCC/bin/gcc.exe
    - set AR=D:/tdmgcc/TDM-GCC/bin/ar.exe

- <font color="#00BFFF"> cargo install maturin </font>
- <font color="#00BFFF"> cargo add pyo3 </font>  将pyo3添加到Cargo.toml 的 dependencies

use std::io;

fn main() {
    // 你的程序代码

    // 在这里添加等待输入的语句
    let mut input = String::new();
    io::stdin().read_line(&mut input).expect("Failed to read line");
}