# struct

1. 定义struct的方式

```go
type Stu struct{
    Name string
    Age int
}
//方式一 结构体变量
var stu = Stu{
    Name:"tom",
    Age:12,
}

stu := Stu{"marry",13}
//方式二 结构体指针变量
stu := &Stu{"xiaoming",16} 
//取出
fmt.println(*stu)
```

