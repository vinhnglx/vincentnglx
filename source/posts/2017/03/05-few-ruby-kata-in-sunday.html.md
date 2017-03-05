---
title: Few Ruby Katas in a rainy day
date: 2017-03-05 10:00 UTC
tags: Ruby, Kata
author: Vincent
---

In a rainy Sunday, I have solved three katas.

### Kata #1

*Return the first longest string consisting of k consecutive strings taken in the array*

*Example:*

      longest_consec(["zone", "abigail", "theta", "form", "libe",
    "zas", "theta", "abigail"], 2) # "abigailtheta"

I solved this kata with a helping from [each_cons](https://ruby-doc.org/core-2.1.0/Enumerable.html#method-i-each_cons) method.
A method belongs to Enumerable in Ruby.

*The code will be:*

      def longest_consec(strarr, k)
      strarr_length = strarr.length
      return "" if strarr_length == 0 || k > strarr_length || k <= 0
      return strarr.each_cons(k).map {|el| el.join("") }.max_by(&:length)
    end

### Kata #2

*Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed
Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.*

*Example:*

      spin_words("Hey fellow warriors") # "Hey wollef sroirraw"
    spin_words("Hello world. My name is Vincent") # olleH .dlrow My name is tnecniV

This kata is quite easy to solve. Basically, I just split the string into an array of words and reverse words that have more than 5 letters.
Then I will convert that array of words to string.

*The code will be:*

      def spin_words(string)
      string.split(" ").map {|el|
        if el.length >= 5 then el.reverse else el end}.join(" ")
    end

### Kata #3

*A string is considered to be in title case if each word in the string is
either (a) capitalised (that is, only the first letter of the word is in
upper case) or (b) considered to be an exception and put entirely into
lower case unless it is the first word, which is always capitalised.*

*Write a function that will convert a string into title case, given an
optional list of exceptions (minor words). The list of minor words will
be given as a string with each word separated by a space. Your function
should ignore the case of the minor words string -- it should behave in
the same way even if the case of the minor word string is changed.*

*Example:*

      title_case('a clash of KINGS', 'a an the of') # A Class of Kings
    title_case('THE WIND IN THE WILLOWS', 'The In') # The Wind in the Willows
    title_case('the quick brown fox') # The Quick Brown Fox

If the minor_words option is null then we will capitalize each word in this input string.
If there is minor_word option then we only capitalize words that don't inside the minor_word list.
In addition, we always capitalize the first word of string.

*The code will be:*

      def title_case(title, minor_words = '')
      if minor_words.empty?
        title.split(" ").map(&:capitalize).join(" ")
      else
        minor_arr = minor_words.split(" ").map(&:downcase)
        first_el, *rest_el = title.split(" ").map(&:downcase)
        rest_el.map {|el| unless minor_arr.include?(el) then el.capitalize else el end}.unshift(first_el.capitalize).join(" ")
      end
    end

Thanks for reading!
