[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# Rails Assets

Learn how to properly use CSS, JS and Images with our Rails applications.

## Objectives

By the end of this, developers should be able to:

- Leverage the asset pipeline for managing assets
- Include Sass stylesheets with a project
- Include JS code with a project
- Reference images in HTML and CSS using asset pipeline


## Asset Pipeline

The asset pipeline provides a framework to concatenate and minify or compress JavaScript and CSS assets. It also adds the ability to write these assets in other languages and pre-processors such as CoffeeScript, Sass and ERB. It allows assets in your application to be automatically combined with assets from other gems.

The first feature of the pipeline is to concatenate assets, which can reduce the number of requests that a browser makes to render a web page. Web browsers are limited in the number of requests that they can make in parallel, so fewer requests can mean faster loading for your application.

The second feature of the asset pipeline is asset minification or compression. For CSS files, this is done by removing whitespace and comments. For JavaScript, more complex processes can be applied. You can choose from a set of built in options or specify your own.

The third feature of the asset pipeline is it allows coding assets via a higher-level language, with precompilation down to the actual assets. Supported languages include Sass for CSS, CoffeeScript for JavaScript, and ERB for both by default.

## CSS

The manifest file for CSS is the `app/assets/stylesheets/application.css`.  This can be considered the root file for all of your styles.

To include other files, Rails uses the `*=` notation from sprockets.  Generally an application will by default include:
```
 *= require_tree .
 *= require_self
 ```
 
**`*= require_tree .`**

Include all files in the the `app/assets/stylesheets/` folder.

 
**`*= require_self`**

Include any styles written in the `application.css` itself.  Although for the most part, we should not rely on writing styles in the `application.css` directly because they will override all other styles and can be better organized in other files.

**`*= require books`**

If we do not want to use `require_tree .` we can include files individually by using their filename.  This is also useful for when we need to include files from other libararies that are not in our `app/assets/stylesheets/` folder.

### Pro-Tip

CSS cascading and specificity can be tricky when all of the styelsheets are compiled to one file. 

Add classes to the body of your `application.html.erb` so that you can namespace your styles with classes:
```html 
<body class="<%= controller_name %> <%= action_name %>">
  <%= yield %>
</body>
```

For the PostsController#Index, this would result in: 
```html
<body class="posts index">
```

So you can style specifically for any `posts` controller views with:
```css
.posts {}
```

Or for specifically the `posts#index` view with:
```css
.posts.index {}
```

## JS

## Images
