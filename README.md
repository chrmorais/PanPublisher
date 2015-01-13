PanPublisher
============

A simple BASH wrapper to export a Markdown source to PDF, ePUB, Kindle and more.

Requirements
------------
* Pandoc (1.12 or newer) -- to export Markdown source
* Calibre -- to polish resulting ebooks
* Inkscape -- to convert the raw SVG cover
* TeXlive -- to output pdf (via luaLaTeX)
* GGP -- for conditional processing (which is optional)
* fontconfig -- to automagically identify embedded fonts
* Image Magick -- to do some image conversions and to get image sizes
* Standard unix tools (sed, awk, grep, cut, cat, head, etc.)

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
3. `panpublish options document.md` (in which "command" options can be
* -x, --clean-output-dir   Removes output files in working directory
* -f, --clean-output-files Removes output files in current directory
* -d, --prepare-directory  Creates/updates working directory
* -c, --cover              Creates/updates basic cover
* -t, --texconfig          Creates/updates latex config for PDF
* -p, --pdf                Creates/updates pdf document
* -e, --epub               Creates/updates ePUB ebook
* -k, --kindle             Converts ePUB to kindle formats
* -m, --xhtml              Exports to basic xHTML
* -o, --odt                Exports to OpenDocument
* -u, --update-directory   Regenerates working directory
* -b, --backup             Creates/recreates a backup of working directory
* -h, --help               Shows this message
* -l, --license            Shows license information
* -D, --show-deps          Shows which software is used by this script

Planned Features
----------------
* Inclusion of copyright page
* Inclusion of colophon page somewhere at the end
* Font subsetting and obfuscation
* Better styled OpenDocument and HTML versions
