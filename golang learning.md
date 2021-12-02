### var new make区别

测试如下 ：

```go
	var (
		a []int
		b = make([]int, 3)
		c = new([]int)
	)
```

输出如下：

```go
a:[] b:[0 0 0] c:&[]
```

​	可以发现，对于切片类型，直接var是不会分配内存的，为nil。make会分配内存并初始化0值。new会创建一个指针类型。

​	**注意**，对于nil类型的a和指针类型的c，都可以通过append追加元素。

```go
	a = append(a, 1)
	*c = append(*c, 1)
```

输出如下：

```go
a:[1] c:&[1]
```

​	**注意**，`var c int`也会分配内存，初始化0值，这里只讨论var, new, make对slice的效果。

​	**注意**，在make后append，是在初始化的0值之后append，这里在打题的时候发现make后结果不正确。

