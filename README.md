# Hash Concept Review

## Introduction

Hashes and arrays are similar in that they are indexed collections of object
references. However, unlike arrays, hashes can use _any_ object as an index,
while the index of arrays are always defined by integers. The hash index can
be objects of any type--integer, strings, symbols, and others.

## Learning Goals

1.  Recognize hash as a core tool in Ruby
2.  Demonstrate hash creation in Ruby

### Recognize Hash as a Core Tool in Ruby

Hashes are an important and commonly used data type. Think of hashes like a
dictionary that contain a collection of unique keys and values associated
with them. That means you can use integer, string, symbol, or even a boolean
and array as a key in your hash/dictionary.

Let's start with an array that contains 5 different fruits.

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

Now that we know the basics of what hashes are capable of, let's look
at how we can create them!

### Demonstrate Hash Creation in Ruby

Hashes are powerful collections with many methods that programmers can use to
create them. Hashes can be created in 2 relatively straight-forward ways:

#### Use the `new` Keyword

```ruby
groceries = Hash.new
groceries[1] = "potatoes"
groceries[2] = "onions"
groceries[3] = "eggs"

//puts groceries
//{1=>"potatoes", 2=>"onions", 3=>"eggs"}
```

The `store` keyword can also be used to add values to the new hash in place of
square brackets `[]`.

```ruby
groceries = Hash.new
groceries.store(1, "potatoes")
groceries.store(2, "onions")
groceries.store(3, "eggs")

//puts groceries
//{1=>"potatoes", 2=>"onions", 3=>"eggs"}
```

When you store a value in a hash, you supply two objects - the index (also
called the key) and the value.

#### Use the Hash Literal

A hash can also be created using literal notation. You can initialize an empty
hash similarly to `Hash.new` by setting a variable to an empty set of curly braces `{}`.

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

//puts states
//{"AL" => "Alabama", "AK" => "Alaska", "AZ" => "Arizona", "AR" => "Arkansas"}
```

You can retrieve the value by indexing the hash with the same key. The values in
a hash can be objects of any type.

## Conclusion

## Resources
