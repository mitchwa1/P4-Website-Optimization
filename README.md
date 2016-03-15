## Website Performance Optimization portfolio project

Requirements - A Web browser that is capable of running HTML, CSS, and JavaScript

####Getting Started: Get a local server running

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8000
  ```

1. Open a browser and visit localhost:8000
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.  Note that I installed Ngrok via HomeBrew to manage package installation.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8000
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

####Part 1: index.html Optimization

The following opimizations were made in order to achieve a PageSpeed score of 95/100 for mobile, and 97/100 for Desktop.

1. Begin by navigating to the main folder in your Terminal and starting a Python Web Server and NGrok (mentioned above)

1. Optimized and Compressed all images via ImageOptim.
1. Made Pizzeria.jpg a thumbnail image.
1. Removed the Google Fonts link - no noticeable effect on page style.
1. Set google analytics script as async so it is not part of the critical rendering path.
1. Media type was changed to print on the CSS for print media. This way it is not render blocking.
1. Moved the css for screen inline in the index.html. This saves time by not needing to put out a request for a separate file.
1. Minified CSS style and print sheets.
1. Added .htaccess in order to leverage browser caching.

####Part 2: views/pizza.html - Cam's Pizzeria Optimization

The following opimizations were made in order to achieve a Frame Rate of 60 FPS by using: NGrok, ImageOptum, Grok, Chrome Dev. Tools, CSS/HTML/JavaScript Optimization and Minification tools.

1. Begin by navigating to the views folder in your Terminal and starting a Python Web Server and NGrok (mentioned above).

1. Removed sizeSwitcher() and determineDx() functions by adding custom CSS class elements inline of the main.js and style.css files.  I also had to change some of the pizza.html to make this accessible.
1. Used getElementByClassName on changePizzaSizes() function instead of querySelectorAll - I also put the document selector for "randomPizzaContainer" outside of the loop so it only looks it up once.
1. Optimized updatePositions() function by using getElementsByClassName('mover') instead of querySelectorAll. I also made a variable called newScrollTop so the loop has an outside reference.  Inside of the scrolling pizza loop I used transform and translateX instead of "style.left" for display of scrolling pizzas
1. For the movingPizzas1 loop I made an external variable called movePizzas, so there is not a document reference inside of the pizza looper.  I also used getElementById instead of querySelectorAll, and finally changed the number of pizzas to 31 (instead of 200) - because you do not need more than this number to display correctly
1. Added "will-change: transform;" to style.css for: .mover and .randomPizzaContainer - while also adding this to the classes I created inside style.css for "small" "medium" and "large" sizes
1. minified bootstrap-grid.css code
1. Optimized and compressed files in "images" folder using ImageOptum
1. Added .htaccess in order to leverage browser caching.

### Optimization Links and Help

* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). 

* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>