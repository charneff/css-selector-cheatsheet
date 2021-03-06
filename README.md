# css-selector-cheatsheet

We use CSS selectors in order to grab elements from the html. We use this with scraping, with styling with CSS, and later on with Javascript. Here's a cheatsheet of what kind of selectors we can use.

## The element selector

If we have one h2 or more like:
```
<h2>This is an h2</h2>
<h2>This is also an h2</h2>
```

Then we can grab every h2 element by using the element selector:
```
h2
```

We basically just reference the element we want to select. Take note, using the element selector will select all of the h2s. If you want some of the h2s, you may have to combine the element selector with a class selector or id selector.

## The id selector

Ids in html are usually given as a unique attribute. Meaning only one html element should have that specific id.

If we have an element like:
```
<p id="greeting">Hello!</p>
```

Since it has an id attribute, we can grab it with the id selector:
```
#greeting

or we can combine it with an element selector

p#greeting 

this will give us a p element with the id of greeting
```

## The class selector

Classes unlike ids are can be given to multiple elements. So when we select elements with classes, we could be selecting all of them that matches our selector.

For example, we want all the paragraphs with the class of content
```
<p class="content">Some content</p>
<p class="content">Some other content</p>
```

We could grab those elements with:
```
.content

or more specifically

p.content
```

When using `.content` we have to be very careful. If we only want the paragraphs with .content we need to mix it with an element selector. For example:

If we had these elements:
```
<h1 class="content">H1 Content</h1>
<p class="content">P Content</p>
```

And we used this selector:
```
.content
```

We would end up selecting both the h1 and the p elements. Be cautious and be specific with your selectors.

One addition to class selectors, if we have elements with multiple classes that we want to select:
```
<p class="content main-content">This is a p element with two classes</p>
```

We can be even more specific by chaining with our selectors
```
p.content.main-content
```

This is saying that we want the p element with the class of content and the class of main-content.

## Nested Elements

What if we want an h1 inside specific divs. The divs might have an id, however the h1 may not. On top of this, we don't want every h1 in the document. For example:
```
<div id="main-content">
  <h1>Welcome to the page!</h1>
</div>
```

How can we make sure only to grab this specific h1? We can use a child selector like:
```
div#main-content h1
```

Notice the space after `div#main-content`. This is us saying we want to go into the `div#main-content` and grab the `h1` inside. There is no limit as how far you can go nested. Example:

```
 div#main-content div.product-desc h1.header.title
```

This would be us saying go into `div#main-content`, access every `div.product-desc` and access every `h1.header.title` in each of the `div.product-desc`. For scraping this would be bad. We would have an array of elements with our titles. However we'd most likely just want `div.product-desc` if it contains information for each one of our products.

## Scraping

A pro tip while scraping, when first selecting the elements you are wanting to scrape. Make sure that each element you are scraping contains all the information you want. So if you want a name / blend of coffee and maybe a link for more details. Then grab the element that contains that information. If you do it correctly, you'll have an array elements and each element will have the information inside. That will allow you to iterate through the data and create your objects based on that data.
