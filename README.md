# Hash Concept Review

## Introduction

Hashes and arrays are similar in many ways. They are collections of things -
data types. Strings, Numbers, Booleans… or even other hashes and arrays!
However, unlike arrays, hashes can use any data type for the index. All of the
following hashes are valid:

```ruby
hash_with_number_keys = {0 => "hello", 1 => "world"}
hash_with_number_keys[0]
# => "hello"

hash_with_string_keys = { "you say" => "goodbye", "I say" => "hello"}
hash_with_string_keys["you say"]
# => "goodbye"


hash_with_array_keys = { [2,3] => "hi", [4,5] => "world"}
hash_with_array_keys[[4,5]]
# => "world"

hash_with_boolean_keys = { true => "yes", false => "no"}
hash_with_boolean_keys[true]
# => "yes"
```

Arrays, on the other hand, can only use an integer as the index:

```ruby
array = ["hello", "world"]
array[0]
# => "hello"
```

As we will see in this lesson, it turns out that this ability to index however
we like makes the hash a powerful tool!

## Learning Goals

1.  Recognize hash as a core tool in Ruby
2.  Demonstrate hash creation in Ruby

### Recognize Hash as a Core Tool in Ruby

Hashes are an important and commonly used data type. Take your time and make
sure you understand how they work.

Think of hashes like a dictionary. Like a dictionary, hashes contain a
collection of unique keys (words) and values associated with them (definitions).

>     Ruby(key): An awesome programming language (definition)

Unlike a dictionary which uses words as keys, you can use integer, string,
symbol, or even a boolean and array as a key in your hash/dictionary.

> ♕(key): A piece in a chess game (definition).

To recognize the value of using a hash, let's take a look at an example array
that contains 5 different fruits:

```ruby
fruits = ["mango", "papaya", "coconut", "plantain", "dragonfruit"]
```

Now that we have a list of fruits, what if we wanted to associate more
information with each? It would be rather challenging to add in and access
specific pieces of information to this array. The nested arrays would become
complex and cumbersome, and accessing the information would require knowing
the index for each:

```ruby
fruits = [
        ["mango", ["orange","red","green"]],
        ["papaya", ["orange","green"]],
        ["coconut", ["brown", "white"]],
        ["plantain",["green","yellow", "brown"]],
        ["dragonfruit",["red", "white", "black"]]
        ]
```

In a hash, this information could be organized much more neatly as such:

```ruby
fruits = {
        "mango" => ["orange","red","green"],
        "papaya" => ["orange","green"],
        "coconut" => ["brown", "white"],
        "plantain" => ["green","yellow", "brown"],
        "dragonfruit" => ["fuschia", "white", "black"]
        }
```

The value for each fruit can now be accessed by its key:

```ruby
puts fruits["coconut"]
=> ["brown", "white"]

puts fruits["dragonfruit"]
=> ["fuschia", "white", "black"]
```

And if we wanted to add _two_ sets of associated data to our fruit:

```ruby
fruits = {
        "mango" => {
                "colors" => ["orange","red","green"],
                "nutrients" => ["vitamin A", "vitamin B-6", "vitamin C"]
                },
        "papaya"  => {
                "colors" => ["orange","green"],
                "nutrients" => ["vitamin C", "magnesium", "potassium"]
                },  
        etc...
        }
```

We can access the value of each set of keys like so:

```ruby
puts fruits["mango"]["colors"]
=> ["orange", "red", "green"]

puts fruits["papaya"]["nutrients"]
=> ["vitamin C", "magnesium", "potassium"]
```

Since we can use Strings as hash keys, we use keys to describe what their values
are, making it much easier to understand and access data.

#### Order Does Not Matter

Another benefit of hashes is that order of key value pairs does not matter. Back
in our array of fruits and fruit colors, if we want to access color information
for a particular fruit, say `"coconut"`, we either need to know its position or
find it by iterating over the array:

