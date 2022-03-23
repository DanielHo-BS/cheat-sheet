# Introduction

[Sphinx](https://www.sphinx-doc.org/en/master/index.html) is a tool that makes it easy to create intelligent and beautiful documentation, written by Georg Brandl and licensed under the BSD license.


# Usage

    make help --see all options
    make html
    make latexpdf
    make text

## pdf

requiestment

    sudo app install latexmk
    sudo apt install texlive-latex-extra

command 

    make latexpdf


## [docx](https://github.com/amedama41/docxbuilder)

requiestment

    pip install docxbuilder

Add 'docxbuilder' to extensions configuration of conf.py:

    extensions = ['docxbuilder']

You can control the generated document by adding configurations into conf.py:

    docx_documents = [
        ('index', 'docxbuilder.docx', {
            'title': project,
            'creator': author,
            'subject': 'A manual of docxbuilder',
        }, True),
    ]
    docx_style = 'path/to/custom_style.docx'
    docx_pagebreak_before_section = 1

command

    make docx