
# Pure Function

## In order to separate general functions, methods

### Not pure Function examples
<pre><code>

var name = "FP"
var greeting = ""
func makeGreeting() {
greeting = "Hello, \(name)"
}

func add(_ a: Int) -> Int {
return Int(arc4random()) + a
}

</code></pre>

### Pure Function examples
<pre><code>

func greeting(to name: String) -> String {
return "Hello, \(name)"
}

let greet = "Hello"
func greeting(_ name: String) -> String {
return "\(greet), \(name)"
}

</code></pre>

### Let's practice(my code & other person's code)

<pre><code>

//my code
func solution(_ nums: [Int]) -> Int {
var sum = 0
for i in nums {
sum += i
}
return sum
}

//other person
func solution(_ nums: [Int]) -> Int {
return nums.reduce(0, +)
}

</code></pre>

### My learning : Side Effect, reduce's using

# Higher-Order Functions

## Function that inputed or return function

### Example is supplyed in swift's Foundation Library

<pre><code>

let arr = [1, 2, 3, 4, 5]
func isEven(_ i: Int) -> Bool {
return i % 2 == 0
}
let evens = arr.filter(isEven) //[2, 4]

</code></pre>

### Let's Practice

<pre><code>

//my code

let f: (Int) -> Bool = { 
(number: Int) -> Bool in
return number % 2 == 0
} //함수 내부를 구현하세요

let s: (Int, Int) -> Int = { 
(number: Int, otherNumber: Int) -> Int in
var sum = 0
sum = number + otherNumber
return sum
}//함수 내부를 구현하세요

func solution(_ nums: [Int]) -> Int {
return nums.filter(f).reduce(0, s)
}

//other person
let f: (Int) -> Bool = { $0 % 2 == 0 } //함수 내부를 구현하세요
let s: (Int, Int) -> Int = { $0 + $1 } //함수 내부를 구현하세요

func solution(_ nums: [Int]) -> Int {
return nums.filter(f).reduce(0, s)
}

</code></pre>

### My learning: Syntax optimization's remind and need more try
