### General

To call methods directly on a class (as opposed to calling them on an instance of a class), you should define them with either a `self.` prefix in their name after the `def` keyword, or put the method definition between `class << self` and `end`:

```ruby
def self.method_name
end
```
```ruby
class << self
  def method_name
  end
end

```

### 1. Calculate the interest rate

- Using an if or case statement can be useful when checking conditions.

### 2. Calculate the annual balance update

- When calculating the annual yield, it might be useful to temporarily convert a negative balance to a positive one. The `Float` class has a method to convert both positive and negative values to their absolute value.

### 3. Calculate the years before reaching the desired balance

- To calculate the years, one can keep looping until the desired balance is reached.
- Ruby has no increment operator (`i++`) like some other languages do. Instead, constructs like `i += 1` (which is equal to `i = i + 1`) can be used.
