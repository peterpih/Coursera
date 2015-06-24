
```
<variable>.each do |x|
end
```

**SYMBOLS**
```
.to_s
.to_sym
.intern
```
```
:<symbol>
:<symbol>.to_s      converts to a string
"<string>".to_sym   converts to a symbol
```
```
strings = ["HTML", "CSS", "JavaScript", "Python", "Ruby"]
# Add your code below!
symbols = []   # initialize array
strings.each do |x|
    symbols.push(x.to_sym)
end
```
```
# pre Ruby 1.9
movies = {
    :a => "a",
    :b => "b",
}

# post Ruby 1.9
movies = {
    a: "a",
    b: "b",
}
```

**Timing Example**
```
require 'benchmark'

string_AZ = Hash[("a".."z").to_a.zip((1..26).to_a)]
symbol_AZ = Hash[(:a..:z).to_a.zip((1..26).to_a)]

string_time = Benchmark.realtime do
  100_000.times { string_AZ["r"] }
end

symbol_time = Benchmark.realtime do
  100_000.times { symbol_AZ[:r] }
end

puts "String time: #{string_time} seconds."
puts "Symbol time: #{symbol_time} seconds."
```
