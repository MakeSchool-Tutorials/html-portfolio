---
title: "Adding a Gallery"
slug: js-gallery
---     

#What is JavaScript?
JavaScript is a programming language used to make web pages interactive. It runs on your visitor's computer and doesn't require constant downloads from your website. JavaScript support is built right into all the major web browsers, including Internet Explorer, Firefox and Safari. Provided that the visitors to your site are using web browsers that support JavaScript (most do) and have JavaScript enabled (it is by default), then your JavaScript will run when they visit the page.

JavaScript is an interpreted language, so no special program is required to create usable code. Any plain text editor such as Notepad or TextEdit is quite satisfactory for being able to write JavaScript. That said, an editor like Sublime or Atom that colorizes the code to make it easier to see what is what makes it easier to find your mistakes.

> [info]
> **Are JavaScript and Java related?**
>
> ![Java vs JavaScript](./2-hamster.jpg "Source: http://www.smashingmagazine.com/2009/07/misunderstanding-markup-xhtml-2-comic-strip/") 
> 
> No, they are two completely different computer languages. Only their names are similar. There's a [wonderful answer on StackOverflow](http://stackoverflow.com/questions/245062/whats-the-difference-between-javascript-and-java) to explain it. 

##Details of the language
JavaScript is case-sensitive and uses the Unicode character set.

In JavaScript, instructions are called statements and are separated by a semicolon (;). Spaces, tabs and newline characters are called whitespace. The source text of JavaScript scripts gets scanned from left to right and is converted into a sequence of input elements which are tokens, control characters, line terminators, comments or whitespace. ECMAScript also defines certain keywords and literals and has rules for automatic insertion of semicolons (ASI) to end statements. However, it is recommended to always add semicolons to end your statements; it will avoid side effects.

More information about JavaScript can be found on [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types), which will explain declarations, variables, data types and literals.

#What is jQuery?
Best described by the website itself: *jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers.* 

jQuery is a library written in JavaScript that makes developing in JavaScript easier and has thus become a very popular library (see below info box for more information). 

> [info]
> **jQuery or vanilla JS?**
> 
> There was a time when not all browsers were equal... a nifty "little" library called jQuery came along and attempted to deal with all the inconsistencies by letting the library deal with the different ways things were supported. Instead of having the developer trying to work out how different features in JavaScript would have to be implemented in Internet Explorer and Firefox and Chrome and Opera and and ..., the library knew how to deal with any inconsistencies and the developer could just go ahead and add their great features.
> 
> But then JavaScript evolved. It became better supported in browsers and inconsistencies started to disappear. People wondered if it was still necessary to use jQuery as many things could now be done natively in JavaScript. The advocates of vanilla JS were pushing for reducing the dependency of a library in favor of implementing things in pure JavaScript. There are still many things that jQuery can help with and it is still a widely used library but it isn't as vital anymore as it used to be. Especially for smaller projects that do only trivial things like selecting elements to then do something with them, it now seems overkill to use jQuery.  
>
> For our portfolio, we will use it to show you how it is used but will also offer you a comparison in vanilla JS, so that you can see the difference between them.
>
> An example of selecting an HTML element by id: 
> 
> jQuery:
> `$('#my_id')`
> 
> Vanilla JS:
> `document.getElementById('my_id')`
> 
> Although vanilla JS has more characters in this instance (at least at first glance), it doesn't have the overload of having to load in an entire library!

#Add JavaScript &amp; jQuery to your page
There are some debates on this (of course!). Just like the CSS can be declared in the head tag of the HTML document, JavaScript can be declared in a similar fashion within the script tag. However, just as with CSS, best practice recommends that the JavaScript should be in a separate file and just be linked to the HTML in the head tag.

The old way to do this used to be the same way we did with our CSS files. You would add the **link** tag inside the head tag and it would load in the JavaScript file. 

