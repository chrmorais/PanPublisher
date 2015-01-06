PanPublisher
============

A simple BASH wrapper to export a Markdown source to PDF, ePUB, Kindle and more.

Requirements
------------
* Pandoc (1.12 or newer) -- to export Markdown source
* Calibre -- to polish resulting ebooks
* Inkscape -- to convert the raw SVG cover
* TeXlive -- to output pdf (via luaLaTeX)
* fontconfig -- to automagically identify embedded fonts
* Image Magick -- to do some image conversions and to get image sizes

Basic Features
--------------
* Works from a single document containing the markdown source (you only have to edit one file)
* Creates a working directory to store source configuration
* Generates a sensible LaTeX configuration (based on user input) instead of a bland default document
* Generates a basic cover image if you don't have one image ready to use
* Generates ePUB, PDF, Kindle (mobi), Kindle Fire (azw3), OpenDocument (incomplete) and HTML (very basic) versions from the source

Advanced Features
-----------------
* Embeds fonts in ePUB and generates PDF using system fonts as chosen by the user
* Cover image is customisable (colors, fonts, bitmap image to embed)
* ePUB is refactored to include custom `cover.xhtml` and `title_page.xhtml`
* ePUB is polished by Calibre (ebook-polish) and is standardas-compliant
* Metadata is retrieved from source metadata block
* PDF compilation includes graphic cover.

Basic Usage
-----------
1. Put the script in a place in your PATH
2. Put your source document in a directory where you don't mind that a lot of garbage may be created (tip: do not use ~/Destkop or ~/).
3. `panpublish document.md command` (in which "command" can be null, `cover`, `pdf`, `ebook` or `kindle`)
4. null option recreates working directory, splits the source and regenerates some configuration
5. `cover` option builds a basic SVG image, converts it to `.png`, `.pdf` and `.jpg` and generates `cover.xhtml`
6. `pdf` generates a LaTeX source in the working directory and uses luaLaTeX to compile it
7. `ebook` option generates an ePUB ebook (customised and polished)
8. `kindle` option converts an existing ePUB ebook into `.mobi` and `.azw3`
5. `panpublish clean` will remove from the current directory all *.pdf, *.epub, *.odt, *.azw*, *.mobi and *.tex files (very aggressive, use with extreme caution, but I have used "rm -i" to reduce damage).

Planned Features
----------------
* Use GPP to process image inclusion with ImageMagick's identify to get proper sizes
* Inclusion of copyright page
* Inclusion of colophon page somewhere at the end
* Font obfuscation
* Using a custom latex template (must figure out how Pandoc chooses one, as I have not yet succeded in making it use my customised template).
* Better styled OpenDocument and HTML versions
* Use getopts to process user input choices instead of relying on command-line arguments
* Improved `.pdf` output incorporating some TeX hacks and black magic...
