# Getting started

This template is based on [Mkdocs Material](https://squidfunk.github.io/mkdocs-material/), a static site generator geared towards (technical) project documentation. And uses Python to generate static site and other plugins to generate PDFs of user manual.

## Setup
To set up the document enviorment require:

- Python >= 3.10.5
- [GTK3 Runtime](https://github.com/tschoonj/GTK-for-Windows-Runtime-Environment-Installer/releases) (Windows only, for pdf generation)

Once you have above fufilled, run
``` shell
pip install requirements.txt
```
under this project's root dir.

After installation complete, make sure all requirements installed sucessfully and run
``` shell
mkdocs serve
```
under the root dir of this project, and you should see the document is serving on you local machine.

## Adding Content

Generally just add new content file under `docs` folder, new content should be detedcted and auto generated. For more advanced content control, please refer to [Mkdocs Redirect](https://github.com/mkdocs/mkdocs-redirects/tree/master), and add custom structure in `mkdocs.yml`.

All contents are written in `.md` file, if you don't know what Markdown is, [please learn](https://www.markdownguide.org/). And this template also support many extention features, you can refer [here](https://squidfunk.github.io/mkdocs-material/setup/extensions/).

## Generating

This template can generate static site and PDF file for distributing,.

### Static Site

Run 
```
mkdocs build
```
and the static site bundle will be generated under `site/`.

### PDF

PDF generaion is backed by a plugin, so you need to edit `mkdocs.yml` to turn the feature on. Uncomment `with-pdf` config
``` yml
plugins:
  - search:
      separator: '[\s\-,:!=\[\]()"`/]+|\.(?!\d)|&[lg]t;|(?!\b)(?=[A-Z][a-z])'
  - minify:
      minify_html: true
  # - with-pdf:
  #     # cover_subtitle: 
  #     # cover_logo: 
  #     toc_level: 2
  #     two_columns_level: 3
  - offline
```
and when you `serve` or `build`, the PDF file will be generated.

!!! warning "Generating PDF really takes time"

    Generation of only two file document will take ~1 miniute, if your docs are large please wait with patient. not recommed to constantly generating PDFs. 

You will find pdf in `site/pdf/` if you are using `build`.