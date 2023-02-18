# Go语言
Go 编程语言是一个开源项目，旨在提高程序员的工作效率。

Go 富有表现力、简洁、干净、高效。它的并发机制使编写充分利用多核和联网机器的程序变得容易，而其新颖的类型系统支持灵活和模块化的程序构建。Go 可以快速编译为机器代码，但具有垃圾收集的便利性和运行时反射的强大功能。它是一种快速的、静态类型的编译语言，感觉就像一种动态类型的解释语言。
# 目录
[toc]

## 定义结构体及结构体函数
```golang
package main

import "fmt"
// define a struct
type book struct{
        title string
        author string
        id int
}

func (b *book) getBook(){
        fmt.Println(b.title)
}

// function main
func main(){
    book1 := book{"hah","aut",1}
    book1.getBook()
}
```

## 接口
```golang
package main
import (
        "fmt"
)

type Linux interface{
    info()
}

type Ubuntu struct{}
type Centos struct{}

func (this *Ubuntu) info(){
    fmt.Println("this is ubuntu")
}

func (this *Centos) info(){
    fmt.Println("this is centos")
}


func main(){
    var linux Linux
    linux = new(Ubuntu)
    linux.info()

    linux = new(Centos)
    linux.info()
}

```


