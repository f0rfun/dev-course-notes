# Array Methods - High Level Concepts

Map, Filter, and Reduce do not manipulate the original array. You end up with new values.

I'm going to try explaining the 3 methods visually using emojis.

## Map

[🥓, 🍟, 🍤, 🍿].map(origin) => [🐷, 🥔, 🦐, 🌽]

Maps an array of elements through a function to a new value. Given some food e.g. bacon, fries, ebi tempura, popcorn, passing them through a function that maps them to their source gives us pork, potato, shrimp and corn. You get the point.

## Filter

[🍔, ⚽️, 💻, 🥝].filter(isEdible) => [🍔, 🥝]

Filters an array to get just what we want (the filtrate). The filter returns a boolean i.e. filter ? keep : discard.

## Reduce

[🍄, 🥕, 🥚, 🌿, 🍗].reduce(cook) => [🍲]

Reduces an array of items into a single value. We can combine different ingredients and the reduction is a good stew.

## Map or Reduce

On deciding which to use, the intent is key. Use map when you want to **_convert_** a series of inputs into an **_equal length_** series of outputs. Use reduce when you want to **_combine_** a series of inputs into a single output.

In cases where both can produce the same results, prioritize readability assuming negligible differences in performance.
