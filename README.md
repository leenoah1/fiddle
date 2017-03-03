# jsbin or jsfiddle or blockbuilder?

There are quite a few JavaScript playgrounds.  For our purposes, <http://blockbuilder.org> may be the best.

Note: For debugging code, there's really no substitute for the developer's console.  But be careful with the playgrounds. They use iframes, so you'll probably need to change the execution context accordingly.  See [this stackoverflow post](http://stackoverflow.com/questions/3275816/debugging-iframes-with-chrome-developer-tools) for more info.

Here's how to load Mike Bostock's block <https://bl.ocks.org/mbostock/4062045> in each playground.

# blockbuilder.org

Browse to: <http://blockbuilder.org/mbostock/4062045>.  

That's right, all you have to do is change "https://bl.ocks.org" to "http://blockbuilder.org" in the URL (be careful that https changes to http).  Note: blockbuilder automatically loads data from the gist. There's no need to reconfigure code.

# jsbin.com

Start with the URL for the gist (not the block): <https://gist.github.com/mbostock/4062045>.

Browse to: https://gist.jsbin.com/mbostock/4062045

That's right, all you have to do is change "github" to "jsbin" in the gist's URL. But...

1. You'll have to change the URL for the data. In this case, change one line

        d3.json("miserables.json", function(error, graph) {

    to

        var url = "https://gist.githubusercontent.com/mbostock/4062045/raw/5916d145c8c048a6e3086915a6be464467391c62/";
        d3.json(url + "miserables.json", function(error, graph) {
  
1. jsbin.com also seems to have a little trouble loading the files. For example, in my experience, the JavaScript window has some stray characters "sadfsdfsafsdsdsadf" that might cause problems.

# fiddle

JSFiddle.com has a nice collaborative mode, but it's the most difficult to configure for loading gists.  The files in this repo have been set up to load automatically in JSFiddle. To open the repo in JSFIddle, click:

<http://jsfiddle.net/gh/get/library/pure/umbcvis/fiddle/tree/master/>

The files used by JSFiddle:

* demo.html (html without boilerplate tags: doctype, html, meta, etc.)
* demo.css (CSS only)
* demo.js (JavaScript only)
* demo.details (manifest for configuring remote resources, such as d3.v4.min.js)
* miserables.json (data served from the master branch)

For more info, see <a href="http://doc.jsfiddle.net/use/github_read.html">JSfiddle guidelines</a>. In addition, several important modifications in ```demo.js``` were changed to make it work well...

* window.onload -- the callback contains all the code from the block (otherwise d3.js loads after the code)
* svg -- the ```viewBox``` attribute and CSS ```width: 100%``` scale things to fit in the JSFiddle frame
* miserables.json -- served locally from this github project's website

# github project site

index.html (not used by JSFiddle) opens the JSFiddle files directly from this umbcvis github project's page:

<https://umbcvis.github.io/fiddle/>

See the [Github documentation](https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/)
for guidance on configuring gh-pages to serve files from the master branch.
