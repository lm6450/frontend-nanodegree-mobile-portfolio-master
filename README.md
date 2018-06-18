#Installation
1. Download files from GitHub repository:
https://github.com/lm6450/arcade-game-master
2. Unzip file
3. Open index.html in a browser window

#Modifications
1. Used "use strict" for better framerate
2. Removed the use of determineDx; set var randomPizzas = document.querySelectorAll(".randomPizzaContainer") to avoid code repetition. 

// Iterates through pizza elements on the page and changes their widths
  function changePizzaSizes(size) {
    var newwidth;
      switch(size)  {
        case "1":
          newwidth = 25;
          break;
        case"2":
          newwidth = 33.3;
          break;
        case"3":
          newwidth = 50;
          break;
        default:
          console.log("bug in sizeSwitcher");
      }
    var randomPizzas = document.querySelectorAll(".randomPizzaContainer");
    for (var i = 0; i < randomPizzas.length; i++) {
      // var dx = determineDx(randomPizzas[i], size);
      // var newwidth = (randomPizzas[i].offsetWidth + dx) + 'px';
      randomPizzas[i].style.width = newwidth + "%";
    }
  }

  changePizzaSizes(size);

3. Moved var pizzasDiv outside of the for loop to avoid doing it on every loop

// This for-loop actually creates and appends all of the pizzas when the page loads
var pizzasDiv = document.getElementById("randomPizzas");
for (var i = 2; i < 100; i++) {
  
  pizzasDiv.appendChild(pizzaElementGenerator(i));
}

4. Used an if loop to determine the number of pizzas needed in the backgroung (backPizzas) depending on the size of the screen and related to column width of bootstrap layout

// Generates the sliding pizzas when the page loads.
document.addEventListener('DOMContentLoaded', function() {
  var cols = 8;
  var s = 256;
    var backPizzas = 0;
    if (window.innerWidth >= 1200) {
      backPizzas = 64;
    } else if (window.innerWidth >= 992){
      backPizzas = 48;
    } else if (window.innerWidth >= 768) {
      backPizzas = 32;
    } else {
      backPizzas = 16;
    }

    for (var i = 0; i < backPizzas; i++) {
      var elem = document.createElement('img');
      elem.className = 'mover';
      elem.src = "images/pizza.png";
      elem.style.height = "100px";
      elem.style.width = "73.333px";
      elem.basicLeft = (i % cols) * s;
      elem.style.top = (Math.floor(i / cols) * s) + 'px';
      document.getElementById("movingPizzas1").appendChild(elem);
    }
    updatePositions();
  });

## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository and inspect the code.

### Getting started

#### Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

#### Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js. 

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>
