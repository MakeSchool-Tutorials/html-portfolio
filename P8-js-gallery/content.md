---
title: "Adding a Gallery"
slug: js-gallery
---     

#The Gallery
Once we're finished we'll have a page like the one below, that is resizable and allows the visitor to see all of your work at once via the thumbnails, but also allows them to click on each image to see a bigger view.

![Cat Gallery](./3-gallery.gif "Cat Gallery")

#Creating the HTML gallery page
We need to create an empty HTML page that will contain the gallery. We want to make the page look consistent with our first page, so let's reuse some of the styles and add the same header to our gallery page.

> [action]
> Create a new HTML page called gallery.html. Copy the content from index.html, but remove everything except the `header`, `script` and `head` tags - make sure you keep everything enclosed in those tags. You should change the content of the title tag to something like "your_name Gallery".
> 
> Remove the script tags from index.html as we don't need them there anymore - all of our JavaScript will be in the gallery page.

Your page should now look like this:

![Empty gallery](./1-empty-gallery.png "Empty gallery")

> [solution]
> 
> ```
>    <html>
>        <head>
>            <title>Make School's Gallery</title>
>            <link rel="stylesheet" type="text/css" href="./css/portfolio.css">
>        </head>
>    
>        <body>            
>            
>            <header class="header">
>                <nav class="nav">
>                    <ul>
>                        <li class="nav-item"><a href="./index.html">Home</a></li>
>                        <li class="nav-item"><a href="./gallery.html">Gallery</a></li>
>                        <li class="nav-item"><a href="./contact.html">Contact</a></li>
>                    </ul>
>                </nav>
>            </header>
>    
>            <script src="./vendor/jquery-2.2.0.min.js"></script>
>            <script src="./js/portfolio.js"></script>
>        </body>
>    </html>
> ```

#Downloading some plugins
Now that we have an empty gallery page, let's download a couple of JavaScript plugins - JustifyGallery and Swipebox. Both are designed to work with jQuery, and both come with their own CSS files. JustifyGallery is a nice image gallery that can work with different size thumbnails and image aspect ratios. Swipebox will be invoked when an image is clicked; it will overlay the image, while dimming the rest of the site, and provides some additional navigation.

