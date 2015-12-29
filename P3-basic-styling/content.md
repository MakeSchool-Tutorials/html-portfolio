---
title: "Basic Styling"
slug: basic-styling
---     

#Styling the portfolio
Now that the files are connected, let's add some basic rules to our CSS to make the page look more colorful. One way to do that is to add some background color to the page. Pick any color you like, keeping in mind that your users will have to see that page and you want to make a good impression and keep your text legible.

> [action]
> Use the tag selector for body and add a rule to it in the CSS file. Remember that a tag selector has no dot nor hashtag, then add curly brackets and within it, the following rule:
> ```
>    background-color: #dfdfdf;
> ```
> Save your file and check out your portfolio so far. 

Now that you know how it's done, let's add some more default styles to our CSS file like the color of our font, the font type itself and color for our links. The default styles provided by each browser aren't very fancy nowadays, so let's put some style onto that page!

> [action]
> Come up with a few rules that you always want to see on your page and add them to the same body tag. Here are some examples of things you could add:
> 
> - color of the font
> - font-family (changes the font type you use)
> - font-size 
> - more [CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference), click through each property to see what they do
>
> You can see lots of ideas of what CSS can do in the [CSS Zen Garden](http://www.mezzoblue.com/zengarden/alldesigns/).
>
> A good place to find some colors to add to your page is [color-hex](http://www.color-hex.com/). If you're looking for fonts, try [cssfontstack](http://www.cssfontstack.com/).

<!-- Comment to break actionable boxes. -->

> [info]
> **Hex values, RGB and more**
>
> You've probably noticed that I used the word blue in our first example to set the font color. But with the background-color, I used hex values. It's also possible to use RGB values. There's a good write up on Wikipedia [here](https://en.wikipedia.org/wiki/Web_colors) about web colors, so just go ahead and find out more about the differences between these.

<!-- Comment to break actionable boxes. -->

> [solution]
> Here is the CSS that we used to style some basics on our page:
> ```
>    body {
>      background-color: #dfdfdf;
>      color: #333333;
>      font-family: 'Courier New', Courier, 'Lucida Sans Typewriter', 'Lucida Typewriter', monospace;
>    }
> ```
> It's good to set a group of fonts as some operating systems might not have the first font you specified and will fall back on the second specified font. If that doesn't exist either, it will try the third one and so on.

#Basic styling for the header
First we add the border at the top. We've chosen the color that we already have in the logo. There are simple Chrome extensions out there that can help you with selecting a color from a web page, like [Colorzilla](https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp) for example.

> [action]
> Add a top border to the header. The property **border** can take 3 shorthand values. The first one is the type of border you want (solid, dotted, dashed), the second parameter is the size of the border in pixels and the last parameter is the color. 

<!-- Comment to break actionable boxes. -->

> [solution]
> Don't forget to add a class to your header tag in the HTML!
> ```
>    .header {
>      border-top: solid 8px #019cdb;
>    }
> ```

Now if you reload the page, do you see that there is some spacing between the border and the top of the page? Why do you think that is? 

This is one of those cases where all browsers display it slightly different. Each browser vendor uses their own default stylesheet to display certain elements. One of the things they do is add a default margin and padding to HTML elements. One way to prevent this, is to use a normalized stylesheet (as mentioned in the boilerplate info box). We will just use a very simplified version for that by adding the following rules to the very top of our CSS file.

> [action]
> Add this rule to the very top of your stylesheet and see what that does to your border:
> ```
>    * {
>      margin: 0;
>      padding: 0;
>    }
> ```

Now that has made all the difference! This resets the browsers stylesheet to make all HTML elements have 0 as a default value for the margin and padding. There's more that can be done here but for sake of simplicity, we leave it at that for now. If you're more interested in this topic, head [here](http://nicolasgallagher.com/about-normalize-css/) to read more about it.

Now that we have a nice border at the top, let's make our links look better than the dotted list we currently have. There are two things we want to achieve here. We want to make the links display horizontally rather than vertically in a list. On top of that, we want to remove the dots that prefix each list item and remove the underline of the links. And while we're at it, we should position the navigation better as a whole and have the links be a different color when a user hovers over each item.

> [action]
> Make the list vertical by using the rule `display:inline;` and `list-style:none;` on the list items. Add some margin to our nav tag to move it away from the left and down from the top. Don't forget to use classes!

<!-- Comment to break actionable boxes. -->

> [solution]
> In the CSS file:
> ```
>    .nav {
>      margin-top: 12px;
>      margin-left: 10%;
>    }
>    
>    .nav-item {
>      list-style: none;
>      display: inline;
>      margin-right: 12px;
>    }
> ```
>
> In the HTML file:
> ```
>    <header class="header">
>        <nav class="nav">
>            <ul>
>                <li class="nav-item"><a href="#">Home</a></li>
>                <li class="nav-item"><a href="#">Gallery</a></li>
>                <li class="nav-item"><a href="#">Contact</a></li>
>            </ul>
>        </nav>
>    </header>
> ```

As we want the link changes to be sitewide and not just for this instance, let's use the tag selectors for the links. You also need to use the pseudo selector :hover to change the link color on hover. It is used by adding **:hover** after your selector. In this instance, you would use **a:hover** as a selector to change the link color on hover. 

> [action]
> Use the a tag selector to add a default color to links and remove the underline of the link. The text-decoration property will help you.

<!-- Comment to break actionable boxes. -->

> [solution]
> ```
>    a {
>      color: #019cdb;
>      text-decoration: none;
>    }
>    
>    a:hover {
>      color: #48b2e8;
>    }
> ```
> This should achieve something like this: 
>
> ![basic header styling](./1-header.png "basic header styling")

#Basic styling for the footer
As the footer has only two items that need styling, let's transform it before the main content. The footer needs to get a new font color for the "About" header and we need to style the button. Let's start with the color and casing of the header. 

> [action]
> Change the font-color and casing of the "About" header. Add a class to the header first and then use the "text-transform" and color properties. 

<!-- Comment to break up actionable boxes. -->

> [solution]
> Because we want to reuse the title later on in the other titles. We added one class for rules that the other titles have in common called *title* and another class called *footer-sub* that will control the font-size of this particular title.
> 
> In the HTML file:
> ```
>    <footer>
>        <h3 class="footer-sub title">About</h3>
>        <div>Download My CV</div>
>    </footer>
> ```
> In the CSS file:
> ```
>    .title {
>      color: #019cdb;
>      text-transform: uppercase;
>      letter-spacing: 3px;
>    }
> 
>    .footer-sub {
>      font-size: 30px;
>    }
> ```

Once we've changed those, we should add those two horizontal lines left and right of the title. That will require some flexbox magic though, so let's hold off with that until the next section where we will cover flexbox in depth.

Let's focus our attention on the button instead. First we need to give the button a border to make it look like a button and let's color in the same theme as the rest our page. We should also give it a hover effect, so users know that they have to click it to download the CV.

> [action]
> Add a border to the button, play with the options that the inspector provides to get a feel for what styles are available. You want to use the properties: *border*, *display:inline-block;*, *padding* and for the hover effect, you need to use the pseudo selector :hover again. In there you might want to use the property *cursor*.

<!-- Comment to break up actionable boxes. -->

> [solution]
> You want to add a class to the HTML div:
> ```
>    <div class="button">Download My CV</div>
> ```
> And then we add the following rules to the class and use the pseudo selector :hover.
> ```
>    .button {
>      border: 2px solid #019cdb;
>      color: #019CDB;
>      display: inline-block; /* To wrap the border just around the content */
>      font-size: 20px;
>      margin-top: 12px;
>      padding: 12px 30px;
>    }
>    
>    .button:hover {
>      background-color: #019CDB;
>      color: #dfdfdf;
>      cursor: pointer;
>    }
> ```
> This should achieve something like this: 
>
> ![footer styling](./2-footer.png "footer styling")


#Basic styling of the main content
After the header and footer, let's take care of the main content. The kitten image should be round and we want our logo to be positioned above the kitten. Our two catch phrases should be centered on the image. Making our image a circle and centering content on web pages used to be an art in hacking and making complicated changes to our web page just to get things centered. Thanks to the latest advances in CSS, we can now forget all of this and use the power of flexbox to get everything in place! We'll cover that part in the next section. For now let's focus on changing the font size, color and type.

> [action]
> Pick a font you like on [cssfontstack](http://www.cssfontstack.com/) and add it to the class selector of your main title and sub title. Then select a color for the font as well as a size for the font and add it to the rules. The rules that you might want to look into are *text-transform*, *letter-spacing* and *font-size*.

<!-- Comment to break up actionable boxes. -->

> [solution]
> You need to add a class to the h1 and h2 tag. We added one class for rules that the two titles have in common called *title* and a separate class for each title to manipulate the font-size.
>
> The HTML file:
> ```
>    <section>
>        <img src="https://goo.gl/RG3GtK" />
>        <img src="http://placekitten.com/g/600/600" />
>        <h1 class="main title ">Hello I'm Kitty</h1>
>        <h2 class="sub title">I love creating code</h2>
>    </section>
> ```
> The CSS file:
> ```
>    .title {
>      color: #019cdb;
>      text-transform: uppercase;
>      letter-spacing: 3px;
>    }
>    
>    .main {
>      font-size: 78px;
>    }
>    
>    .sub {
>      font-size: 57px;
>    }
> ``` 
> This should achieve something like this: 
>
> ![main content styling](./3-main-content.png "main content styling")

Once you have had some time adding CSS properties to your page, make sure the page looks like you expected. Below is a solution that will style the page to look like the page we showed at the beginning of this tutorial. It will give you an idea of things you can add to the page that will make the page more colorful and modern. Don't get ahead of yourself in terms of centering the content and making the image circular. We'll cover this in the next part using CSS3.

> [solution]
> Just in case, we lost you somewhere, here are the HTML and CSS file that will make the page look like this:
> ![All content with basic styling](./4-all-content.png "All content with basic styling")
>  
> HTML file: 
> ```
>    <body class="default">
>      <header class="header">
>          <nav class="nav">
>              <ul>
>                  <li class="nav-item"><a href="#">Home</a></li>
>                  <li class="nav-item"><a href="#">Gallery</a></li>
>                  <li class="nav-item"><a href="#">Contact</a></li>
>              </ul>
>          </nav>
>      </header>
>    
>      <section>
>          <img src="https://goo.gl/RG3GtK" />
>          <img src="http://placekitten.com/g/600/600" />
>          <h1 class="main title ">Hello I'm Kitty</h1>
>          <h2 class="sub title">I love creating code</h2>
>      </section>
>    
>      <footer>
>          <h3 class="footer-sub title">About</h3>
>          <div class="button">Download My CV</div>
>      </footer>
>    </body>
> ```
> And the CSS file so far:
> ```
>    * {
>      margin: 0;
>      padding: 0;
>    }
>    
>    body {
>      background-color: #dfdfdf;
>      color: #333333;
>      font-family: 'Courier New', Courier, 'Lucida Sans Typewriter', 'Lucida Typewriter', monospace;
>    }
>    
>    a {
>      color: #019cdb;
>      text-decoration: none;
>    }
>    
>    a:hover {
>      color: #48b2e8;
>    }
>    
>    .header {
>      border-top: solid 8px #019cdb;
>    }
>    
>    .nav {
>      margin-top: 12px;
>      margin-left: 10%;
>    }
>    
>    .nav-item {
>      list-style: none;
>      display: inline;
>      margin-right: 12px;
>    }
>    
>    .title {
>      color: #019cdb;
>      text-transform: uppercase;
>      letter-spacing: 3px;
>    }
>    
>    .main {
>      font-size: 78px;
>    }
>    
>    .sub {
>      font-size: 57px;
>    }
>    
>    .footer-sub {
>      font-size: 30px;
>    }
>    
>    .button {
>      border: 2px solid #019cdb;
>      color: #019CDB;
>      display: inline-block; /* To wrap the border just around the content */
>      font-size: 20px;
>      margin-top: 12px;
>      padding: 12px 30px;
>    }
>    
>    .button:hover {
>      background-color: #019CDB;
>      color: #dfdfdf;
>      cursor: pointer;
>    }
> ```
