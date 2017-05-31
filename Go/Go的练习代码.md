# 平时练习Go的代码

1.go实现递归：

```
package main

import "fmt"

func main() {
	var result = fibonacci(10)
	fmt.Printf("fibonacci(%d) is: %d\n", 10, result)

}

func fibonacci(n int) (res int) {
	if n <= 0 {
		res = 0
	}else {
		res = n + fibonacci(n-1)
	}
	return
}
```


2.go实现回调

```
package main

import "fmt"

func main()  {
	callback(1,Add)
}

func Add(a,b int)  {
	fmt.Printf("The sum of %d and %d is: %d\n", a, b, a+b)
}

func callback(y int,f func(int,int))  {
	f(y,2)
}
```

3.函数调用

```
package main

import "fmt"

func main() {
	var f = Adder2()
	fmt.Print(f(1), " - ")
	fmt.Print(f(20), " - ")
	fmt.Print(f(300))
}

func Adder2() func(int) int {
	var x int
	return func(delta int) int {
		x += delta
		return x
	}
}
```


4.把函数付给变量

```
package main

import "fmt"

func main() {
	// make an Add2 function, give it a name p2, and call it:
	p2 := Add2()
	fmt.Printf("Call Add2 for 3 gives: %v\n", p2(3))
	// make a special Adder function, a gets value 3:
	TwoAdder := Adder(2)
	fmt.Printf("The result is: %v\n", TwoAdder(3))
}

func Add2() func(b int) int {
	return func(b int) int {
		return b + 2
	}
}

func Adder(a int) func(b int) int {
	return func(b int) int {
		return a + b
	}
}
```
