[![Build Status](https://travis-ci.org/dhowe/RiTaJS.svg?branch=master)](https://travis-ci.org/dhowe/RiTaJS)

### RiTaJS: a generative language toolkit for JavaScript


<a href="https://rednoise.org/rita"><img height=80 src="https://rednoise.org/rita/img/RiTa-logo3.png"/></a>

#### [The RiTa website](http://rednoise.org/rita)

RiTaJS is designed to an easy-to-use toolkit for experiments
in natural language and generative literature, based on the RiTa
(http://rednoise.org/rita) library for Java. Like the original RiTa, RiTaJS
works alone or in conjunction with ProcessingJS, P5.js, or as Node or Bower modules.  All RiTa and RiTaJS tools
are free/libre/open-source according to the GPL (http://www.gnu.org/licenses/gpl.txt).



#### About the project
--------
* Author:           Daniel C. Howe (https://rednoise.org/daniel)
* Related:          RiTa -> https://github.com/dhowe/RiTa
* License:          GPL (see included [LICENSE](https://github.com/dhowe/RiTaJS/blob/master/LICENSE) file for full license)
* Web Site:         https://rednoise.org/rita
* Github Repo:      https://github.com/dhowe/RiTaJS/
* Bug Tracker:      https://github.com/dhowe/RiTa/issues
* Reference:    http://www.rednoise.org/rita/reference/

#### A Simple Sketch
--------
Create a new file on your desktop called 'first.html' and download the latest rita.js from [here](http://rednoise.org/rita/download/rita-latest.micro.js), add the following lines, save and drag it into a browser:

```html
<html>
  <script src="https://code.jquery.com/jquery-1.11.2.min.js"></script>
  <script src="./rita-latest.micro.js"></script>
  <script>
    window.onload = function() {
      $('#content').text(RiTa.tokenize("The elephant took a bite!"));
    };
  </script>
  <div id="content" width=200 height=200></div>
<html>
```

#### With [NodeJS](http://nodejs.org/)
--------
To install: `$ npm install rita`

```javascript
var rita = require('rita');
var rs = rita.RiString("The elephant took a bite!");
console.log(rs.features());
```

#### With [p5.js](http://p5js.org/)
--------
Create a new file on your desktop called 'first.html' and download the latest rita.js from [here](http://rednoise.org/rita/download/rita-latest.micro.js), add the following lines, save and drag it into a browser:

```html
<html>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.4.3/p5.min.js"></script>
  <script src="./rita-latest.micro.js"></script>
  <script>
  function setup() {

    createCanvas(200,200);
    background(50);
    textSize(20);
    noStroke();

    var words = RiTa.tokenize("The elephant took a bite!")
    for (var i=0, j = words.length; i<j; i++) {
        text(words[i], 50, 50 + i*20);
    }
  }
  </script>
</html>
```

#### With [Processing.JS](http://processingjs.org)
--------
Create a new file on your desktop called 'first.html' and download the latest rita.js from [here](http://rednoise.org/rita/download/rita-latest.micro.js), add the following lines, save and drag it into a browser:

```html
<html>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/processing.js/1.4.8/processing.min.js"></script>
  <script src="./rita-latest.micro.js"></script>
  <script type="text/processing" data-processing-target="processing-canvas">
    void setup() {

      size(200,200);
      background(50);
      textSize(20);
      noStroke();

      String words = RiTa.tokenize("The elephant took a bite!");
      for (int i=0, j = words.length; i<j; i++) {
          text(words[i], 50, 50 + i*20);
      }
    }
  </script>
  <canvas id="processing-canvas"> </canvas>
</html>
```

#### With [browserify](http://browserify.org/)
--------
Create a file 'main.js' and paste the following code into it
```java
var rita = require('rita');

var rs = rita.RiString("The elephant took a bite!");

console.log(rs.features());
```
Install the [RiTa](https://www.npmjs.com/package/rita) and [browserify](https://www.npmjs.com/package/browserify) modulewith [npm](https://www.npmjs.com/):
```
$ sudo npm install -g rita
$ sudo npm install -g browserify
```
Now recursively bundle up all the required modules starting at main.js into a single file called bundle.js with the browserify command:
```
$ browserify main.js -o bundle.js
```
Browserify parses the AST for require() calls to traverse the entire dependency graph of the project.

Drop a single script tag into html and open it with web browser and inspect the output from developer console
```html
<script src="bundle.js"></script>
```

#### Can I contribute?
--------
Please! We are looking for more coders to help out... Just press *Fork* at the top of this github page and get started, or follow the instructions below...


#### Development Setup
--------
1. Download and install [npm](https://www.npmjs.org/) The easiest way to do this is to just install [node](http://nodejs.org/).
2. [Fork and clone](https://help.github.com/articles/fork-a-repo) this library.

  a. First, login to github and fork the project

  b. Then, from a terminal/shell:

    ```bash
    $ git clone https://github.com/dhowe/RiTaJS.git
    ```
3. Now navigate into the project folder and install dependencies via npm.

  ```bash
  $ cd RiTaJS && npm install
  ```
4. To create the library from src, use gulp.

  ```bash
  $ ./node_modules/.bin/gulp build
  ```

5. Run all tests (in phantomJS) with gulp.

  ```bash
  $ ./node_modules/.bin/gulp test
  ```
6. Work on an existing [issue](https://github.com/dhowe/RiTa/issues?q=is%3Aopen+is%3Aissue+label%3ARiTaJS), then [submit a pull request...](https://help.github.com/articles/creating-a-pull-request)
