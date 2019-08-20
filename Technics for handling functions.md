
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
