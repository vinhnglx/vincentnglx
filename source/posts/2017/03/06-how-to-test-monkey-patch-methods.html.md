---
title: How to test monkey-patch methods?
date: 2017-03-06 14:52 UTC
tags: Ruby
author: Vincent
---

I won't explain what's Monkey-patch, many developers knew about it.

In Ruby, we can create and test monkey-patch methods like the code below:

        module StringExtensions
        # Number of words in a string
        def word_count
          self.split.size
        end
      end

      describe String do
        before do
          String.include StringExtensions
        end

        describe "#word_count" do
          it "returns number of words in a string" do
            expect("Hell yeah".word_count).to eq 2
            expect("Hello world! I'm Vincent".word_count).to eq 4
          end

          it "returns zero if a string is empty" do
            expect("".word_count).to eq 4
          end
        end
      end

Personally, I don't like monkey-patch, we can create a Word class for methods relate to words in a string.
But you know, sometimes we have to monkey-path so this is one way we can apply.

Thanks for reading!
