# 基础

## 目录

* [1 数据类型](broken-reference)
* [2 所有权的规则](broken-reference)
* [3 引用](broken-reference)

```rust
use rand::Rng;
// 基础库：比较
use std::cmp::Ordering;
// 基础库：输入流
use std::io;

fn main() {
    // 创建一个随机数生成器
    // 生成 1 到 100 之间的随机数
    // let mut rng = rand::thread_rng();
    // let random_number: u32 = rng.gen_range(1..=100);
    let sys_number: u32 = rand::thread_rng().gen_range(1..=100);
    // let strings = ['a', 'b', 'c', 'd'];
    // for str in strings {
    //     print!("str: {}", str);
    // }

    loop {
        let mut input = String::new();
        // 用户输入
        io::stdin().read_line(&mut input).expect("输入错误");
        let input: u32 = match input.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("非法数字，请重新输入");
                continue;
            },
        };
        println!("输入值：{}", input);
        match input.cmp(&sys_number) {
            Ordering::Less => println!("输入值: {} < 系统值: {}", input, sys_number),
            Ordering::Greater => println!("输入值: {} > 系统值: {}",  input, sys_number),
            Ordering::Equal => {
                println!("输入值: {} = 系统值: {}",  input, sys_number);
                break;
            },
        } 
    }
}

```

## 1 数据类型

1. Rust 是静态编译语言，编译时必须知道所有变量的数据类型
   1. 某些情况下，编译器可以推断出变量的类型。
   2. 如果类型复杂，如 字符串类型转成数字类型之后，必须显示表明类型，否则编译器会报错&#x20;
2. isize/usize
   1. 由计算机的架构所决定 32 | 64位。
   2. 主要在对集合进行索引操作时使用。

## 2 所有权的规则

1. 每个值都有一个所有者。
2. 一次只能有一位所有者。
3. 当所有者离开作用域时，该值将被删除。

## 3 引用

1. 一个作用域内，只能有 一个可变的引用，或者多个不可变的引用。也代表可变引用与不可变引用不能同时存在（同一变量）。
2. 引用必须一直有效。