```ruby
fruits = [
        ["mango", ["orange","red","green"]],
        ["papaya", ["orange","green"]],
        ["coconut", ["brown", "white"]],
        ["plantain",["green","yellow", "brown"]],
        ["dragonfruit",["red", "white", "black"]]
        ]

fruits[2][1]
# => ["brown", "white"]
```

If a new fruit was added to the beginning of this array, suddenly,
`fruits[2][1]` no longer refers to `["coconut", ["brown", "white"]]`. But
with a hash, keys can be in any order:

```ruby
fruits = {
        "mango" => {
                "colors" => ["orange","red","green"],
                "nutrients" => ["vitamin A", "vitamin B-6", "vitamin C"]
                },
        "coconut"  => {
                "colors" => ["brown","white"],
                "nutrients" => ["vitamin C", "magnesium", "potassium"]
                },  
        etc...
        }

fruits["coconut"]["colors"]
# => ["brown", "white"]
```

Being able to simply state `fruits["coconut"]["colors"]` is clear and direct.

#### Instant Look Up

When handling large sets of data, the ability look up hash values by key
actually provides a boost in performance.

Imagine an array of _all_ fruits, vegetables, grains, etc... We don't know where
particular fruit are positioned within the array so we can't just type
`fruits[2][1]`. Instead, we need to iterate over the array and look for matches:

```ruby
fruits.find {|fruit| fruit[0] == "coconuts"}
# => ["coconut", ["brown", "white"]]
fruits.find {|fruit| fruit[0] == "coconuts"}[1]
# => ["brown", "white"]
```

Having to use `find` on a large array means looking at _every_ item in the array
until there is a match. The length of the array determines how long it takes to
find something in it.

In a hash, if we know the key, we can instantly find what we need every time, no
matter how big or small the entire hash is:

```ruby
fruits["coconut"]["colors"]
# => ["brown", "white"]
```

### Demonstrate Hash Creation in Ruby

Now that we know the basics of what hashes are capable of, let's look at
how we can create them!

Hashes can be created in 2 relatively straight-forward ways:

#### Use the `new` Keyword

```ruby
groceries = Hash.new
groceries[1] = "potatoes"
groceries[2] = "onions"
groceries[3] = "eggs"

puts groceries
# => {1=>"potatoes", 2=>"onions", 3=>"eggs"}
```

The `store` keyword can also be used to add values to the new hash in place of
square brackets `[]`.

```ruby
groceries = Hash.new
groceries.store(1, "potatoes")
groceries.store(2, "onions")
groceries.store(3, "eggs")

puts groceries
# => {1=>"potatoes", 2=>"onions", 3=>"eggs"}
```

When you store a value in a hash, you supply two objects - the index (also
called the key) and the value.

#### Use the Hash Literal

A hash can also be created using literal notation. You can initialize an empty
hash similarly to `Hash.new` by setting a variable to an empty set of curly
braces `{}`.

```ruby
states = {}
```

A hash can be created with shorthand by passing in key value pairs.

```ruby
states = {
    "AL" => "Alabama",
    "AK" => "Alaska",
    "AZ" => "Arizona",
    "AR" => "Arkansas"
}

puts states
# => {"AL" => "Alabama", "AK" => "Alaska", "AZ" => "Arizona", "AR" => "Arkansas"}
```

You can retrieve the value by indexing the hash with the same key. The values in
a hash can be objects of any type.

## Conclusion

Hashes are a universal programming concept that are great for faster, simpler
data access. While arrays are used for any sequence of things that need to be in
order, hashes are used to map or associate information you want to store to
keys. They can be seen as "look up tables," like a dictionary or glossary.
Hashes can be created by initializing a new hash with the `.new` method or an
empty hash with `{}` and assigning values to keys with the bracket notation,
`.store`, or with the literal `=>`. Now we can retrieve different types of data
objects much more easily!

## Resources

- [Ruby Hash class]

[ruby hash class]: https://docs.ruby-lang.org/en/2.0.0/Hash.html
