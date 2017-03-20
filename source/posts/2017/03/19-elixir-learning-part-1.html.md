---
title: Elixir Learning Part 1
date: 2017-03-19 03:27 UTC
tags: elixir
author: Vincent
---

Yo! It's time to start learning new languages. Elixir is a language that I started to learn. Below are few notes:

- Everything in Elixir is an expression that has a return value.

- Module is a collection of functions, something like a namespace. Every Elixir function must be defined inside a module.

    - To call a fucntion of a module, use the syntax : `ModuleName.function_name(args)`
    - To define your own module, use the `defmodule` contruct.
    - Inside the module, using `def` contruct to define function.
    - `defmodule` and `def` are compilation constructs called **macros**


            defmodule Geometry do
            def rectangle_area(a, b) do
              a * b
            end
          end

    - A module name must follow certain rules: start with an uppercase letter and is usually written in *CamelCase* style.

- Function must always be a part of a module. Function name start with lowercase letter and underscore character.

    - Function names can end with `?` or `!`
        - `?` means a function returns true of false
        - `!` means a function may raise a runtime error
    - If a function has no arguments then we can omit parentheses.

- To combine functions, passing the result of one function as the argument to the next one. Elixir comes with a built-in operator: `|>` - pipeline operator

            iex(2)> -5 |> abs |> Kernel.+(6)
          11

- Arity is a fancy name for the number of arguments a funciton receives.

              defmodule Greeting do
              def say_hi(name) do
                # ...
              end
            end

    - The function Greeting.say_hi receives one argument so function arity is 1.
    - This function is often called `Greeting.say_hi/1`

- **Two functions with the same name but different arities are two different functions.**

              defmodule Geometry do
              def area(a, b) do # Arity: Geometry.area/2
                a * b
              end

              def area(a) do # Arity: Geometry.area/1
                area(a, a)
              end
            end

            # Geometry.area(5) # => 25
            # Geometry.area(3,4) # => 12

   - It usually make no sense for different functions with a same name to have completely different implementations.
   - In general, a lower-arity function delegates to a higher-arity function.
   - Elixir allows you to specify defaults for argument by using the `\\` operator.

            defmodule Geometry do
            def sum(a, b \\ 0)
              a + b
            end
          end
          # Geometry.sum(5) # => 5
          # Geometry.sum(4,6) # => 10

- Using `def` macro when define a function, the function is made public. Using `defp` macro to make the function private.
