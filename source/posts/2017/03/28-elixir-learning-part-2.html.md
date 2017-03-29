---
title: Elixir Learning Part 2
date: 2017-03-28 14:18 UTC
tags: elixir
author: Vincent
---

### Import and Alias

To call a function from another module, you have to reference the module name, sometime this can be cumbersome. If your module often calls functions
from another module, let's use `import` other module into your own.


        defmodule User do
        import IO

        def name do
          puts "Vincent"
        end
      end

      User.name # Hello Vincent

- You can import multiple modules.

- An alternative to import is `alias` to reference a module under a different name


          defmodule User do
          alias IO, as: Alien

          def name do
            Alien.put "Vincent"
          end
        end

        User.name # "Vincent"

- Alias will useful if a module has a long name.

### Module attributes

- Module attributes can be used as compile-time `constants`. The constant exists only during the compilation of the module.

          # circle.ex
          defmodule Circle do
          @pi 3.14159

          def area(r) do
            r*r*@pi
          end
        end

        Circle.area(4) # 4 * 4 * 3.14159 = 50.26544

- Generate a compiled file by command: `elixirc circle.ex`, then start `iex` shell from the same folder. From `iex` shell, call `Circle.area(4)`


### Atom

- Atoms are literal named constants. Similar to symbols in Ruby, for example: `:an_atom`, `:user_name`

- Another syntax for Atom constants start with uppercase: `Abcd`. This is called an `alias`. When you use an alias, the complier implicitly addes the `Elixir` as a prefix. `Abcd == Elixir.Abcd`

- One important thing, Elixir doesn't have a dedicated boolean type - `:true == true`. This mean a boolean is just an atom that has value of true or false.

- Another special thing is `nil`. Nil is also an atom - `nil == :nil`

          nil || false || 3 # 3
          nil || true # true
          3 || nil # 3

          3 && nil # nil
          nil && 3 # nil

### Tuples

- Tuples are used to group a small, fixed number of elements together.

          user = { "Vincent", 27, "Software Developer" }

### List

- List are used to manage dynamic, variable-sized collections of data.

          user = [1,2,3,4,5, "Vincent"]

- The complexity of operations on list have an O(n).

- **NOTE** You should avoid adding elements to the end of a list. The reason in below section

### Recursive list definition

- An alternative way of looking at lists is to think of them as recursive structures. A list can be represented by a pair (`head`, `tail`), where `head`
is the first element of the list and `tail` points to the pair of remaining elements

- There is special syntax to support recursive list definition.

        a_list = [head | tail]

- So for example we have a list `[1,2,3,4,5]` then the construct can be write:

        a_list = [1 | [2 | [3 | [4 | [5 | []]]]]]
        # [1,2,3,4,5]

**That's why we SHOULD NOT add elements to the end of a list.**

- Use `hd` to get the head of a list and `tl` to get the tail of a list.

          list = [1,2,3,4]
        hd(list) # 1
        tl(list) # [2,3,4]

Or

            [a | b] = list
          a # 1
          b # [2,3,4]

- How we push new element to the top of the list

          list = [1,2,3,4]
        new_list = [0 | list]
        # [0,1,2,3,4]

**NOTE:**

- Data in Elixir is immutable and you can't do an in-memory modification of a value.
- You need to store its result to another variable or rebound.

