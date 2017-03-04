---
title: How to scrape a web page to find duplicate contents
image:
date: 2017-03-03 15:40 UTC
tags: Ruby, Scrape
author: Vincent
---

I recently tried to submit my job application to a few companies, unfortunately, I still can't get hired but I passed some rounds
for technical test. This post is a technical test from a company in Singapore, they want to me write a tool to
find duplicated contents from their website.

From the requirement, you will know we need to write a scraping tool and an algorithm to find duplicated contents.
So this post will have two sections: *how to scrape a site* and *how to find duplicated contents*?

## How to scrape a site

We will open any website, for example, [Viki](https://www.viki.com). At the first glance, you will find the problem.

![Viki - Homepage](https://docs.google.com/uc?id=0B-S3PHiYZOY1S0otclJ0OHFOckk)

We can say: Contents are considered duplicate if they had the same URL, title, and image_src.

What's next step? Will we write a code to parse HTML contents?

No, we need to check again because you know, a famous site like Viki, I don't believe they only use one way to render contents.

So, what should I do? Okay - We will the javascript on this website to find which contents will be rendered by Javascript. Wait!!! Perharps some people will ask me why I do that? Why I disable javascript?

My answer is very simple, trust me, because this will directly affect the way you will scrape the site!

So, this is a screenshot after I turned off Javascript

![Viki - After disabled JS - Homepage](https://docs.google.com/uc?id=0B-S3PHiYZOY1Y3pjanhsSFJXbk0)

There is a difference between these images - You can't find the **"TOP PICKS FOR YOU"** section in the screenshot that I disabled Javascript.
This mean maybe this section is rendered from AJAX call by using Javascript.

Next step, we will use Chrome Developer Tool to find the common HTML structure of these duplicated contents.

![Viki - Inspect common html structure](https://docs.google.com/uc?id=0B-S3PHiYZOY1Szl5a0V5UG96aHM)

These elements has common class `"thumbnail js-express-player"` and structure inside `<div class="thumbnail-wrapper"></div>`, `<div class="thumbnail-description"></div>`.
We will parse to get html contents based on these classes.

Here is the final decision: AFTER the page finished loading contents, we will crawl the site, parse the HTML contents.

My favorite language is Ruby - and in Ruby, I can use [open-uri](https://ruby-doc.org/stdlib-2.1.0/libdoc/open-uri/rdoc/OpenURI.html)
or few gems such as [nokogiri](http://www.nokogiri.org/), [mechanize](https://github.com/sparklemotion/mechanize) to crawl and parse HTML contents.

But we want to parse the content that AJAX loads its, hence these gems can't handle it.
In this case, we can use [Selenium-Webdriver](https://github.com/SeleniumHQ/selenium/wiki/Ruby-Bindings) with a headless webkit - [PhantomJS](https://github.com/ariya/phantomjs) to crawl the page and [Nokogiri](https://github.com/ariya/phantomjs) to parse.

Basically the code will be:

      @driver = Selenium::WebDriver.for(:phantomjs)
    @driver.navigate.to('https://www.viki.com')

After that, we will use Nokogiri to parse HTML contents

      page_source = Nokogiri::HTML(@driver.page_source)
    body = page_source.css('.thumbnail.js-express-player')

As I said before, we will parse title, url and image_src and these will be located on an object: `{title: "...", image_src: "...", url: "xxx"}`.
Hence the code will be:

      body.map {|element|
      {
        "title" => element.css('.thumb-title').text.strip,
        "image_src" => element.css('.thumbnail-img img').attribute('src').text,
        "url" => element.css('.thumbnail-img').attribute('href').text
      }.to_s
    }

When we get a list of objects then we are ready to go to step two: Find the duplicated contents from this list.

## How to find duplicated contents

We had the array of objects so how to find identical objects in array? We implement a loop and compare one by one to find the identical object?
Huh, that's solution will work but the Big O notation is **O(n^2)** - the code will run very slow.

So what's the better solution? Did you remember the [MD5 algorithm](https://en.wikipedia.org/wiki/MD5)? The MD5 algorithm is a widely used hash function producing a 128-bit hash value.
It can be used as a checksum to verify data integrity.

In this case, I need a cryptographic hash that takes content and returns a fixed bit string. Objects have the same content will be grouped with identical hash.

Ruby have a library called [Digest/MD5](https://ruby-doc.org/stdlib-2.1.0/libdoc/digest/rdoc/Digest.html) can help me encrypt.

Below is my code sample, the final result is hash contains identical objects, and of course the Big O notation is **O(n)**:

      hash = {}
    raw.each do |el|
      key = Digest::MD5.hexdigest(el).to_sym
      hash.has_key?(key) ? hash[key].push(el) : hash[key] = [el]
    end

    hash.delete_if { |key, value| value.size == 1 }

## Conclusion

From this technical test, I develop a tool can extend to find duplicated contents from many websites. Source code available at [vinhnglx/dupco](https://github.com/vinhnglx/dupco)
