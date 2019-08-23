
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


# Composition

## Some function's return value used other function's input value

### Sure, some function's return type must equal to other function's input type

<pre><code>
//Example Code

func f1(_ i: Int) -> Int {
return i * 2
}

func f2(_ i: Int) -> String {
return "\(i)"
}

let result = f2(f1(100))

func ff(_ pf1: @escaping (Int) -> Int, _ pf2: @escaping (Int) -> String) -> (Int) -> String {
return { i in
return pf2(pf1(i))
}
}
let f3 = ff(f1, f2)
let result = f3(100)

//use generic
func comp<A, B, C>(_ pf1: @escaping (A) -> B, _ pf2: @escaping (B) -> C) -> (A) -> C {
return { i in
return pf2(pf1(i))
}
}
let f3 = comp(f1, f2)

</code></pre>

### Let's practice

<pre><code>
//my code
func comp<A, B, C>(_ pf1: @escaping (A) -> B,
_ pf2: @escaping (B) -> C) -> (A) -> C {
return { i in
return pf2(pf1(i))
}
}

func filterEven(_ ns: [Int]) -> [Int] {
var temporaryBox: [Int] = []
for number in ns {
guard number % 2 == 0 else { continue }
temporaryBox.append(number)
}

return temporaryBox
//함수를 구현하세요
}

func sum(_ ns: [Int]) -> Int {
//함수를 구현하세요
var result = 0
for number in ns {
result += number
}
return result
}

let filteredSum = comp(filterEven, sum)

func solution(_ nums: [Int]) -> Int {
return filteredSum(nums)
}

//other person
func comp<A, B, C>(_ pf1: @escaping (A) -> B,
_ pf2: @escaping (B) -> C) -> (A) -> C {
return { i in
return pf2(pf1(i))
}
}

func judgeEven(_ num:Int) -> Bool {
return num % 2 == 0
}

func filterEven(_ ns: [Int]) -> [Int] {
//함수를 구현하세요
return ns.filter{judgeEven($0)}
}

func add(_ a:Int, _ b:Int) -> Int {
return a + b
}

func sum(_ ns: [Int]) -> Int {
//함수를 구현하세요
return ns.reduce(0, {add($0,$1)})
}

let filteredSum = comp(filterEven, sum)

func solution(_ nums: [Int]) -> Int {
return filteredSum(nums)
}
</code></pre>

### my learning: I have to develop my sight

# Curring

## Separate function that inputed 2 more parameters

### Purpose :  To easy composition

<code><pre>

func f(_ a: Int, _ b: Int) -> Int {
return a * b
}

func f1(_ a: Int) -> Int {
return a
}
func f2(_ b: Int) -> Int {
return b
}

func multiply(_ a: Int) -> (Int) -> Int {
return { b in 
return a * b
}
}
let area = multiply(10)(20)

</pre></code>

### Let's practice

<pre><code>

//my code
func filterSum(_ ns: [Int], _ n: Int) -> Int {
return ns.filter({ $0 % n == 0 }).reduce(0, +)
}

func filterSum2(_ n: Int) -> ([Int]) -> Int {
var box: Int = 0
return {
(ns: [Int]) -> Int in
for number in ns {
guard number % n == 0 else { continue }
box += number
}
return box
}

}

func solution(_ nums: [Int], _ r: Int) -> Int {
let filteredR = filterSum2(r)
return filteredR(nums)
}

//other person
func filterSum(_ ns: [Int], _ n: Int) -> Int {
return ns.filter { $0 % n == 0 }.reduce(0, +)
}

func filterSum2(_ n: Int) -> ([Int]) -> Int {
return {
return filterSum($0, n)
}
}

func solution(_ nums: [Int], _ r: Int) -> Int {
let filteredR = filterSum2(r)
return filteredR(nums)
}


</code></pre>


### My fault: I did kill FP's strong point. So code is complexed
