---
title: "A Sticky Footer"
slug: sticky-footer
---     

#Some fancy lines
One thing we're still missing from the footer is some pretty and fancy lines next to "About". We will be using a little trick from our dev kit for those. We will add a `<div>` tag before and after the `<h3>` and give the `div` a top border. We are basically adding two boxes, but because they will be empty with just a top border, they will look like lines.

![Flex column](./3-footer-flex.png "Flex column")

> [action]
> Add a class to the `footer` and use `text-align:center;` to center the text inside the `footer`. Open and close a new `div` before and another `div` after the `h3` tag inside the `footer`. Add a class to the two `div`s called *line*. While we're at it, let's wrap those three elements (`div`, `h3`, `div`) into another `div` to keep this section contained. Inside the line class, add a rule for `border-top`, choosing a border size, style and color. Make the line class have `width` 100%. `div` elements have 0 `height` and `width` without any content, so we are telling the element to be 100% `width` of the available space.

<!-- Comment to break actionable boxes. -->

> [solution]
> The HTML:
> 
> ```
>    <footer class="footer">
>        <div>
>            <div class="line"></div> 
>            	<h3 class="footer-sub title">About</h3>
>            <div class="line"></div>
>        </div>
>        <a href="./resume.pdf" class="button">Download my Resume</a>
>    </footer>
> ```
> The CSS so far:
> 
> ```
>    .footer {
>      text-align: center;
>    }
>
>    .line {
>      border-top: 1px solid #828282;
>      width: 100%;
>    }
> ```

Alright, we almost have a perfect looking footer, the only thing is that the lines are over and under the "About" header, but actually we want them to be on the left and right, like this.

Any idea on how we might change this?

![Flex column](./3-footer-flex.png "Flex column")

To be more like this?

![portfolio with styling](./1-finished.png "portfolio with styling")

I hope your answer was flexbox! Because then you are quite right. Remember how we spoke about flexboxes' default setting being a row? That will be very useful right now. Let's use flex on the surrounding div.

> [action]
> Add `flex` to the `div` surrounding the line `div`s and `h3` tag. Reload the browser. Do you see how the lines are short? That's because the footer is centered and doesn't take up all the space of the page. Add `width:100%;` to the footer class to change that. Do you see how the horizontal line goes all the way to the edge of the page and touches the "About" header? That's a little weird, let's put some white space around the lines to give them room the breathe. Add some left and right margin to the `line` class. Also, the footer is very close to the bottom to the page, so add some bottom margin to the `footer` class to give it some space.

> [solution]
> The CSS:
> 
> ```
>    .footer {
>      text-align: center;
>      width: 100%;
>      margin-bottom: 2%;
>    }
>    
>    .line {
>      border-top: 1px solid #828282;
>      width: 100%;
>      margin-left: 1%;
>      margin-right: 1%;
>    }
> ```


#A sticky footer
And now to the sticky footer! We need to employ some CSS3 trickery to keep the footer at the bottom. This also used to be a very hacky thing in web development but has now been improved thanks to CSS3!

We will make use of the new css viewport units, which allows us to calculate the height of the main content and tell the browser to put the footer below it. This will require us to know the height of the footer.

> [action]
> To calculate the height of the main content, we're going to add a `div` around the entire content except the footer tag. But we have a problem - the way the `flex column` divs are currently nested, we can't add the `div` that will enclose the main content. You need to close the `div` tag with the `flex column` class before the footer starts, instead of after. That will move the footer outside of the outermost `flex column` `div`. 
> 
> So, add the `div` that will enclose the main content. Then add a class to it and add the following rule to the class:
> 
> ```
>      min-height: calc(100vh - 126px);
> ```

<!-- Comment to break actionable boxes. -->

> [solution]
> Adding the above rule to the class `main-wrapper` will calculate the view height (`vh`) and subtract the height of the footer from it. This will always push the footer just below any other content that is on the page.
>
> The HTML should be like this:
> 
> ```
>    <body>             
>      <div class="main-wrapper">
>          <header class="header">
>              <nav class="nav">
>                  <ul>
>                      <li class="nav-item"><a href="#">Home</a></li>
>                      <li class="nav-item"><a href="#">Gallery</a></li>
>                      <li class="nav-item"><a href="#">Contact</a></li>
>                  </ul>
>              </nav>
>          </header>
>          
>          <div class="flex column">
>              <section>
>                  <div class="flex column">
>                      <img class="logo" src="https://goo.gl/RG3GtK" />
>                      <img class="main-img circle" src="http://placekitten.com/g/150/150" />
>                  </div>
>                  <h1 class="main title ">Hello I'm Kitty</h1>
>                  <h2 class="sub title">I love creating code</h2>
>              </section>
>          </div>
>      </div>
>    
>      <footer class="footer">
>          <div class="flex">
>              <div class="line"></div> 
>              <h3 class="footer-sub title">About</h3>
>              <div class="line"></div>
>          </div>
>          <div class="button">Download My CV</div>
>      </footer>
>    </body>
> ```

Alright, we're almost there. The only thing left to do is to move the titles on top of the image and resize the image, so that everything fits onto one page. Of course, we could have the user scroll up and down to see our titles, but it's a better first impression when the visitor can see everything at a glance.

