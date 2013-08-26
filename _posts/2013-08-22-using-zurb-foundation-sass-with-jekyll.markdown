---
layout: post
title:  "Setting up Zurb Foundation SASS with your Jekyll Blog"
date:   2013-08-22 07:19:00
categories: jekyll sass foundation
---

This post will instruct you on how to setup the SASS version of Zurb Foundation CSS Framework.

1. Download the Foundation framework from http://foundation.zurb.com

2. Place files in appropriate files:

    --css
        foundation.scss
        normalize.scss
        --foundation
            _variables.scss
            --components
                *.scss
        
    --js
        jquery.js
        foundation.js
        custom.modernizr.js

3. Install the SASS gem:

    sudo gem install sass

4. Now we want to compile the .scss files into normal .css files. Make sure you look at the foundation.scss file and ensure you are happy with all of the included components. In a terminal tab, run the SASS watch command in the css folder (or against individual files) in order for them to compile:

    sass --watch css

    or to focus on individual files:

    sass --watch css/foundation.scss css/normalize.scss


5. Include the following files in your _layouts/default.html

    {% highlight html %}

        <!DOCTYPE html>

        <!-- paulirish.com/2008/conditional-stylesheets-vs-css-hacks-answer-neither/ -->
        <!--[if IE 8]>    <html class="no-js lt-ie9" lang="en"> <![endif]-->
        <!--[if gt IE 8]><!--> <html class="no-js" lang="en"> <!--<![endif]-->

        <html>
        <head>

            <meta charset="utf-8" />

            <!-- Set the viewport width to device width for mobile -->
            <meta name="viewport" content="width=device-width" />

            <title>{{ page.title }}</title>

            <link rel="favicon" href="img/favicon.ico">

            <!-- Stylesheets -->
            <link rel="stylesheet" href="css/normalize.css">
            <link rel="stylesheet" href="css/foundation.css">

        </head>

        <body>

            <!-- 
                The following is an example of the Foundation grid.
                This is a good way to determine the success of your SASS compilation
            -->

            <div class="row">

                <!-- The side navigation area -->
                <div class="small-2 columns">

                    <ul class="side-nav">
                        <li class="active"><a href="/">Home</a></li>
                        <li class="divider"></li>
                        <li>Recent Posts</li>
                        <li>
                            <ul class="posts">
                            {% for post in site.posts %}
                            <li><a href="{{ post.url }}">{{ post.title }}</a></li>
                            {% endfor %}
                            </ul>
                        </li>
                        <li class="divider"></li>
                        <li><a href="#">About</a></li>
                        <li><a href="#">Contact Us</a></li>
                    </ul>

                </div>

                <!-- The main content area -->
                <div class="small-10 columns">
                    {{ content }}
                </div>

                </div>

            </div>

            <!-- JavaScripts -->
            <script src="js/vendor/jquery.js"></script>
            <script src="js/foundation/foundation.js"></script>
            <script src="js/vendor/custom.modernizr.js"></script>

        </body>
        </html>

    {% endhighlight %}  


6. In another terminal tab, run the jekyll server command:

    jekyll serve

7. You can now view your website by opening your browser and going to the following address:

    http://localhost:4000/