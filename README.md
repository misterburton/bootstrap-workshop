# Bootstrap Workshop

_**presented with <3 by [@misterburton](https://twitter.com/misterburton)**_

**Overview:** We'll start out with a little workflow & project setup, take a few moments to cover the basics of Bootstrap and then dive into creating a responsive page for Chicago's [Tree House Humane Society](http://www.treehouseanimals.org/).

***

### A couple things:

1. Take a moment to install this [RWD Bookmarklet](http://responsive.victorcoulon.fr/).

2. Then, check out what we're making, using your new bookmarklet: [http://misterburton.com/local/th/](http://misterburton.com/local/th/)

***

Prerequisite software installs: (here's hoping you've already done this)

* [Sublime Text 2](http://www.sublimetext.com/)
* [LiveReload](http://livereload.com/)

Prerequisite know-how:

* basic understanding of HTML & CSS
* know that this is going to be super easy & super awesome

***

## First up, making Sublime Text way more awesome

### Installing Package Control for Sublime

Open Sublime text and choose _**View > Show Console.**_

In the console window that opens at the bottom of the app, paste the following block of code (taken from Sublime Package Control's [Installation Page](https://packagecontrol.io/installation)):

**For Sublime Text 2 Users:**

```
import urllib2,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```

**For Sublime Text 3 Users:**

```
import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
Restart Sublime Text.

### Installing Emmet for Sublime

Now, open _**Tools > Command Palette**_, type 'install' in the window that opens and select `Package Control: Install Package`.

In the resulting window, type **'Emmet'**. Choose the resulting _**'Emmet (ex-Zen Coding) for Sublime Text'**_ option that appears in the list to install.

![emmet](http://i.imgur.com/tIZr6Sa.png)

## Download workshop files

[link](https://raw.githubusercontent.com/misterburton/bootstrap-workshop/master/_assets/BootstrapWorkshopFiles.zip)

## Adding LiveReload to our project

Open LiveReload and drag your project folder to its sidebar:

![LiveReload](http://i.imgur.com/J0CI2zU.png)

Copy the code from the _'Insert this snippet…'_ box.

Paste the text just above the closing `</body>` tag in your `index.html` file, like this:

![LiveReload Code](http://i.imgur.com/3Qjvjj0.png)

## Basic site & folder structure setup (Read along, for now, as I've done all this boring stuff for you)

### Downloads

* Download Bootstrap [here](getbootstrap.com).
* Download Font Awesome [here](fontawesome.io).
* Download Fastclick [here](http://ftlabs.github.io/fastclick/).
* Download JQuery [here](http://jquery.com/download/).
* Download Hamburgler [here](http://johnm.com.au/hamburgler/).

### Our Folder structure

```
BootstrapWorkshop/
├── css/
│   ├── bootstrap.min.css
│   ├── font-awesome.css
│   ├── form.css
│   ├── hamburgler.css
│   └── site.css
│
├── fonts/
│   ├── fontawesome-webfont.eot
│   ├── fontawesome-webfont.svg
│   ├── fontawesome-webfont.ttf
│   ├── fontawesome-webfont.woff
│   └── FontAwesome.otf
│
├── img/
│   └── icons/
│       ├── apple-touch-icon-ipad-retina.png
│       ├── apple-touch-icon-ipad.png
│       ├── apple-touch-icon-iphone.png
│       └── apple-touch-icon-retina.png
│
└── js/
    ├── bootstrap.min.js
    ├── fastclick.min.js
    ├── hamburgler.js
    ├── jquery.min.js
    └── site.js

```

### Link libraries in your index.html file

**CSS Syntax w/in `<head>` tags**

```
<link rel="stylesheet" href="css/bootstrap.min.css">
```

**JavaScript Syntax, placed before closing `</body>` tag**

```
<script src="js/bootstrap.min.js"></script>
```

### Disable 300ms tap delay on mobile in the site.js file

**Instantiate FastClick.js when `onDocumentReady` fires**

```
// shorthand jQuery for 'onDocumentReady'
$(function() {

  // disable 300ms tap delay on mobile browsers
  FastClick.attach(document.body);

}); // ./end onDocumentReady
```

### Write CSS Media Query Breakpoints in site.css

**CSS _@media_ query breakpoints taken directly from [getbootstrap.com/css](http://getbootstrap.com/css/)**

```
/*
Extra small devices (phones, up to 768px)
No media query since this is the 'mobile first' default in Bootstrap
Bootstrap HTML syntax: -xs-
*/

/* mobile & global CSS goes here */

/*
Small devices (tablet portrait, 768px and up)
Bootstrap HTML syntax: -sm-
*/
@media (min-width: 768px) {
  
  /* CSS for small devices goes here */

}

/*
Medium devices (tablet landscape & laptop, 992px and up)
Bootstrap HTML syntax: -md-
*/
@media (min-width: 992px) { 

  /* CSS for medium devices goes here */

}

/*
Large devices (desktop & laptop widescreen, 1200px and up)
Bootstrap HTML syntax: -lg-
*/
@media (min-width: 1200px) {

  /* CSS for large devices goes here */

}
```

## All Set Up, Let's Learn Some Bootstrap

### Scaffolding a Bootstrap Site

Bootstrap defaults to a 12-column grid. So, if you can add numbers from 1 to 12, you've only a little syntax to learn & you're already there.

![12 column grid](http://i.imgur.com/h9nDPbQ.png)

Bootstrap affords us a number of CSS utility classes with which to build our site, classes like `.container`, `row` and colums of varying widths, 1-12. (ex. `col-xs-12`)

We first start w/ a `container` div by writing the following:

```
<div class="container"></div>
```

Bootstrap sites are made by stacking one row after another. To create a row within our container div element, write the following:

```
<div class="row"></div>
```

If you remember our CSS Media Query breakpoints from setup, we had 4 that we reference via Bootstrap's HTML syntax:

1. Extra small, written as: `-xs-`
2. Small: `-sm-`
3. Medium: `-md-`
4. Large: `-lg-`

Columns in Bootstrap govern the layout of your site. They can span different widths at each of our 4 above breakpoint sizes.

For example, the following syntax will create a `row` with a single div element that spans all 12 columns at any page width:

```
<div class="row">
	<div class="col-xs-12">I span all 12 columns. Woot!</div>
</div>
```

Add a class of `red` to our new column div to better see what's going on in the browser, like this:

```
<div class="col-xs-12 red">
```

A row with one column is great for a header or navbar, sure, but what if we want a different layout to our row, like a three column grid?

Similar to the above example, we're going to create a `row` div element, only this time, it will contain three, equal-width columns. Within each column div's `class="…"` declaration, we're going to tell it how to size itself at our different media query breakpoints:

```
<div class="row">
	<div class="col-xs-12 col-sm-4">Left Column</div>
	<div class="col-xs-12 col-sm-4">Middle Column</div>
	<div class="col-xs-12 col-sm-4">Right Column</div>
</div>
```

To make this easier to read, let's dissect only one of the column divs:

```
<div class="col-xs-12 col-sm-4">Left Column</div>
```
As we've alluded to, above, the magic is in its `class="…"` declaration. The following line…

```
"col-xs-12 col-sm-4"
```

… tells Bootstrap:

* At our extra small size, span all 12 columns
* At our small size — i.e. when the viewport is 768px & wider — span only 4 columns
* because we've not specified either our `-md-` or `-lg-` sizes, they will default to the next largest size specified (in our case, `-sm-`, or 4 column

**Stack three of these together, as we have …**

```
<div class="row">
	<div class="col-xs-12 col-sm-4">Left Column</div>
	<div class="col-xs-12 col-sm-4">Middle Column</div>
	<div class="col-xs-12 col-sm-4">Right Column</div>
</div>
```

**… And we've now made a responsive row layout:** 3 columns on tablet, laptop & desktop (`col-sm-4`), and one column on mobile (`col-xs-12`).

All we had to do is add to 12: `col-sm-4` + `col-sm-4` + `col-sm-4` = 12 columns.

To better assist in seeing what's going on w/ our columns, add the classes `red`, `green`, and `blue` to each column after `col-sm-4`, respectively, like this:

```
<div class="row">
  <div class="col-xs-12 col-sm-4 red">Left Column</div>
  <div class="col-xs-12 col-sm-4 green">Middle Column</div>
  <div class="col-xs-12 col-sm-4 blue">Right Column</div>
</div>
```

Now, resize the width of your browser to see the page snap from a three-column grid at a width of >= 768px, and a 1 column grid of three stacked divs at widths < 768px.

### You now have a basic understanding of how every Bootstrap layout is created.

(woot!!!)

***

## With our new ka-nowledge, let's make a page for small, orphaned and sick kittens

First off, housekeeping. That little block of code we just wrote:

```
<div class="container">
  <div class="row">
    <div class="col-xs-12 col-sm-4 red">Left Column</div>
    <div class="col-xs-12 col-sm-4 green">Middle Column</div>
    <div class="col-xs-12 col-sm-4 blue">Right Column</div>
  </div>
</div>
```
You can delete it, we'll not be using it.

### Creating our header

Write the following:

```
<header></header>
```

Hit save (⌘ + s), and you'll see a brown header w/ a logo in your browser. (I've pre-written our CSS, so we can focus more attention on the Bootstrap bits)

Our header needs two things. First, a search form (for reference, all of the CSS for this search field is in `css/form.css`).

```
<!-- search form -->
<form id="searchForm">
  <input type="search">
</form>
```

***
_**For reference:** our search form was created via [this](http://webdesignerwall.com/tutorials/expandable-mobile-search-form) tutorial, and the icon we're using within it comes via [the noun project.](http://thenounproject.com/term/find/15028/)_

_The web is full of great resources like these, so when we're getting a quick & dirty prototype together, I find it's always best to avoid reinventing the wheel, whenever possible._
***

Next, our title. Also w/in `<header>` tags, and just beneath the `<form>` tags, insert the following:

```
<span>tree house</span>
```

Your full header HTML should read:

```
<!-- header -->
<header>

  <!-- search form -->
  <form id="searchForm">
    <input type="search">
  </form>

  <span>tree house</span>

</header><!-- ./header -->
```

_**Note:** I prefer to use comments to call out closing tags, just to make the syntax of a page more glancably understandable. The syntax i use is:_

```
<!-- ./tag, id or class name -->
```

### Desktop Navigation

Bootstrap's default navbar is rather clunky & unattractive, so we're going to skip it. (not to worry, we'll be using plenty of other pre-made Bootstrap UI components in just a moment)

We'll start w/ a `div` we give the id of `desktopNavWrapper`:

```
<div id="desktopNavWrapper"></div>
```

Within our `desktopNavWrapper `, we'll drop an unordered list of Treehouse's 6 top level navigation items, like this:

```
<ul id="desktopNav">
  <li><a href="#">About Us</a></li>
  <li><a href="#">Our Programs</a></li>
  <li><a href="#">Adopt</a></li>
  <li><a href="#">Caring for Cats</a></li>
  <li><a href="#">Get Involved</a></li>
  <li><a href="#">Support Us</a></li>
</ul>
```

All told, your desktop nav should look like this:

```
<!-- desktop nav wrapper -->
<div id="desktopNavWrapper">
  
  <!-- desktop nav -->
  <ul id="desktopNav">
    <li><a href="#">About Us</a></li>
    <li><a href="#">Our Programs</a></li>
    <li><a href="#">Adopt</a></li>
    <li><a href="#">Caring for Cats</a></li>
    <li><a href="#">Get Involved</a></li>
    <li><a href="#">Support Us</a></li>
  </ul><!-- ./desktop nav -->

</div><!-- ./desktop nav wrapper -->
```

##

### Carousel

On the Bootstrap site, there are many examples of pre-built, common UI components. On the site's 'JavaScript' page, you'll find [this carousel example](http://getbootstrap.com/javascript/#carousel).

Beneath the UI, there is even code you can copy/paste into your site. Keep in mind that the Bootstrap project is entirely open source, so all of this code is legal to use & up for grabs.

First, we'll make a container for our carousel:

```
<div class="container" id="carouselContainer"></div>
```

***
_Worth noting: a Bootstrap page will often have only a single container, within which many stacked rows make up the entire page. In our case, however, we have a few elements we want to span the entire width of the page, thus needing their own container. In the case of our carousel, we need a `container` div with no left or right padding._
***

Within our `carouselContainer `, we'll drop the example carousel HTML. (I've made three modifications to the Bootstrap site's example code for use in our page: 1) I removed the arrows & circles UI, 2) changed the outer div id from `carousel-example-generic` to `carousel` and 3) added the `carousel-fade` class.):

```
<!-- carousel -->
<div id="carousel" class="carousel slide carousel-fade" data-ride="carousel">

  <!-- Wrapper for slides -->
  <div class="carousel-inner" role="listbox">

    <!-- item 1 -->
    <div class="item active">
      <img src="img/carousel/01.jpg" height="550" width="1170" alt="...">
      <div class="carousel-caption">
        <h3>February is Chicago's Spray/Neuter Month</h3>
        <a class="btn btn-default btn-sm" href="#" role="button">Learn More</a>
      </div>
    </div><!-- ./item 1 -->

    <!-- item 2 -->
    <div class="item">
      <img src="img/carousel/02.jpg" height="550" width="1170" alt="...">
      <div class="carousel-caption">
        <h3>3 Stray Kittens, 3 Degrees, 30&deg; Below Wind Chills</h3>
        <a class="btn btn-default btn-sm" href="#" role="button">Learn More</a>
      </div>
    </div><!-- ./item 2 -->

    <!-- item 3 -->
    <div class="item">
      <img src="img/carousel/03.jpg" height="550" width="1170" alt="...">
      <div class="carousel-caption">
        <h3>Hawthorne Race Course Cats, What We're Doing to Help</h3>
        <a class="btn btn-default btn-sm" href="#" role="button">Learn More</a>
      </div>
    </div><!-- ./item 3 -->

  </div><!-- ./carousel-inner -->

</div><!-- ./carousel -->
```

Sliding carousels are rather unattractive and jarring, so I've make ours fade. A quick google search led me to [this](http://codepen.io/Rowno/pen/Afykb) example on CodePen. I've already included its CSS to override the default, sliding behavior. We reference this fading CSS by adding the above-mentioned `carousel-fade` class to our carousel's outermost div.

You'll notice also that there are 'Learn More' buttons in our carousel photo captions. These are also pre-built Bootstrap components, whose code I grabbed from the [buttons section](http://getbootstrap.com/css/#buttons) of Bootstrap's 'CSS' page.

***

_**Carousel Options:** in our `site.js` file, we're dictating the time between item transitions via the following function (note: if your mouse is over the carousel, transitions are paused):_

```
$('.carousel').carousel({
  interval: 4000
})
```

***

### Taking a moment to up our Sublime game

As we've seen, typing CSS-style syntax, followed by the tab key — for instance, `.container` + tab — gives us the full `<div class="container"></div>` line.

For our first row, we want a div that spans all 12 columns of our grid. We'll give this an id of `mission`. So, to make a container w/ a row inside, we type the following:

```
.container>.row
```

Now, hit tab. You should see:

```
<div class="container">
	<div class="row"></div>
</div>
```

Dissecting our syntax, what we're telling Emmet:

1. `.container`: make a div w/ the class `container`
2. `>.row`: go one level deeper and create another div w/ the class, `row`

You get the idea.

Going one bigger, erase the above code that we created. This time, type:

```
.container>.row>col-xs-12#mission
```

Again, hit tab. This time, you should see:

```
<div class="container">
	<div class="row">
		<col-xs-12 id="mission"></col-xs-12>
	</div>
</div>
```

Dissecting `.container>.row>col-xs-12#mission`:

1. `.container`: make a div w/ the class `container`
2. `>.row`: go one level deeper and create another div w/ the class, `row`
3. `>col-xs-12#mission`: go one level deeper and create a div with the class, `col-xs-12` and also the id, `mission`

You can take this concept infinitely far. For instance, the following:

```
.container>.row>.col-xs-6.branding{<img src="logo.jpg">}+.col-xs-6.nav>ul>li.navItem*5>a[#]>{item $}
```

Grants you:

```
<div class="container">
	<div class="row">
		<div class="col-xs-6 branding">
			<img src="logo.jpg">
		</div>
		<div class="col-xs-6 nav">
			<ul>
				<li class="navItem"><a href="#">item 1</a></li>
				<li class="navItem"><a href="#">item 2</a></li>
				<li class="navItem"><a href="#">item 3</a></li>
				<li class="navItem"><a href="#">item 4</a></li>
				<li class="navItem"><a href="#">item 5</a></li>
			</ul>
		</div>
	</div>
</div>
```

***

_**For reference:** Emmet's site has a [cheat sheet](http://docs.emmet.io/cheat-sheet/) that shows you all its available shortcuts._

***

Getting back to making things …

### Main Content Area

First, we need a container for our main content:

```
<div class="container"></div>
```

Next, a row w/in this container:

```
<div class="row"></div>
```

And, to hold our mission statement, a div that spans all 12 columns at any page size. We'll give this div an id of `mission` by writing `.col-xs-12#mission` and hitting tab:

```
<div class="col-xs-12" id="mission"></div>
```

Within this column div, we want for our statement to stand out, so we'll wrap it in `h2` tags:

```
<h2>Tree House is a cageless, no kill humane organization specializing in the rescue and rehabilitation of sick and injured stray cats.</h2>
```

Our main content container should now look like this:

```
<!-- main content container -->
<div class="container">

  <!-- mission -->
  <div class="row">
    <div class="col-xs-12" id="mission">
      <h2>Tree House is a cageless, no kill humane organization specializing in the rescue and rehabilitation of sick and injured stray cats.</h2>
    </div>
  </div><!-- ./mission -->
  
</div><!-- ./main content container -->
```

Just beneath the closing `</div><!-- ./mission -->`, we're going to add another row that contains three column divs:

```
<div class="row"></div>
```

Each of these three divs will span all 12 columns at our `-xs-` width, but only 4 columns at our `-sm-` width and larger. So, within our new `row` div, we type `.col-xs-12.col-sm-4`, and then tab. You should see the following:

```
<div class="col-xs-12 col-sm-4"></div>
```

Within this column div, we're going to place three thumbnail components. Looking to the [custom content](http://getbootstrap.com/components/#thumbnails-custom-content) section of Bootstrap's 'components' page, again, we find both the UI and associated code we need.

```
<!-- love -->
<div class="col-xs-12 col-sm-4">
  <div class="thumbnail">
    <img src="http://placekitten.com/g/400/200" alt="">
    <div class="caption">
      <h3>Come and Get Your Love</h3>
      <p>Come and Get Your Love! This Valentine's day weekend (February 13th-15th), visit us for our Love promotion!</p>
      <p><a href="#" class="btn btn-default" role="button">Learn More</a></p>
    </div>
  </div>
</div><!-- ./love -->
```

With only slight modifications — I've removed one of the two buttons, dropped in placeholder images from placekitten.com and copy taken from the [Tree House site](www.treehouseanimals.org) — we've created our first thumbnail.

We can copy/paste this block to create two more columns, replacing the copy with corresponding content from the tree house site:

```
<!-- love -->
<div class="col-xs-12 col-sm-4">
  <div class="thumbnail">
    <img src="http://placekitten.com/g/400/200" alt="">
    <div class="caption">
      <h3>Come and Get Your Love</h3>
      <p>Come and Get Your Love! This Valentine's day weekend (February 13th-15th), visit us for our Love promotion!</p>
      <p><a href="#" class="btn btn-default" role="button">Learn More</a></p>
    </div>
  </div>
</div><!-- ./love -->

<!-- new shelter -->
<div class="col-xs-12 col-sm-4">
  <div class="thumbnail">
    <img src="http://placekitten.com/g/400/281" alt="">
    <div class="caption">
      <h3>Our New Shelter</h3>
      <p>We’re planning to design and build a new, state-of-the-art, environmentally friendly Adoption Center and low-cost Veterinary Clinic in Chicago. We have already acquired a site for the project, but we need your support to raise funds for the construction.</p>
      <p><a href="#" class="btn btn-default" role="button">Learn More</a></p>
    </div>
  </div>
</div><!-- ./new shelter -->

<!-- tree house app -->
<div class="col-xs-12 col-sm-4">
  <div class="thumbnail">
    <img src="http://placekitten.com/g/400/260" alt="">
    <div class="caption">
      <h3>Tree House Smartphone App</h3>
      <p>Tree House introduces PetSpotter, a revolutionary iPhone application that takes advantage of the features of the world's most popular smartphone to help pet guardians report and locate lost pets.</p>
      <p><a href="#" class="btn btn-default" role="button">Learn More</a></p>
    </div>
  </div>
</div><!-- ./tree house app -->
```

### The homestretch: Three Buttons & a Footer

First, a wrapper div for our three buttons:

```
<div id="threeButtonsWrapper"></div>
```

Within our wrapper div, we'll place three buttons, once again borrowed from the [buttons](http://getbootstrap.com/css/#buttons) section of our the 'CSS' page on the Bootstrap site:

```
<button type="button" class="btn btn-default">Donate</button>
<button type="button" class="btn btn-default">Email Newsletter</button>
<button type="button" class="btn btn-default">Share</button>
```

Next up, a footer containing two divs sporting the IDs of `socialButtons` and `bottomThreeLinks`, respectively.

We can create these, individually, or all in one shot using the following syntax, followed by a press of the tab key:

```
footer>#socialButtons+#bottomThreeLinks
```

Remember, this reads:

* `footer`: create a footer element
* `>#socialButtons`: go one level deep and create a div w/ the id `socialButtons`
* `+#bottomThreeLinks` at this same level, create a div w/ the id `bottomThreeLinks`

A press of the tab key should create the following:

```
<footer>
	<div id="socialButtons"></div>
	<div id="bottomThreeLinks"></div>
</footer>
```

Within our social buttons we'll be dropping some icons granted us via Font Awesome's [icons page](http://fontawesome.io/icons/):

```
<i class="fa fa-facebook-square"></i>
<i class="fa fa-twitter-square"></i>
<i class="fa fa-vimeo-square"></i>
<i class="fa fa-pinterest-square"></i>
<i class="fa fa-instagram"></i>
<i class="fa fa-flickr"></i>
<i class="fa fa-youtube-play"></i>
```

Further, let's wrap them within `<a>` tags and link to Tree House's verious social media properties:

```
<a href="https://www.facebook.com/pages/Tree-House-Humane-Society/141825113026" target="_blank"><i class="fa fa-facebook-square"></i></a>
<a href="https://twitter.com/treehousecats" target="_blank"><i class="fa fa-twitter-square"></i></a>
<a href="https://vimeo.com/treehousevideos" target="_blank"><i class="fa fa-vimeo-square"></i></a>
<a href="https://www.pinterest.com/treehousecats/" target="_blank"><i class="fa fa-pinterest-square"></i></a>
<a href="https://instagram.com/treehousecats/" target="_blank"><i class="fa fa-instagram"></i></a>
<a href="https://www.flickr.com/photos/treehousecats/" target="_blank"><i class="fa fa-flickr"></i></a>
<a href="https://www.youtube.com/user/treehousecats" target="_blank"><i class="fa fa-youtube-play"></i></a>	
```

Finally, w/in our `#bottomThreeLinks` div, drop in the last of our content:

```
<div class="bottomLink"><a href="#">Privacy Policy</a></div> | 
<div class="bottomLink"><a href="#">Contact Us</a></div> | 
<div class="bottomLink"><a href="#">Login</a></div>
```

***

### One Last thing: mobile nav

Remember hamburgler.js? A quick visit to its [page](http://johnm.com.au/hamburgler/) shows us just how easy it makes adding a mobile, 'hamburger' style nav to our page.

A quick copy/paste of the example code & we're basically good to go. I've added only the `mobileNavLink` class for styling, and changed the names of the links to mirror those of our desktop nav.

Simply paste the following above our opening `<header>` tag:

```
<!-- hamburgler menu --> 
<div class="mobilenav"> 
  <li><a class="mobileNavLink" href="#">About Us</a></li> 
  <li><a class="mobileNavLink" href="#">Our Programs</a></li> 
  <li><a class="mobileNavLink" href="#">Adopt</a></li> 
  <li><a class="mobileNavLink" href="#">Caring for Cats</a></li> 
  <li><a class="mobileNavLink" href="#">Get Involved</a></li> 
  <li><a class="mobileNavLink" href="#">Support Us</a></li> 
</div><!-- ./hamburgler menu -->

<!-- hamburgler icon --> 
<a href="javascript:void(0)" class="icon"> 
   <div class="hamburger"> 
     <div class="menui top-menu"></div> 
     <div class="menui mid-menu"></div> 
     <div class="menui bottom-menu"></div> 
   </div> 
</a><!-- hamburgler icon -->
```

Aaaaaaand, we're done.