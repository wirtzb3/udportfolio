## Website Performance Optimization portfolio project

The objective was to optimize an online portfolio for speed! In particular, to optimize the critical rendering path and make the page render as quickly as possible by applying the techniques we've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

In part 1, our task was to take a portfolio page and optimize it for the PageSpeed Insight score to reach above 90 for both mobile and desktop.

In part 2, our task was to take a janky, horrible website and make it run consistently at 60FPS.

### Getting started

Some useful tips to help you open my project:

1. Clone my repository https://github.com/wirtzb3/udportfolio
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```
If you want to find PageSpeed Insights for portfolio page:
1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)


### Optimizations for Part 1:
Changes made in udportfolio/index.html

1. Line 11: Took out web fonts because it slowed down performance significantly
2. Line 12: Inlined style.css to eliminate a render-blocking resource request
3. Line 13-25: Add async to all script tags
4. Minified and optimized images in folder


### Optimizations for Part 2:
Changes made in udportfolio/views/js/main.html

1. Line 406: Used a more specific selector to call element (querySelector --> getElementById)
2. Line 444: Used a more specific selector to call element (querySelector --> getElementsByClassName); declared variable and called element before/outside of loop, to be used in loop and initialization of loop
3. Line 445: Took calculation out of loop so calculations would be done before loop
4. Line 496: Took scrolling out of loop so it doesn't force a query every time the loop runs
5. Line 498: Changed querySelectorAll to getElementsByClassName
6. Line 502-505: Made an array to push the phase values to so the sine calculations only have to be done five times, instead of for each item in array
7. Line 511: Used CSS3 transform instead of style.left to avoid triggering layout
8. Line 533: Moved query out of loop, and made query more specific (querySelectorAll --> getElementById)
9. Line 544-546: moved updatePositions into requestAnimationFrame for a more smooth animation
