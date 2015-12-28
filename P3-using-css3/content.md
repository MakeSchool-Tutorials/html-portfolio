---
title: "Using CSS3"
slug: using-css3
---     

#Cutting Edge CSS
Now that we have some basic styling, let's make our main image round and centered. We are going to use some new CSS3 rules for this. Let's start with making the image round. One trick to make the image round is to use the **property** border-radius. Applying a border-radius of 50% to any element makes it a circle (see the info box for more details). We also want to make sure that our image is exactly centered in the middle of our page... and while we are at it, we don't just want to center our image but our entire content. 

> [info]  
> **The box model of HTML elements**
> In a document, each element is represented as a rectangular box. Determining the size, properties — like its color, background, borders aspect — and the position of these boxes is the goal of the rendering engine (inside the browser).
> In CSS, each of these rectangular boxes is described using the standard box model. This model describes the content of the space taken by an element. Each box has four edges: the **margin** edge, **border** edge, **padding** edge, and **content** edge.
> 
> ![box model](./2-box-model.png "box model")
> 
> The content area is the area containing the real content of the element. It often has a background, a color or an image.
> The padding area extends to the border surrounding the padding. When the content area has a background, color, or image set on it, this will extend into the padding, which is why you can think of the padding as extending the content. The padding is located inside the padding edge.
> The border area extends the padding area to the area containing the borders. It is the area inside the border edge.
> The margin area extends the border area with an empty area used to separate the element from its neighbors. It is the area inside the margin edge.

Now, that we know a bit more about box models, let's try to use that knowledge to center our content. We want to use one of the newest rules in the CSS realm that has kind of turned our world upside down when it comes to positioning things on a web page. This used to involve a lot of [hacks](http://stackoverflow.com/questions/2017809/what-is-the-best-way-to-center-a-webpages-content-using-css) and [ugliness](http://stackoverflow.com/questions/10872688/how-to-center-body-on-a-page) but now that we have [flexbox](https://philipwalton.github.io/solved-by-flexbox/demos/vertical-centering/), we have found a nice and consistent way to position things on our pages.

The flexbox concept might be a bit of beast to wrap your head around, so let's go through it step by step. Let's add the display:flex rule to the body tag. We can do this by using the body tag selector directly in the CSS but it's nicer to use class tags instead. 

> [action]
> Make a class called flex in your CSS file and then add the class to the body tag. Add the following rules to the flex class in your CSS:
> ```
> display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6, BB7 */
> display: -ms-flexbox;  /* TWEENER - IE 10 */
> display: -webkit-flex; /* NEW - Safari 6.1+. iOS 7.1+, BB10 */
> display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
> ```
> Why did we add four rules instead of just one? See the info box at the bottom of this step but ultimately, we still have to cater for various browser versions that implement the same style using different rules. All new browsers use the `display:flex;` rule but older browsers still need their **vendor prefix**. A good page to check if a prefix is needed for a rule, is [http://shouldiprefix.com/](http://shouldiprefix.com/).

If you now reload the browser, you should see the content moved but not centered. The content has now aligned itself horizontally. That's because flex has two different ways to align elements and the default is horizontally (or like a row). To change it's default behavior, we will wrap our content into a div. At the moment, our content is a header, a section and a footer. 

> [action]
> Wrap a div tag around those three sections.

The content is now back into the correct order but we need to still center the whole content. Two rules will help us with this. 

> [action] 
> Add these two rules to your flex class: 
> ```
> align-items: center;
> justify-content: center;
> ```

Once you have saved your files, reload your browser and voila! Our content is perfectly centered albeit still not quite what we expected. Let's fix that.

> [info]
> **When can I use new CSS3 rules?**
> As a developer it is important that you stay up to date on new technologies and it's also fun to start playing with new technologies. However, it is also important that you are aware that not all browsers will start supporting new ideas right away or maybe in different ways. This might mean that you have to make the decision to either use a new technology at the risk of it not being supported by all browsers, which could mean that you will have some users not being able to access your site or certain features of it. This can of course be prevented by [graceful degradation](https://www.w3.org/wiki/Graceful_degradation_versus_progressive_enhancement#Graceful_degradation_and_progressive_enhancement_in_a_nutshell) but it's best if you are aware of it in the first place. A good source to test if a feature is available and can be used without any issues is the excellent site [Can I Use?](http://caniuse.com/).
> As we have decided to use flexbox and border-radius, our page does not support users on IE8 (for the border-radius) and IE9 (for flexbox). To get support in IE10 and IE11, we need to use vendor-prefix. This means that our content will not have a circle image and won't be centered.
> Any ideas how we could cater for those older browsers?

> [solution]
> You guessed it, graceful degradation! In this case we could make use of the older hacks on how to center our content and come up with a different way to make the image circular. Alternatively, we could load in different stylesheets based on browser features. This requires some more logic in the `<head>` tag or some JavaScript.








