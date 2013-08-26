htmlmerge
=========

__HTML, CSS and Javascript merging tool__  
Merge all linked _css_ and _javascript_ resources of an _html_ file into a
single file.

### Requirements ###
* `Python 2.7`
* `BeautifulSoup v3` python library
* (optional) Google `htmlcompressor`
* (optional) Yahoo `YUIcompressor`

This script was tested on `Gentoo Linux` with `Python 2.7` and `BeautifulSoup3`.


### Install ###
Save `htmlmerge` to your bin path and make it executable.
e.g.

    wget https://raw.github.com/fin-ger/htmlmerge/master/htmlmerge
    mv htmlmerge ~/bin/
    chmod +x ~/bin/htmlmerge

Make sure `~/bin/` is in your `$PATH` variable.

### Usage ###
<code>
htmlmerge infile [options] [-h|--help]

Merge all linked css and javascript resources of an html file into one file

Required arguments:
  infile                Set input html file
                        Use '-' to read piped output from another program

Optional arguments:
  -h, --help            Show short help message and exit
  --long-help           Show this help message and exit
  -v, --version         Show program's version number and exit
  -x, --compress-html   Compress html (Google htmlcompressor required)
  -c, --compile-css     Compile stylesheets (YUIcompressor required)
  -j, --compile-js      Compile javascript (YUIcompressor required)
  -k, --no-css          Disable css merging
  -r, --no-css-import   Disable css @import merging
  -s, --no-js           Disable javascript merging
  -u, --unlock-comments
                        Unlock comments in javascript and css
                        (e.g. /*! ... */ becomes /* ... */)
  -o FILE, --output FILE
                        Set output file (default: merged.html)
                        If the file extension is .gzip the html will be gziped
                        Use '-o -' to pipe output to another program
  -g, --gzip            Force a gziped output. The file extension does not
                        matter.
                        This is useful if you would like to pipe gziped output
  -l VAL, --loglevel VAL
                        Set logging level [quiet|error|warning|info|debug]
                        (default: info)

Javascript and css compiler options:
  YUIcompressor

  -w COLUMN, --line-break COLUMN
                        Insert a line break after the specified column number
                        (default: 500)

Javascript compiler options:
  YUIcompressor

  --nomunge             Minify only, do not obfuscate
  --preserve-semi       Preserve all semicolons
  --disable-optimizations
                        Disable all micro optimizations

Examples:
  htmlmerge index.html
  htmlmerge index.html -x -c -j -o build/out.html -u
  htmlmerge index.html -x --loglevel quiet -k -r -s

For CSS or JavaScript compression, additional YUIcompressor jar file must be
present in the same directory as this script.
For HTML compression, additional Google htmlcompressor jar file must be present
in the same directory as this script.

Copyright (c) Fin Christensen 2013 - All rights reserved!
</code>
### How It Works ###
This script searches for `link`, `style` and `script` tags in the given html
file and looks for `src` or `href` attributes. It will write all scripts into
one single `script` tag and all stylesheets into one single `style` tag.
Stylesheets linked via `@import` will be merged, too. If a media query is given
with `@import` the scripts skips the import because this stylesheet is not
needed for all devices. The generated *merged* html will be written to the given
output file. If there is no output file given the script will save to
`merged.html`.

### Todo ###
* convert small graphics to base64 string
* possibility to compile javascript google-closure-compiler
* possibility to merge `@import`'s with a media query
* possibility to keep merged sources in single tags
* possibility to pass arguments to htmlcompressor
* add a preset system

### Author ###
Fin Christensen

__License__  
*Have a look into `LICENSE`* `MIT`

__Copyright__  
Copyright &copy; Fin Christensen 2013 - All rights reserved!