An example of this:
```
    <head>
        <title>Make School's Portfolio</title>
        <link rel="stylesheet" type="text/css" href="./css/portfolio.css">
        <script src="./js/portfolio.js"></script>
    </head>
``` 
Now, this is where the debate lies. The browser renders a web page from top to bottom, so it will start with loading the CSS file, then load the JavaScript file and then it will render the rest of the HTML content. The problem is that if it takes a long time to load the JavaScript, then the rest of the page will not render until the JavaScript has finished loading. Remember that your visitors might not wait around until the page is loaded and go elsewhere. 

Most of the time you don't need the JavaScript as soon as the page is loaded as most of your content will most likely be written in HTML. So why load the JavaScript in before the HTML? Well exactly, we don't need that. If you've had a look at the HTML5 Boilerplate, you will have seen that the latest "best practice" is to load the JavaScript inside the body tag, just before it closes. This ensures that the HTML can render and your visitor sees something happening before it starts loading in the JavaScript.

> [action]
> Add a folder to your project and name it **js**. Inside it, create another folder called **vendor** and an empty file with the **.js** extension. Name it **portfolio.js**.   

![Add JS in Sublime](./1-sublime-js.png "Add JS in Sublime")

We also need to download the jQuery library from the website. As we already used CSS3 heavily, we are definitely not catering for IE8, so we can download the 2.x version.

> [action]
> Go ahead and download the compressed production version for our project from the [jQuery website](https://jquery.com/download/). Move it into the newly created vendor folder. It's good practice to keep your JavaScript files separate from any libraries you might use. 

Now let's add our script tags to the page.

> [action]
> Add the script tag for our portfolio.js file and the jquery library inside the body tag just before it closes. Add the jQuery library first, then our own file.

<!-- Comment to break actionable boxes. -->

> [solution]
> The HTML should look like this:
>```
>            ...
>
>                <div class="button">Download My CV</div>
>            </footer>
>            
>            <script src="./js/vendor/jquery-1.11.3.min.js"></script>
>            <script src="./js/portfolio.js"></script>
>        </body>
>    </html>
> ```
> The jQuery library needs to be loaded first because we are going to use it in our own JavaScript file, so it needs to be fully loaded before we try to access it.

#Alert "Hello World"
Now that the files are connected, let's test that we didn't make any mistakes. We are going to use the jQuery **ready** function.

> [action]
> Add the following JavaScript into your portfolio.js file:
> ```
>    $( document ).ready(function() {
>      alert('hello');
>    });
> ```

When you reload the browser, you should see an alert window popping up. If you click "ok", it will close. 

![Alert Hello](./3-alert.png "Alert Hello")

**What is happening here?** We are accessing the jQuery library by using the **$** symbol. The dollar is an alias for the library and allows us to access functions that were declared in the library. In this case, the **ready** function. Inside the ready function, a callback is expected as a parameter, a function that is called when the ready function is executed. For our small example, we used the **alert** function, which creates a little popup with the string we pass to it.

The ready function is used to execute any code when the page is loaded for the first time. This is a good place to put any event listeners for buttons or events that are user triggered.

> [info]
> **Alert in vanilla JS**
> 
> Just for comparison, the above function would look like this in vanilla JS:
> ```
>    document.onreadystatechange = function () {
>        if (document.readyState == "complete") {
>            alert('hello');
>        }
>    }
> ```
> Instead of using the dollar symbol to access the document element, we will use the JavaScript selector for *document* and then call a function called *onreadystatechange*. Once the page is complete (which we check in the *if* statement), we call the *alert* function. This is a very simplified version of the jQuery *ready* function but aids to help you understand how different it is to code in vanilla JS as opposed to using the jQuery library.

<!-- Comment to break actionable boxes. -->

> [info]
> ** What are event listeners?**
> 
> An Event Listener is attached to an object (like a button) and waits for some action to be performed on the object, be it a mouse click, mouse hover, pressing of keys, etc. Once an event occurred it is then handled by a function, which does something based on the event. For example, a user presses a button and the function triggered calls the alert function, which displays a message to the user.

Now that we know how to add JavaScript to our page, lets get started on adding a gallery to our website that will showcase our work using the PhotoSwipe plugin. 
