# fmt

* ```
   //输出bool值
      flag := true
      fmt.Printf("%t\n",flag) // true
  ```

* ```
  //输出十进制形式输出
    fmt.Printf("%d\n",123)   // 123
  ```

*  %v     值的默认格式表示 
* %d  输出十进制形式
* %T 输出值的类型

* %s     Sprintf() 是把格式化字符串输出到指定的字符串中，可以用一个变量来接受，然后在打印 

```sql
sql := fmt.Sprintf("select * from matches where series_ex_id = '%s'  AND game_no = %d", exId, nowBo)
```