> [action]
> Go to [JustifyGalllery](http://miromannino.github.io/Justified-Gallery/) and download the latest release. Unzip it and move the whole folder as-is into the vendor folder. Rename that folder, call it **justified**.
> 
> Now go to [Swipebox](http://brutaldesign.github.io/swipebox/#download) and download the library. Unzip it and navigate to **src** folder. Copy that folder into your vendor folder. Rename the **src** folder to **swipebox**. In the swipebox folder are **css** and **js** folders. There are two files in each, one is the minified version (has *min* in the file name) and the other is the development version. We don't need both for production, so go ahead and delete the development versions. It's very common to use minified versions of JavaScript plugins - they have been processed to reduce filesize so that they download faster. Usually whitespace and comments are removed, and sometimes variables are converted to have one character names, which makes them very difficult to read - try opening one of the minified files to see. 


![Vendors in Sublime](./2-vendors.png "Vendors in Sublime")

Now that we have the two plugins in our project, let's connect them to the gallery.html file. 

> [action] 
> Link the JustifiedGallery and SwipeBox CSS files inside the head tag. Then, using the `script` tag, link the JS files below where the jQuery is included but above where portfolio.js is included. 

<!-- Comment to break actionable boxes. -->

> [solution]
> You should have 3 CSS files inside the head tag and 4 JS files just before the body tag closes.
> 
> ```
>    <html>
>      <head>
>          <title>Make School's Gallery</title>
>          <link rel="stylesheet" type="text/css" href="./vendor/justified/justifiedGallery.min.css" /> 
>          <link rel="stylesheet" type="text/css" href="./vendor/swipebox/css/swipebox.min.css" /> 
>          <link rel="stylesheet" type="text/css" href="./css/portfolio.css">
>      </head>
>    
>      <body class="default">            
>          
>          <header class="header">
>              ...
>          </header>
>    
>          <script src="./vendor/jquery-2.2.0.min.js"></script>
>          <script src="./vendor/justified/jquery.justifiedGallery.min.js"></script>
>          <script src="./vendor/swipebox/js/jquery.swipebox.min.js"></script>
>          <script src="./js/portfolio.js"></script>
>      </body>
>    </html>
> ```

#Adding the gallery HTML
Now that the scripts are connected, we need to add some HTML, so the library can take the images and arrange them in a nice grid. 

> [action]
> Add a new `section` tag after the `header` tag, and give it the class `gallery-container`. Inside of the `section`, add a `h2` tag to properly announce the gallery. Give the `h2` some styling with the `sub` and `title` classes. We named ours "Kitty's Gallery", but maybe you'll want to name yours differently.
> 
> Inside the section tag, and after the `h2`, add a `div` with the `id` `gallery`. Inside of the `div`, we will add a bunch of `a` tags. Inside each of these `a` tags, add an `img` tag that will contain a thumbnail of the image we want to show. These requirements are determined by the library and well documented [here](http://miromannino.github.io/Justified-Gallery/getting-started/).
>
> Add a `title` attribute to the `a` tag and an `alt` attribute to the `img` tag. The `href` attribute for the `a` tag needs to link to the image you want to display when the thumbnail is clicked, and the `src` attribute of the `img` tag needs to link to the same image or a smaller version of the image (a thumbnail).
> 
> Here's an example:
> 
> ```
>    <a title="your_title" href="your_image_url">
>        <img alt="your_title" src="your_image_url"/>
>    </a>
> ```
> 
> Now add a ton of images! The best place to store your actual image files is within a directory called `img`, in the root directory for your page.

![Gallery without JS](./4-without-js.png "Gallery without JS")

> [solution]
> 
> ```
>    <section class="gallery-container">
>      <h2 class="sub title">Kitty's Gallery</h2>
>    
>      <div id="gallery">
>          <a title="Title 1" href="http://placekitten.com/452/450?image=1">
>              <img alt="Title 1" src="http://placekitten.com/452/450?image=1"/>
>          </a>
>          <a title="Title 2" href="http://placekitten.com/452/450?image=4">
>              <img alt="Title 2" src="http://placekitten.com/452/450?image=4"/>
>          </a>
>          <a title="Title 3" href="http://placekitten.com/452/450?image=6">
>              <img alt="Title 3" src="http://placekitten.com/452/450?image=6"/>
>          </a>
>          <a title="Title 4" href="http://placekitten.com/452/450?image=9">
>              <img alt="Title 4" src="http://placekitten.com/452/450?image=9"/>
>          </a>
>          <a title="Title 5" href="http://placekitten.com/452/450?image=12">
>              <img alt="Title 5" src="http://placekitten.com/452/450?image=12"/>
>          </a>
>          <a title="Title 6" href="http://placekitten.com/452/450?image=15">
>              <img alt="Title 6" src="http://placekitten.com/452/450?image=15"/>
>          </a>
>          <a title="Title 7" href="http://placekitten.com/452/450?image=13">
>              <img alt="Title 7" src="http://placekitten.com/452/450?image=13"/>
>          </a>
>          <a title="Title 8" href="http://placekitten.com/452/450?image=14">
>              <img alt="Title 8" src="http://placekitten.com/452/450?image=14"/>
>          </a>
>      </div>
>    </section>
> ```

Now that we have the HTML part of the gallery working, you should see your images in their original sizes. But instead of filling the page nicely, left to right, it currently shows the full-size images and there's a lot of white space on the right. Let's take care of that with some simple JavaScript.

#Adding JavaScript to the mix
You will be surprised how little JavaScript it takes to make the gallery look as elegant and nice as we expect, with the help of the plugins. Time to add some code to the portfolio.js file. 

> [action]
> If you haven't already, remove the alert function from the jQuery ready function, so that we can put some different code in there instead. We want to invoke the `justifiedGallery` function on the parent element that holds all of our images. That will activate the plugin, so that it will automatically resize the images to fit the page. We gave the parent element the `id` `gallery`. Use jQuery to select the DOM element with the id `gallery`. Then call the `justifiedGallery` function on it to initialize the plugin. 
> 
> It's a simple as: `$('#gallery').justifiedGallery();`

If you reload the page now, it should look like this:

![Gallery without Parameters](./5-without-params.png "Gallery without Parameters")

It's better, but the pictures are still not very nicely distributed. All of the images are in a row and visible but we want the work presented as bigger thumbnails, it would also be nice to fill up the whitespace. JustifiedGallery supports a number of parameters, which we can make use of. You can find all of them [here](http://miromannino.github.io/Justified-Gallery/options-and-events/).

We want the rows to have a certain height, so we will use the `rowHeight` option. There should also be a bigger margin between the images and, just for kicks, it can  randomize the images each time they load, so that the gallery is never the same layout. JustifiedGallery also provides an option to justify the last row. This means that all images on the last row will take up the available space, as opposed to have them align to the left. This will be nice to get a grid-like layout. 

> [action]
> Look at the options available and try to figure out what parameters you need to pass into the function to achieve the above. Parameters are passed into the function as key-value pairs inside of curly brackets in a JSON-like format.

<!-- Comment to break actionable boxes. -->

> [solution] 
> We made each row 200 pixels high, except the last row which is now justified. We also added a margin of 3 pixels around all the images for a bit of spacing. Making your gallery display the images randomly is totally up to you, but we liked it, so we added that parameter.
> 
> ```
>    $( document ).ready(function() {
>      $("#gallery").justifiedGallery({
>        rowHeight : 200,
>        lastRow : 'justify',
>        margins : 3,
>        randomize: true
>      });
>    });
> ```

![Gallery with JS](./6-with-js.png "Gallery with JS")

Later, we're going to need to do more with the gallery instance we just initialized. To make it easier, we should save a reference to the gallery in a variable.  To do that, add `var gallery = ` before the initialization.

So it will look like this:

> [solution]
> 
> ```
>     var gallery = $('#gallery').justifiedGallery({
        rowHeight : 200,
        lastRow : 'justify',
        margins : 3,
        randomize : true
    });
> ``` 

Excellent! See how easy it is to make use of a plugin? We're almost there now. We're only missing one thing. Currently, when you click on an image, the image will open up in a new page. But we want our image to "pop up" and display bigger on the same page, so that visitors can take a closer look without losing their place.

#Initializing the Swipebox plugin
The Swipebox plugin gives us that functionality and works very well with the JustifiedGallery plugin. If you look at the documentation for the JustifiedGallery plugin, there is even an [example](http://miromannino.github.io/Justified-Gallery/lightboxes/) on how to achieve this. 

We need to be sure that all photos in the JustifiedGallery have loaded before we call the Swipebox plugin. Luckily for us, JustifiedGallery provides events that trigger at certain times of the life cycle of the plugin. One of these events is the `jg.complete` event. We want to initialize Swipebox when that event is triggered.

Here is an example of using the event:

```
    gallery.on('jg.complete', function () {
        alert('the gallery is complete');
    });
```

> [action]
> Inside the `jg.complete` callback, we will bind the Swipebox plugin to each of the `a` tags in our gallery. Use `$('#gallery a')` to grab a reference to each of the `a` tags within the gallery, then use the `swipebox()` function on them. The Swipebox library also accepts parameters to do various things, you can see the [docs here](http://brutaldesign.github.io/swipebox/#options). 

![Swipebox plugin](./7-swipebox.gif "Swipebox plugin")

> [solution]
> Notice that we initialize swipebox with a parameter - we set `hideBarsDelay` to false, which will prevent the swipebox UI from automaticaly hiding itself.  By default, it hides after 3 seconds (3000 milliseconds).
> 
> ```
> $( document ).ready(function() {
>     var gallery = $('#gallery').justifiedGallery({
>         rowHeight : 200,
>         lastRow : 'justify',
>         margins : 3,
>         randomize : true
>     });
>     
>     gallery.on('jg.complete', function() {
>         $('#gallery a').swipebox({hideBarsDelay : false})
>     });
> });
> ```

And there you have it, a beautiful modern gallery to showcase your work! This is where any potential employers might come to see what you have done so far. But how are they going to contact you if they like your work? That is the question we answer in the next part, when we build a "Contact Me" form.
