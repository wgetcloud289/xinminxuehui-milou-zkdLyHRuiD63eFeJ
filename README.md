
#### 算数运算符



```
a = 1 + 1 // 2
a = 10 - 5 // 5
a = 10 / 5  // 2
a = 10 / 0 // js中除以0不会报错，结果是Infinity
a = 2*2 // 4
a = 2**2 // 
a = 10 % 4 // 取余，2


```

js中算数运算，除了字符串的加法，会自动将非数值转换为int进行计算，不像其他语言会报错



```

a = 10 + true // 11

a = 10 - "3" // 7

a = 5 + null // 5

a = 5 - undefined // NaN

```

字符串的加法，会将非字符串的值转换为字符串，进行字符串拼接



```
a = "1" + a // "1a"

a = "1" + 1 // "11"

a = "1" + null // 1null

```


> 利用算数运算隐式类型转换的特性，也可以用于类型转换，比如 `true +''`,使用值与空字符串相加，结果会将true转换成字符串的true


#### 赋值运算符


`=`用来将一个值赋值给一个变量



```
let a 

a = 10 // 将右边的值，赋值给左边变量

let b = a // 将a赋值给b，一个变量只有在左边的时候才是变量，在右边的时候就是值

```

赋值运算



```
// 大部分运算符不会改变变量的值，赋值运算符除外

a = 10
a + 1 // a+1的结果是11，但是a还是10，结果没有赋值

a += 1 // a的结果是11，等价于 a = a + 1, /= 、*= 等等原理一样

```

`??=`空赋值


只有当变量的值是null或undefined的时候，才会进行赋值操作



```
     let a
        a ??= 1 // a没有值，将1赋值给a
        console.log(a) // 1


        let b = 10
        b ??= 2 // b已经有值了，所以不会将2赋值给b
        console.log(b) // 2


```

#### 一元正负



```
let a = 10
// 正号:不会改变数值的符号	
a = +a // 10

// 负号:可以对数值进行符号位取反
let b = 10
b = -b // -10
a = -a // -10

// 当对非数值类型进行正负运算时，会先将其转化为数值然后再运算
let c = "10"
c = +c // int 10，等价于b=Number(c),也可以使用一元的+转换类型
c = -c // int -10

```

#### 自增和自减


##### **自增**


自增分为前自增(变量\+\+)和后自增(\+\+变量)



```
// 前自增
let a = 10
console.log(a++) // 10
console.log(a) // 11


// 后自增
let b = 20
console.log(++b) // 21
console.log(b) // 21

// 前后自增都会使原变量的值增加1，区别在于返回值不同
// 前自增表达式的返回值是自增前的值，后自增的返回值是自增后的值

```

##### **自减**


自减也分为前自减和后自减，原理与自增一致



```
let c = 10
console.log(c--) // 10
console.log(c) // 9

let d = 10
console.log(--d) // 9
console.log(d) // 9

```

#### 逻辑运算符


##### 逻辑非`!`



> `!` 可以对一个值进行非运算，可以对一个布尔值进行取反操作，如果对一个非布尔值进行取反，会先将其转化为布尔值再进行取反，可以利用该特定将其他类型转换为布尔值



```
let result
result = !0 // true

```

##### 逻辑与`&&`



> 与运算如果所有的表达式都是为true，则返回true，否则返回false
> 
> 
> 与运算是短路的，如果有值为false，则直接返回false，不会向后执行



```
let result 

result = true && true // true

result = true && false // false

result = true && alert(1) // alert会执行

result = false && alert(1) // alert不会值

```


> 对于非布尔值的运算，会将其转化为布尔值进行运算，但是最终返回不是布尔，会返回原值
> 
> 
> 如果有值为false，则直接false的值，如果值都为true，则返回最后一个值



```
let result
result = 1 && 2 && 3 // 3

result = 1 && 0 && 2 // 0

```

##### 逻辑或`||`



> 当 \|\|运算的时候左右有true的值，则返回true，否则false
> 
> 
> 或运算也是短路的，如果找到true则直接返回，不会向后运算
> 
> 
> 对于非布尔值的运算，会转换为布尔值然后运算，但是最终也会返回原值，如果第一个是false返回第二个值



```
let result
result = true || false // true
result = false || false // false


result = 1 || 2 // 1
result = 0 || 2 // 2

result = 1 || alert(1) // 不会会执行alert
result = 0 || alert(1) // 会执行alert

```

#### 关系运算符



> 检查两个值之间的关系是否成立，成立返回true，不成立返回false



```
let result 

result = 5 > 5 // false
result = 5 >=5 // true
result = 5 <= 5 // true


// 当对非数值进行关系运算时，会先转为为数值再比较
result = "1" > false // true
result = 5 < "10" // true

// 当关系运算符两端是两个字符串，不会将字符串转换数值，而是逐位比较自费的Unicode编码
result = "a" < "b" // true
result = "12" > "2" // false ，即使两个字符串都是数值，也不会转换数值运算
result = +"12" > "2" // true 可以使用一元运算将一个值转换为数值，则会进行数值运算

```

#### 相等运算符



> `==`相等运算符，用来比较两个值是否相等，相等返回true，否则false
> 
> 
> * 如果两个值是不同类型时，相等运算符会将他们转换为同类型(通常是数值)再比较
> * null和undefined进行相等比较时返回true
> * NaN不和任何值相等，包括他自身



> `===`全等运算符都是用来比较两个值是否相等
> 
> 
> ​ 如果两个值是不同类型，不会进行类型转换，如果两个值类型不同，则直接返回false



```
let result 
// 相等运算
result = 1 == 2 // false

result = "1" == 1 // true

result = null == undefined // true

// 全等运算
result = "1" === 1 // false 
result = 2 === 2 // true
result = null === undefined // false，undefined和null相等，但是不全等

```


> `!=`：比较两个值是否不相等，会自动进行类型转换



> `!==`:比较两个值是否不全等，不会自动进行类型转换



```
result = 1 != 1 // false

result = 1 != "1" // false

result = 1 !== "1" // true

```

#### 条件运算符(三元运算符)



> 条件表达式?表达式1:表达式2
> 
> 
> 执行顺序：
> 
> 
> * 先对表达式进行一个求值判断，如果结果为true，则执行表达式1，如果结果为false，则执行表达式2



```
let a = 10
let b = 20

a > b ? alert("a") : alert("b")

```


```
let max = a > b ? a : b // 如果a大于b，则max=a，否则等于b


```

[运算符优先级](https://github.com)



> 运算符中()拥有最高优先级，如果需要优先运算，可以使用()把表达式包裹起来


 本博客参考[FlowerCloud机场](https://hushicha.org)。转载请注明出处！
