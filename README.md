# OldSkool - Bootstrap 5 HTML Responsive Template

## Overview
OldSkool is a modern & flexible responsive HTML Bootstrap 5 template with customizable card listings on the category page and an excellent product display on the individual product page. It's the perfect starting point for any fashion retail website, and the template's clean and minimal design means it's easy to modify and painless to integrate with your custom Ecommerce application. And above all, it's free!

![Bootstrap 5 Responsive HTML Fashion Store Template](https://pixelrocket-public-assets.s3.eu-west-2.amazonaws.com/github-assets/oldskool-html/homepage-medium.jpg "OldSkool | Responsive Bootstrap 5 Ecommerce Template")

## Demo
[Demo](http://example.com/)

**Please note that this is an HTML template only. It does not connect to a database, and will not automatically work in a content management system (Wordpress etc). You will need to incorporate our code into your application.**

## Template Pages
The template consists of 3 pages:

* Homepage
* Category page
* Product page

To keep code repetition to a minimum, we've used Handlebars.js as the templating engine and partials to quickly add the same code to different pages. We also use a Handlebars plugin for JSON data - this allows us to use loops and output a single HTML code block instead of repeating the same HTML.


## OldSkool Key Features
In addition to all the Bootstrap components and features, OldSkool also offers the following custom components:

* Homepage slideshow (using Swiper.js)
* Brand logo marquee 
* Homepage featured categories (using Swiper.js)
* Instagram slideshow (Swiper.js)
* Category listing card showing sale badge, new product badge and sold out badge
* Custom pagination component
* Header Megamenu
* Customer review component
* Related products slideshow
* Offcanvas category filter display
* Header cart drop down display
* Slidedown search bar


## Build Tool
We used Webpack 4 to compile and build the template. [You can read more about Webpack here](https://webpack.js.org/).

There are two commands for you to run for Webpack:

```
npm start
```
This starts the Webpack devserver. It will automatically open the site in your browser. Any time you save a file, the browser will refresh. Be aware that if you amend the JSON data, or add a new file after starting Webpack devserver, you may have to restart Webpack for it to pickup the new file/data change.

```
npm run build
```
This builds your template. It uses the files located in the src folder and outputs the compiled files to the dist folder.

## Bootstrap Documentation
Bootstrap already has a comprehensive documentation site that will guide you in setting up and using all default Bootstrap features. Bootstrap 5 is fully integrated to our template's source code. Please refer to Bootstrap's doc site first for any default Bootstrap features: [Visit Bootstrap's Doc Site](https://getbootstrap.com/docs/5.0/getting-started/introduction/)


## File structure
📁 dist - Generated version of the template. Go here if you do not want to work with the template source code. But be warned: if you customise anything in this folder directly, and then later recompile the template using webpack, unless you move the dist folder out of the template, your changes will be overridden.

📁 node_modules - Directory where NPM installs dependancies. You will not see this folder until you complete the template installation. You do not need to create this folder.

📁 src - Template source code. Go here to customise your template.

📁 assets - Template assets such as CSS, JS, Images etc.

📁 data - Template JSON Data files. We use these JSON files to make your job easier to insert content into the template. 

📁 html - Template pages. Go here to edit existing pages or add new pages.

📁 partials - Handlebars partial templates. 


## Requirements
If you do not intend to work with the template source code (and that means you will not be compiling it or running the Webpack dev server), you do not need to install anything. You can simply navigate to the dist folder and start editing the files.

Most developers will be editing the source code and will also be running Webpack to compile the template. If that's the case, then ensure that you have Node.js installed. [You can download it from here](https://nodejs.org/en/download/)

That's all you need to have pre-installed. You can now open the main template folder with your command line.

## Installation & Build
You only need to do the following steps if you intend to run Webpack and recompile the template. Please also ensure that you have Node.js installed.

Step One: open up the template folder in your command line. Ensure you are inside the root of the template.

Step Two: in your command line, run npm install. This will install all the dependancies listed in your package.json file.

Step Three: in your command line, run npm start. That's it. Your browser will now open and the "dev" version of the site will be loaded.

## Handlebars Partials
Handlebars is a template engine that allows us to keep our template source code as organised and as clean as possible. It cuts down on code duplication and through the use of helper functions, allows template developers to very quickly output large amounts of data with minimal code. [You can read more about it here](https://handlebarsjs.com).

We use Handlebars for two main reasons: firstly, the use of Handlebars partials allows us to reference the same file in multiple HTML files and means that you only have to edit the code from a single source. If you're used to working with React or Vue, this would be the same as referencing a component. Secondly, the use of JSON data for our dummy catalogue data keeps our template code clean. We can easily output 10 dummy products on our listing page by outputting a basic Handlebars loop.

## Example Handlebars Partial
Open the following file in our template: src/html/index.html.

Around line 21 you'll see the following code:
```
{{> swiper/swiper-homepage-hero }}
```
That's a Handlebars partial. That code tells Handlebars to look inside a folder called swiper (located in the partials folder) and then to find a file called swiper-homepage-hero and insert it into the index.html file when it is compiled.

There are a few important notes about our use of Handlebars partials:

* All of our partials are stored inside src/partials. Do not place partials anywhere else.
* We use .html as our partial file extension. We have also added .svg as a valid partial file extension.
* If you have folders within folders inside your partial folder, only reference the folder the partial resides in. So "partials/header/navbars/navbar.html" would be referenced as "navbars/navbar".
* Do not include the partial file extension. Note in the example above that we output "swiper-homepage-hero" and not "swiper-homepage-hero.html"

## Handlebars Loops
Let's look at how we use Handlebars to keep our code base clean. Open up the category page: src/html/category.html. 

Around line 40, you will find this code:
```
{{#if (config category-products)}}
    {{#each category-products.entries}}
        <div class="col-12 col-sm-6 col-lg-4">
            {{> listing-cards/listing-card this }}
        </div>
    {{/each}}
{{/if}}
```
And that's our loop for a category page. We're passing in JSON data to our Handlebars loop, then inside the loop we are referencing a Handlebars partial and passing it the data for each loop item:
```
{{> listing-cards/listing-card-one this }}
```
## Template Data
The Webpack Handlebars plugin that we use comes with a very handy utility that allows us to pass in JSON files as template data.

Please navigate to: src/data. Here is where our template data JSON files reside. You can edit, remove or add your own to this folder.

Again, if we reference our category page loop:

```
{{#if (config category-products)}}
    {{#each category-products.entries}}
        <div class="col-12 col-sm-6 col-lg-4">
            {{> listing-cards/listing-card this }}
        </div>
    {{/each}}
{{/if}}
```

The important part here with regards to template data is category-products.entries. What this means is that inside our data folder you will find a JSON file called "category-products". This category-products.json file has a "key" called "entries".



## Customise CSS/SASS
All of the template's source CSS/SASS files are kept inside the template's assets folder. Navigate to src/assets/scss. Open up theme.scss with your editor.

This is the main entry point for all other SASS/CSS files.

## Edit/Create HTML Pages
To create a new page, navigate in your code editor to: src/html. To make it easier to get the correct HTML in place, clone an existing page. Rename the newly-created file to whatever URL you require. And that's it. You are now free to open the new page with your code editor, make your changes, and then save the file. Quit Webpack devserver and restart it for the page to show up.

## Credits
[Bootstrap](https://getbootstrap.com/)

[AOS.js](https://michalsnik.github.io/aos/)

[Unsplash](https://unsplash.com/)

[Pexels](https://www.pexels.com/)

[Pixabay](https://pixabay.com/)

[MediumZoom.js](https://github.com/francoischalifour/medium-zoom)

[NoUiSlider.js](https://refreshless.com/nouislider/)

[Simplebar.js](https://github.com/Grsmto/simplebar)

[Swiper.js](https://swiperjs.com/)

## Contact Us
You can find our website [here](https://www.pixelrocket.store) or you can email us at support@pixelrocket.store
