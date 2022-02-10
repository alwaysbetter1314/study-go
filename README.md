# study-go
> study golang  
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