Let's move the titles up, so that we get to see the footer. This is easily done by using a negative top margin again. We can add a negative margin to each title individually but it would be much easier to just have a wrapping `div` around it and pull them both up at the same time.

> [action]
> Add a `div` to surround the `h1` and `h2` tags. Give it a class name and add a rule to it in the CSS using a negative top margin until the footer is on the page. Add the `flex` and the `column` class to the new `div` too, so that our titles stay nice and centered.

<!-- Comment to break actionable boxes. -->

> [solution]
> In HTML:
> 
> ```
>    <div class="titles flex column">
>        <h1 class="main title ">Hello I'm Kitty</h1>
>        <h2 class="sub title">I love creating code</h2>
>    </div>
> ```
> 
> And in CSS:
> 
> ```
>    .titles {
>      margin-top: -22%;
>    }
> ```

Last but not least, let's make the image smaller. Ideally it takes up the center portion of our website, so we can make use of percentage values when setting a width for the image. Without percentages, we would run into a problem. In the next part we will make our page [responsive](https://en.wikipedia.org/wiki/Responsive_web_design) for mobile, so we can't just set a fixed width for the image. Instead let's put a `div` around our main-image and resize that based on a percentage of our entire page. Anything inside that new wrapping `div` will be resized to its parent container.

> [action]
> Put a wrapping `div` around the `img` tag with the circular image. Add a class to that new `div` and give it a `width` in percentage units. It should be small enough to get the footer back onto the page but big enough to still make a splash. 

<!-- Comment to break actionable boxes. -->

> [solution]
> In HTML: 
> 
> ```
>    <div class="img-wrapper">
>        <img class="main-img circle" src="http://placekitten.com/g/600/600" />
>    </div>
> ```
> 
> And in CSS:
> 
> ```
>    .img-wrapper {
>      width: 60%;
>    }
> ```

And there you have it, a portfolio page where everything is almost perfectly in place! We still have some misalignment with the logo and the main image but don't fret, we'll cover that in the media queries section.

![portfolio with styling](./1-finished.png "portfolio with styling")

> [solution]
> If we lost you somewhere, here's the current HTML file:
> 
> ```
>    <html>
>      <head>
>          <title>Make School's Portfolio</title>
>          <link rel="stylesheet" type="text/css" href="./css/portfolio.css">
>      </head>
>    
>      <body>            
>          <div class="main-wrapper">
>              <header class="header">
>                  <nav class="nav">
>                      <ul>
>                          <li class="nav-item"><a href="./index.html">Home</a></li>
>                          <li class="nav-item"><a href="./gallery.html">Gallery</a></li>
>                          <li class="nav-item"><a href="./contact.html">Contact</a></li>
>                      </ul>
>                  </nav>
>              </header>
>              
>              <div class="flex column">
>                  <section>
>                      <div class="flex column">
>                          <img class="logo" src="https://goo.gl/RG3GtK" />
>                          <div class="img-wrapper">
>                              <img class="main-img circle" src="http://placekitten.com/g/600/600" />
>                          </div>
>                      </div>
>                      <div class="titles flex column">
>                          <h1 class="main title ">Hello I'm Kitty</h1>
>                          <h2 class="sub title">I love creating code</h2>
>                      </div>
>                  </section>
>              </div>
>          </div>
>      
>          <footer class="footer">
>              <div class="flex">
>                  <div class="line"></div> 
>                  <h3 class="footer-sub title">About</h3>
>                  <div class="line"></div>
>              </div>
>              <a href="./resume.pdf" download="MyResume" class="button">Download my Resume</a>>          
> 			</footer>
>    
>      </body>
>    </html>
>```
>
> And our CSS file so far:
> 
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
>      margin-bottom: 18px;
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
>    
>    .circle {
>      border-radius: 50%;
>    }
>    
>    .flex {
>      display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6, BB7 */
>      display: -ms-flexbox;  /* TWEENER - IE 10 */
>      display: -webkit-flex; /* NEW - Safari 6.1+. iOS 7.1+, BB10 */
>      display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
>      align-items: center;
>    }
>    
>    .column {
>      flex-direction: column;
>    }
>    
>    .footer {
>      text-align: center;
>      width: 100%;
>      margin-bottom: 2%;
>    }
>    
>    .row {
>      flex-direction: row;
>    }
>    
>    .main-img {
>      margin-top: -54px;
>    }
>    
>    .logo {
>      z-index: 2;
>      width: 100px;
>    }
>    
>    .line {
>      border-top: 1px solid #828282;
>      width: 100%;
>      margin-left: 1%;
>      margin-right: 1%;
>    }
>    
>    .main-wrapper {
>      min-height: calc(100vh - 126px);
>    }
>    
>    .titles {
>      margin-top: -22%;
>    }
>    
>    .img-wrapper {
>      width: 60%;
>    }
> ```

But hold on, try resizing the browser into a smaller size. Uh oh, now the font is way too big for our mobile screen and the layout looks broken! 

![broken on mobile](./2-not-resized.png "broken on mobile")

Let's get that fixed in the next part where we work with CSS media queries.
