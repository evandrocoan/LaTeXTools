# LateXTools: A LaTeX Plugin for Sublime Text 2 and 3

by Ian Bacher, Marciano Siniscalchi, and Richard Stein

**Marciano's blog:**
<http://tekonomist.wordpress.com>

**Documentation:**
<https://latextools.readthedocs.io>

*Latest revision:* v3.15.1 (2018-04-23).

[![Package Control](https://img.shields.io/packagecontrol/dm/LaTeXTools.svg?maxAge=2592000)](https://packagecontrol.io/packages/LaTeXTools)

*Headline features*:

- Documentation migrated to ReadTheDocs (https://latextools.readthedocs.io)
- Support for the import package
- TOC quickpanel now shows just the current document when using (C-r)
- Uses analysis for ref / cite commands and better caching
- Improved fill all completions for large files
- %!TEX directives now override settings in all circumstances

## Prereleases

LaTeXTools uses pre-releases to beta test new features and improve the stability of releases. If you also want to get the newest features and help us testing them. Just open *Preferences > Package Settings > Package Control > Settings - User* and insert at a reasonable (correct JSON syntax) position:

``` js
    "install_prereleases": ["LaTeXTools"],
```

If you also use prereleases of other packages just add them comma separated into the list.


## Overview

This plugin provides several features that simplify working with LaTeX files:

* The ST build command takes care of compiling your LaTeX source to PDF using `texify` (Windows/MikTeX) or `latexmk` (OSX/MacTeX, Windows/TeXlive, Linux/TeXlive). Then, it parses the log file and lists errors and warning. Finally, it launches the PDF viewer and, on supported viewers ([Sumatra PDF](http://sumatrapdfreader.org/free-pdf-reader.html) on Windows, [Skim](http://skim-app.sourceforge.net/) on OSX, and [Evince](https://wiki.gnome.org/Apps/Evince) on Linux by default) jumps to the current cursor position.
* Forward and inverse search with the named PDF previewers is fully supported
* Fill everything including references, citations, packages, graphics, figures, etc.
* Plugs into the "Goto anything" facility to make jumping to any section or label in your LaTeX file(s)
* Smart command completion for a variety of text and math commands
* Additional snippets and commands are also provided
* Fully customizable build command
* Fully customizable PDF viewers
* Full support for project files and multi-file documents
* Easily view package documentation
* Word counts

## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
   wait few seconds until the installation finishes up
1. Now,
   Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Go to the menu **`Tools -> Command Palette...
   (Ctrl+Shift+P)`**
1. Type **`Preferences:
   Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   find the following setting on your **`Package Control.sublime-settings`** file:
   ```js
       "channels":
       [
           "https://packagecontrol.io/channel_v3.json",
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
       ],
   ```
1. And,
   change it to the following, i.e.,
   put the **`https://raw.githubusercontent...`** line as first:
   ```js
       "channels":
       [
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
           "https://packagecontrol.io/channel_v3.json",
       ],
   ```
   * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
     you will not install this forked version of the package,
     but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
   go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
search for **`LaTeXTools`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


Finally, you'll need to have a working TeX installation and a PDF viewer. LaTeXTools supports [MacTeX](https://www.tug.org/mactex/), [MiKTeX](http://www.miktex.org/) and [TeXLive](https://www.tug.org/texlive/) as TeX systems and [Skim](http://skim-app.sourceforge.net/), [Sumatra PDF](http://sumatrapdfreader.org/free-pdf-reader.html), [Evince](https://wiki.gnome.org/Apps/Evince), [Okular](https://okular.kde.org/), and [Zathura](https://pwmt.org/projects/zathura/) as PDF viewers. For detailed instructions on how to set these up, please see [our online documentation](http://latextools.readthedocs.io/en/latest/install/)!

## Bugs, issues & feature requests

Please read the [installation instructions](http://latextools.readthedocs.io/en/latest/install/) carefully to ensure you get up and running as quickly as possible. Help for troubleshooting common issues can be found in the [Troubleshooting](#troubleshooting) section at the end of this README. For other bugs, issues or to request new features, please get in touch with us via [Github](https://github.com/SublimeText/LaTeXTools).

**Please** [search for existing issues and pull requests](https://github.com/SublimeText/LaTeXTools/issues/?q=is%3Aopen) before [opening a new issue](https://github.com/SublimeText/LaTeXTools/issues/new).

## Acknowledgements

Additional contributors (*thank you thank you thank you*): first of all, Wallace Wu and Juerg Rast, who contributed code for multifile support in ref and cite completions, "new-style" ref/cite completion, and project file support. Also, skuroda (Preferences menu), Sam Finn (initial multifile support for the build command); Daniel Fleischhacker (Linux build fixes), Mads Mobaek (universal newline support), Stefan Ollinger (initial Linux support), RoyalTS (aka Tobias Schidt?) (help with bibtex regexes and citation code, various fixes), Juan Falgueras (latexmk option to handle non-ASCII paths), Jeremy Jay (basic biblatex support), Ray Fang (texttt snippet), Ulrich Gabor (tex engine selection and cleaning aux files), Wes Campaigne and 'jlegewie' (ref/cite completion 2.0!). **Huge** thanks to Daniel Shannon (aka phyllisstein) who first ported LaTeXTools to ST3. Also thanks for Charley Peng, who has been assisting users and generating great pull requests; I'll merge them as soon as possible. Also William Ledoux (various Windows fixes, env support), Sean Zhu (find Skim.app in non-standard locations), Maximilian Berger (new center/table snippet), Lucas Nanni (recursively delete temp files), Sergey Slipchenko (`$` auto-pairing with Vintage), btstream (original fill-all command; LaTeX-cwl support), Richard Stein (auto-hide build panel, jump to included tex files, LaTeX-cwl support config, TEX spellcheck support, functions to analyze LaTeX documents, cache functionality, multiple cursor editing), Dan Schrage (nobibliography command), PoByBolek (more biblatex command), Rafael Lerm (support for multiple lines in `\bibliography` commands), Jeff Spencer (override keep_focus and forward_sync via key-binding), Jonas Malaco Filho (improvements to the Evince scripts), Michael Bar-Sinai (bibtex snippets).

*If you have contributed and I haven't acknowledged you, email me!*
