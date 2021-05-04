# Create your book's source files

Now that we understand our book's structure, let's create a sample book to learn from.

## Quickly generate a sample book

Jupyter Book comes bundled with a lightweight sample book to help you understand a book's structure.
Create a sample book by running the following command:

```
jupyter-book create mynewbook/
```

This will generate a mini Jupyter Book that you can both build and explore locally. It will have a few decisions made for you, and you can explore the configuration of the book in `_config.yml` and its structure in `_toc.yml`. Use this book as inspiration, or as a starting point to work from.

## Investigate your book's content files

First, note that there are at least two different kinds of content files: **markdown** files (ending in `.md`) and **Jupyter Notebooks** (ending in `.ipynb`).

We'll discuss each below.

### Markdown files (`.md`)

Markdown is an example of a [markup language](https://en.wikipedia.org/wiki/Markup_language) - a way to structure text with extra characters and syntax that give it extra meaning (e.g., using `**bold**` to denote **bold**).
It is very popular and used across many different technology platforms.

Markdown files come in slight variations, often called *flavors of markdown*.
There are two flavors of markdown that Jupyter Book supports:

- [CommonMark markdown](https://commonmark.org/) - a markdown standard that is very common.
- [MyST Markdown](../content/myst.md) - an extension of CommonMark with extra functionality for enriched documents.

Let's take a look at one of the markdown files in the template book, `intro.md`:

````md
# Welcome to your Jupyter Book

This is a small sample book to give you a feel for how book content is
structured.

:::{note}
Here is a note!
:::

And here is a code block:

```
e = mc^2
```

Check out the content pages bundled with this sample book to see more.
````

Above you see several different kinds of structure:

- `#` symbols denote **section headers** in CommonMark markdown.
  They define the section headers on this page, for example.
- `:::{note}` is a **directive** in MyST Markdown.
  It is rendered like this:

  :::{note}
  I'm a note!
  :::
- ` ``` ` denotes a **code block** in CommonMark markdown.
  It is rendered like this:

  ```
  e=mc^2
  ```

All content files must have a page title (specified as the first header). All subsequent headers must increase linearly (so no jumps from H1 to H3). See [](rules-all-content-types) for more rules that all content must adhere to.

For more information about MyST markdown and all the things you can do with it, see [](../content/myst.md).


### Jupyter Notebooks (`.ipynb`)

The other type of content we'll note is a **Jupyter Notebook**, ending in `.ipynb`.
Jupyter Notebooks have a combination of computational content and narrative conent.
Each notebook is associated with a **kernel** (aka, Python, R, Julia, etc) that defines the language used to execute the notebook's computational content.

By default, when Jupyter Book builds your book, **notebooks will be executed and their outputs cached**. On subsequent builds, notebook pages will be re-executed only if their code has changed.

:::{margin} ✨Notebooks with text files✨
You can also store Jupyter Notebooks as markdown files or other text files. See [](../file-types/myst-notebooks.md) and [](../file-types/jupytext.Rmd).
:::

Any outputs generated by the notebook will be inserted into your built book (though they may not be in your input notebook). This way you do not need to store the notebook's outputs with your repository. See [](../content/execute.md) for more information.

There are many other interesting things that you can do with notebook content as a part of your book. We recommend checking out [](../content/code-outputs.md) as well as [](../interactive/interactive.md) to get started with Jupyter notebooks.

## Inspect your configuration file

In addition to these content files, your book also has a **configuration file** (`_config.yml`).
This controls the behavior of your book in many ways.

A few decisions have been made for you.
Let's take a look at a few examples:

This snippet configures some metadata about your book, and determins the logo displayed in the top left:

```yaml
# Book settings
# Learn more at https://jupyterbook.org/customize/config.html

title: My sample book
author: The Jupyter Book Community
logo: logo.png
```

This configuration activates **citations** for your book (see [](../tutorials/references.md) for getting started with citations and references).

```yaml
# Add a bibtex file so that we can create citations
bibtex_bibfiles:
  - references.bib
```

This configuration tells Jupyter Book to execute all of your Jupyter Notebook files **every time** the book is re-built, instead of cache-ing them.

```yaml
# Force re-execution of notebooks on each build.
# See https://jupyterbook.org/content/execute.html
execute:
  execute_notebooks: force
```

Check out the other content in your configuration file, and reference it against the pages in this documentation to see what it does.

## Your book's table of contents

Finally, your book also has a **Table of Contents** that tells Jupyter Book where each of your content source files should go.

```yaml
- file: intro
- file: markdown
- file: notebooks
```

This is a simple table of contents, consisting of three pages.
The first item of your ToC is always your book's **landing page** - the first page people will see when they look at your book.

Subsequent pages are defined in sequential order.
You can do a lot more than just define a single list of pages - see [](../customize/toc.md) for more information about structuring your book.

## Create your own content file

Now that you've seen a few sample content files, try creating your own!

In the folder with all of your sample book contents, create a new file called `mymarkdownfile.md`. Put the following content in it:

```md
# Here's my sample title

This is some sample text.

(section-label)=
## Here's my first section

Here is a [reference to the intro](intro.md). Here is a reference to [](section-label).
```

We've added two new pieces of markdown syntax, both of them are related to **cross-references**.

- `(section-label)=` is a label that's attached to a section header. It refers to whatever header follows, and allows you to refer to this label later on in your text.
- `[link text](link-target)` syntax is how you specify a link in markdown. Here we've linked to another page, as well as to the label we created above.

When you build your book, you'll see how these links resolve in the output.

## Next step: build your book

Now that you've got a Jupyter Book folder structure, you can create
the HTML (or PDF) for each of your book's pages. That's covered in the next
section.