# Hash Concept Review

## Introduction

Hashes and arrays are similar in many ways.

- They are both _data structures_
- They are **essential** tools for programmers to understand
- They are both used to hold collections of things

They _differ_ in how we find elements in the collection and whether the items
have any ordering mechanism.

## Learning Goals

1.  Recognize hash as a core tool in programming
2.  Recognize hash vocabulary word: Key
3.  Recognize hash vocabulary word: Value
4.  Compare Weakness of Nested Arrays versus a Hash
5.  View a `Hash` in Ruby
6.  Access `Hash` Elements Through Bracket-Notation in Ruby
7.  Create `Hash`es in Ruby

## Recognize Hash as a Core Tool in Ruby

Hashes are an important and commonly used data type. Ruby, Python, and
JavaScript developers use hashes (or something very similar to it) **every
day**.  Take your time and make sure you understand how they work.

Think of hashes like a dictionary. Dictionaries have a unique word that points
to a definition of that word. The word `ant` points to a definition like "a
small insect that likes to ruin picnics" and `anteater` is a unique word that
points to a definition like "a large mammal that likes to eat ants."

## Recognize Hash Vocabulary Word: Key

In a dictionary we lookup a definition by the word. When we look things up in a
hash we call the unique thing we search by the _key_.

## Recognize Hash Vocabulary Word: Value

In a dictionary, when we lookup a definition by the word we get its definition.
When we look things up in a hash based on the key, we get back the _value_ of
that _key_ in the hash.

Unlike a dictionary which uses words as keys, you can use integer, string,
symbol, or even a boolean and array as a key in your hash/dictionary.

## Compare Weakness of Nested Arrays versus a Hash

To recognize the value of using a hash, let's take a look at an example array
that contains 5 different fruits:

```ruby
fruits = ["mango", "papaya", "coconut", "plantain", "dragonfruit"]
```

Let's say that Flatiron Genetic Engineering as now created new colors of these
5 fruits. They sent the new information over to us in the form of a table:

| Fruit      | Color Varieties|
|------------|----------------|
|mango       |orange,red,green|
|papaya      |orange,green|
|coconut     |brown, white|
|plantain    |green,yellow, brown|
|dragonfruit |red, white, black|

Now that we have a list of fruits, what if we wanted to associate more
information with each? We _could_ try to make an array of arrays or "nested
array" work like so:

```ruby
fruits = [
        ["mango", ["orange","red","green"]],
        ["papaya", ["orange","green"]],
        ["coconut", ["brown", "white"]],
        ["plantain",["green","yellow", "brown"]],
        ["dragonfruit",["red", "white", "black"]]
        ]
```

But how would we get the varieties of the `"plaintain"`? We would have to loop
through the array by even-number increments from 0, find the index that matches
the string, add `1` to that index, and get back the array.

Gross.

What we want to say is "Hey hash! Give me the array associated with the
`String` `"plantain"`. Or, more technically, "Hey hash, let me give you a
_key_, please return its corresponding _value_." We'll learn to do that now.

## View a `Hash` in Ruby

Let's assume someone defined our fruit table as a `Hash` in Ruby. They've
assigned it to the constant `FRUITS`. We can print the contents in IRB like so
using the `p` command:

```ruby
2.3.3 :001 > p FRUITS
{"mango"=>["orange", "red", "green"], "papaya"=>["orange", "green"], "coconut"=>["brown", "white"], "plantain"=>["green", "yellow", "brown"], "dragonfruit"=>["fuschia", "white", "black"]}
 => {"mango"=>["orange", "red", "green"], "papaya"=>["orange", "green"], "coconut"=>["brown", "white"], "plantain"=>["green", "yellow", "brown"], "dragonfruit"=>["fuschia", "white", "black"]}
```

As we can see, as `Array`s are surrounded by square-brackets (`[]`), `Hash`es
are surrounded by curly-braces (`{}`). The _key_ is listed and is shown
"pointing to" with an arrow (`=>`) the _value_. So we see that `"mango"` points
to `["orange", "red", "green"]`.

## Access `Hash` Elements Through Bracket-Notation in Ruby

To access the contents of a `Hash` we provide the _key_ in bracket notation
(just like an `Array`).

Thus:

```ruby
FRUITS["dragonfruit"] #=> ["fuschia", "white", "black"]
FRUITS["dragonfruit"][1] #=> "white"
```

## Create `Hash`es in Ruby

Just like `Array`, in Ruby, we can create `Hash`es with a `Hash`-literal format
**or** with a constructor method called `Hash.new`. _Just like with `Array_,
most of the time, when creating a `Hash` from scratch, we prefer the Hash
literal syntax.

### Hash Literal Syntax

Here's your own `fruits` hash:

```ruby
fruits = {
        "mango" => ["orange","red","green"],
        "papaya" => ["orange","green"],
        "coconut" => ["brown", "white"],
        "plantain" => ["green","yellow", "brown"],
        "dragonfruit" => ["fuschia", "white", "black"]
        }
```

Since we're getting comfortable with nested data structures, let's try nesting
our `Hash`es:

```ruby
fruits = {
        "mango" => {
                "colors" => ["orange","red","green"],
                "nutrients" => ["vitamin A", "vitamin B-6", "vitamin C"]
                },
        "papaya"  => {
                "colors" => ["orange","green"],
                "nutrients" => ["vitamin C", "magnesium", "potassium"]
                }
        }
```

> **STRETCH:** Use bracket notation to print out the first nutrient for a
> papaya.

#### Use the `new` Keyword

Unlike `Array`, it's common to use the `Hash.new` constructor method.

```ruby
groceries = Hash.new # OR: groceries = {}
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

### Quick Check

As a stretch, try this code out in your head, and then in IRB:

```ruby
directors = {}
directors.store("Coppola", Hash.new)
directors["Coppola"] = { "Francis Ford" => { "movies" => ["The Godfather", "Apocalypse Now"], "life" => "Guy from Detroit tells the triumph and tragedy of a dream called 'America'"} }
directors["Coppola"]["Sophia"] = {}
directors["Coppola"]["Sophia"]["movies"] = ["Lost in Translation", "Virgin Suicides"]
directors["Coppola"]["Sophia"].store("life", "Tough childhood in the Philippines with her father, tried acting, met Kirsten Dunst and made moody movies")
```

What are the value of these look-ups?

- `directors["Coppola"]["Francis Ford"]["movies"][2]`
- `directors["Coppola"]["Sophia"]["movies"]["life"]`
- `directors["Coppola"]["Francis Ford"]["movies"][1]`
- `directors["Coppola"]["Sophia"]["life"]
``

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
