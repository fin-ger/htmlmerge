htmlmerge
=========

__HTML, CSS and Javascript merging tool__  
Merge all linked _css_ and _javascript_ resources of an _html_ file into a
single file.

### Requirements ###
* `Python 2.7`
* `BeautifulSoup v3` python library

This script was tested on `Gentoo Linux` with `Python 2.7` and `BeautifulSoup3`.


### Install ###
Save `htmlmerge` to your bin path and make it executable.
e.g.

    wget https://raw.github.com/fin-ger/htmlmerge/master/htmlmerge
    mv htmlmerge ~/bin/
    chmod +x ~/bin/htmlmerge

Make sure `~/bin/` is in your `$PATH` variable.

### Usage ###
    htmlmerge [-h] [-v] [-o FILE] [-l VAL] infile
    
    Merge all linked css and javascript resources of an html file into one file
    
    positional arguments:
      infile                set input html file
    
    optional arguments:
      -h, --help            show this help message and exit
      -v, --version         show program's version number and exit
      -o FILE, --output FILE
                            set output html file (default: merged.html)
                            use '-o -' to pipe output to another program
      -l VAL, --loglevel VAL
                            set logging level [quiet|error|warning|*info|debug]
    
    examples:
      htmlmerge index.html
      htmlmerge index.html -o build/out.html
      htmlmerge --loglevel quiet index.html

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

### Author ###
Fin Christensen

__License__  
*Have a look into `LICENSE`* `MIT`

__Copyright__  
Copyright &copy; Fin Christensen 2013 - All rights reserved!
