---
title: "Build Your Own Portfolio!"
slug: build-your-own-portfolio
---

#Get started with HTML
Alright, let's get started. We will use the popular text editor Sublime Text 3 to create our files and the Chrome browser to inspect our files and run the portfolio.

You can use any text editor you feel comfortable with, for example the Atom editor, WebStorm or just your simple old NotePad or TextEdit. It really depends on your own preference and what you want from your text editor.

Let’s start by making a folder on your computer and name it **portfolio**. Inside it, let’s create an HTML file and name it **index.html**. Depending on your text editor, specifying a file with **.html** will color the syntax while you are writing the code, which makes it easier to read and work with.

> [info]
> **To boilerplate or not to boilerplate?**
> 
> This is an interesting debate or actually it was. Nowadays, it's good practice to use the [HTML5 boilerplate template](https://html5boilerplate.com/) because it adds tons of good practice into your site from the start. But don't believe me, read about it [here](http://stackoverflow.com/questions/15453299/html5-boilerplate-and-twitter-bootstrap). 
> We won't use it in this project because we are just working on a very small peronal project and won't have the time to go into too much detail about the exact details of the boilerplate but on your next project, you really should!

#Creating your first HTML page
> [action]
> Let’s create the basic outline of an HTML file. An HTML file consists of HTML tags and needs at > least the following:> 
> 
> ```
> <html>
>     <head>
>         ...
>     </head>
> 
>     <body>
>         Hello World!
>     </body>
> </html>
> ```

These simple tags are enough to display our well known *Hello World* in the browser. Save your file and open the index.html file in the browser to make sure that everything worked as expected.

You should see something like this:

![index.html in the browser](./2-index-in-browser.png "index.html in the browser")

Do you spot the index.html title in the tab of the browser? 

> [action]
> Let's change that to something more appropriate like "MakeSchool's Portfolio" - you should change this to something that reflects your name, username or anything else that you want to showcase.
>
> We can do this by adding the `<title>` tag to the `<head>` tag, which is responsible for the name of your website.
> 
> ```
> <head>
>     <title>Make School's Portfolio</title>
> </head>
> ```

Have a look and see how the title changed.

![New title for website](./3-title.png "New title for website")

OK, now let's get started in earnest. We want to put some information onto the portfolio that shows who we are and what work we have done, so we need to add some information about us.

#HTML tags
There are some great new HTML5 additions, that make adding components to a website quite self explanatory. Here are a few tags that can be used to add components:

- `<article>`  Represents an independent piece of content of a document, such as a blog entry or newspaper article.
- `<audio>`  Defines an audio file.
- `<footer>`  Represents a footer for a section and can contain information about the author, copyright information, et cetera.
- `<header>`  Represents a group of introductory or navigational aids.
- `<nav>`  Represents a section of the document intended for navigation.
- `<section>`  Represents a generic document or application section.

Some of the tags from HTML versions before that are also great to know are the following tags:

- `<button>`  Represents a clickable button.
- `<div>`  Is the generic container for flow content, which does not inherently represent anything. It can be used to group elements for styling purposes or because they share attribute values. It should be used only when no other semantic element (such as <article> or <nav>) is appropriate.
- `<h1> ... <h6>`  Heading elements implement six levels of document headings, `<h1>` is the most important and `<h6>` is the least. A heading element briefly describes the topic of the section it introduces.
- `<img src="a_url_to_somewhere" />`  Represents an image in the document. It is a self closing tag and has no closing tag. Note the backslash.
- `<li>`  Is used to represent an item in a list. It must be contained in a parent element: an ordered list (`<ol>`), an unordered list (`<ul>`), or a menu (`<menu>`).
- `<ol>`  Represents an ordered list of items. Typically, ordered-list items are displayed with a preceding numbering, which can be of any form, like numerals, letters or Romans numerals or even simple bullets.
- `<p>`  Represents a paragraph of text.
- `<span>`  Is a generic inline container for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes for example.
- `<ul>`  Represents an unordered list of items, namely a collection of items that do not have a numerical ordering, and their order in the list is meaningless. 

> [info]
> A full list of all existing HTML elements with their explanations can be found at [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element). An excellent source for any web related questions you might have.

<!-- Comment to break actionable boxes. -->

> [action]
> Look at the picture above and think about which HTML tags should be used to add the content on the page. Don't worry about the styling for now, just get all the content on the page for now.

#Adding the content section by section
It would be easiest to think of the website in sections. The top section of the page will contain the navigation to other pages. 

> [action]
> The top section should contain a header tag with a nav tag inside. The nav tag should contain an unordered list and each list item should contain a link tag. An anchor tag (or a tag) contains the href attribute that links to a specific page. We will keep those blank for now as we don't have another page to link to yet. 
> Example of an a tag: `<a href="#">Link</a>`
> See if you can come up with your own header section.

<!-- Comment to break up actionable boxes. -->

> [solution]
> This is what the HTML should roughly look like:
>```
>    <header>
>      <nav>
>          <ul>
>              <li><a href="#">Home</a></li>
>              <li><a href="#">Gallery</a></li>
>              <li><a href="#">Contact</a></li>
>          </ul>
>      </nav>
>    </header>
>```

Before adding the middle section, let's focus on the bottom as it has only two additions to the page. 

> [action]
> The bottom section will contain the title for the bottom section and the "Download My CV" button. Try coming up with a structure for the footer.

<!-- Comment to break up actionable boxes. -->

> [solution]
> The bottom section should contain the footer tag and within it, the title of the section as well as the button to download the CV.
>```
>    <footer>
>        <h3>About</h3>
>        <button>Download My CV</button>
>    </footer>
>```

Already two-thirds of the way there with our HTML structure. Now, let's add the middle section, which will contain our main content.

> [action]
> The middle section contains our head image (don't worry about the circle shape yet), a logo and a couple of catchy phrases that bring attention to the page. 

<!-- Comment to break actionable boxes. -->

> [solution]
> Our head image and our logo should of course be in <img> tags. The two phrases could be in h1 and h2 tags to achieve a hierarchy of the two phrases.
>```
>    <section>
>        <img src="https://goo.gl/RG3GtK" />
>        <img src="http://placekitten.com/g/600/600" />
>        <h1>Hello I'm Kitty</h1>
>        <h2>I love creating code</h2>
>    </section>
>```

When you have finished adding your content to the page, refresh the browser and make sure all your content shows up in a similar fashion as the image below. 

![Portfolio without CSS](./4-content-without-style.png "Portfolio without CSS")

Now that we have all of our content there, you can see that it is in dire need of some styling. We want to make sure that our styling looks good on mobile as well as desktop, so we will style it with resizability in mind.

> [solution]
> The entire HTML file should look like this now:
>```
>    <html>
>        <head>
>            <title>Make School's Portfolio</title>
>        </head>
>    
>        <body>
>            <header>
>                <nav>
>                    <ul>
>                        <li><a href="#">Home</a></li>
>                        <li><a href="#">Gallery</a></li>
>                        <li><a href="#">Contact</a></li>
>                    </ul>
>                </nav>
>            </header>
>    
>            <section>
>                <img src="https://goo.gl/RG3GtK" />
>                <img src="http://placekitten.com/g/600/600" />
>                <h1>Hello I'm Kitty</h1>
>                <h2>I love creating code</h2>
>            </section>
>    
>            <footer>
>                <h3>About</h3>
>                <button>Download My CV</button>
>            </footer>
>        </body>
>    </html>
>```
    