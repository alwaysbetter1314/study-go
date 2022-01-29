# study-go
study golang

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

