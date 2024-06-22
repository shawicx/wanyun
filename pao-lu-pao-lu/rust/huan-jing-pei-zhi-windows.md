# 环境配置（windows）

## 目录

* [1 配置文件](broken-reference)
* [2 换源](broken-reference)
  * [2.1 rustup](broken-reference)
  * [2.2 cargo](broken-reference)

## 1 配置文件

1. 文件位于 `C:\Users\{userName}\.cargo` 文件夹，文件名称是或者自己创建。
2. 使用命令`notepad config.toml`编辑文件（）。

## 2 换源

### 2.1 rustup

```bash
setx RUSTUP_DIST_SERVER [https://mirrors.ustc.edu.cn/rust-static](https://mirrors.ustc.edu.cn/rust-static)
setx RUSTUP_UPDATE_ROOT [https://mirrors.ustc.edu.cn/rust-static/rustup](https://mirrors.ustc.edu.cn/rust-static/rustup)
```

### 2.2 cargo

编辑配置文件，以下源任选一个即可。

```toml
# 清华大学
[source.crates-io]
replace-with = 'tuna'
[source.tuna]
registry = "https://mirrors.tuna.tsinghua.edu.cn/git/crates.io-index.git"

# 中国科技大学
[source.crates-io]
replace-with = 'ustc'
[source.ustc]
registry = "https://mirrors.ustc.edu.cn/crates.io-index"

# 阿里云
[source.crates-io]
replace-with = 'rustcc'
[source.rustcc]
registry = "https://code.aliyun.com/rustcc/crates.io-index.git"

```
