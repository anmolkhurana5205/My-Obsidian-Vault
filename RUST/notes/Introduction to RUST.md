- .rs is the extension of the rust file.
- RUST is a strictly typed language. Unlike js
- It has a separate compilation step. Unlike js where one by one line is compiled and get executed.
- RUST has low level System access.
- Incredibly faster than JS
- supports multi threading unlike js(node.js where there is only thread)
- It is memory safe.
- Package manager is cargo for rust.
- dependencies file or manifest file is cargo.toml
- we can fetch and build external libraries from crates.io (command = cargo publish)

### Applications of RUST
- Create backend for full stack apps
- Creating CLI.
- Crete browsers
- Great code editors

### cargo init / cargo new
- to create a new rust project.
- the only difference is "cargo init" doesn't make the new folder it just makes the already present folder a cargo project
- but on the other side cargo new create a new folder and makes it a cargo project.
### cargo test
-  runs your test suite.
### cargo doc
-  build docs for your project
### cargo run
-  it builds + execute your project.
### cargo build
- compile your rust project

| Command                  | Description                               |
| ------------------------ | ----------------------------------------- |
| `cargo new project_name` | Create a new project                      |
| `cargo build`            | Compile the project                       |
| `cargo run`              | Build and run the project                 |
| `cargo check`            | Check code for errors (faster than build) |
| `cargo test`             | Run tests                                 |
| `cargo update`           | Update dependencies                       |
| `cargo doc --open`       | Generate and open documentation           |
| `cargo publish`          | Publish a crate to crates.io              |
