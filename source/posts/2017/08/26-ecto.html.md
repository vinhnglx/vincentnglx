---
title: Ecto
date: 2017-08-26 02:48 UTC
tags: elixir, ecto
author: "Vincent"
---

When I start to learn and work on Elixir, I really impressive about Ecto.

> Ecto is a database wrapper and language integrated query for Elixir.

My personal feeling is Ecto is not magically like ActiveRecord. For example, Ecto doesn't support Lazy-Load, you need to allow data
to be preloaded into structs. Lazy loading is often a source of confusion and performance issues and Ecto pushes developers to do the proper thing. Sound good, huh?

Ecto also supports a mechanism to help you organize the schema across multiple contexts - break a large schema into smaller ones. Maybe one for reading data,
another for writing. Or one for your database, another for your forms.

And did you know the Plataformatec? They wrote a cool [free Ecto ebook](http://pages.plataformatec.com.br/ebook-whats-new-in-ecto-2-0) and the book will be updated frequently when Ecto release new version.

After few days reading the book below is my summary and of course, from the book, I also had few things don't completely understand. I will deep dive it again in this September.

---

- ORM - O is for Objects. Objects couple state and behavior together. For example, in the `product` object, we have state named `price` and behavior named `purchased?`.
And with Ruby programming language, the code will be: `product.price` and `product.purchased?`

But Elixir fails the "coupling of state and behavior". Behavior in Elixir is always added to modules via functions. Elixir provides structs to help us work with
structured data.

        defmodule Product do
        defstruct [:price, :title]

        def purchased?(product) do
          # Do Sth
        end
      end

The call will be

        product = Product.new(title: "iPhone 8", price: 1000)
      product.price

      Product.purchased?(product)

- ORM - RM is Relational Mapper. Ecto provides schemas that map any data source into an Elixir struct. *When applied to your database, Ecto schemas are relational mapper*


        defmodule Sample.Type do
        use Sample.Web, :model

        schema "types" do
          field :name, :string
          field :desc, :string
          field :slug, :string
          has_many :quotes, Sample.Quote

          timestamps()
        end
      end

As you see, the schema `types` is the place you provide information for fields and set relationship to another model.

And a schema may be end-up with hundreds of fields, relationships - this is a very bad schema. Therefore, it's better to break schema across multiple contexts, this would lead to simpler and clearer solutions.

- Most queries in Ecto are written using schemas. And Ecto 2.0 adds many improvements to schemaless queries - allowing all database operations to be expressed without a schema. They tend to simple queries.

- Ecto supports test factories and we don't need to use a 3-party library for creating factories.

- **Ecto has dynamic queries, allow us to build dynamic expressions that are later interpolated into the query. This feature is quite cool, and I noted here. Will come back to deep dive.**

- Ecto introduces the ability to run queries in different prefixes. Data in different prefixes are isolated. This is really fit when you build multi-tenant application. **One more note to deep dive.**

- Ecto also includes `many_to_many` relationships - **I'm sure will take a look about this in my current side project.**

- The last two things about transaction with Ecto.Multi and Concurrent test with SQL Sandbox - **I will deep dive when I face these problems**


