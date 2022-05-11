# Get started

This is a short step-by-step tutorial to get started with the Sphinx Book Theme.

:::{note}
This documentation and the examples below are written with MyST Markdown, a form
of markdown that works with Sphinx. For more information about MyST markdown, and
to use MyST markdown with your Sphinx website,
see [the MyST-parser documentation](https://myst-parser.readthedocs.io/)
:::

## Prerequisites

You should be relatively familiar with [the Sphinx ecosystem](http://www.sphinx-doc.org/), and have it installed locally on your computer.

:::{note}
If you don't already have a Sphinx site ready to customize, you can create one with:

```bash
sphinx-quickstart
```
:::

## Install and activate the theme

First install `sphinx-book-theme` with `pip`:

```
pip install sphinx-book-theme
```

then, activate the theme in your Sphinx configuration (`conf.py`):

```
...
html_theme = "sphinx_book_theme"
...
```

This will activate the Sphinx Book Theme for your documentation.

:::{note}
You may need to comment-out your `html_theme_options` configuration depending on your previous theme.
:::

## Add a source repository button to your theme

There are several ways that you can customize the Sphinx Book Theme.
For this tutorial, we'll add a pointer to a GitHub repository for our theme.

To add a button that links to the repository for your documentation, add the following configuration in `conf.py`.

```python
html_theme_options = {
    ...
    "repository_url": "https://github.com/{your-docs-url}",
    "use_repository_button": True,
    ...
}
```

When you build your documentation, your header should now include a small GitHub logo that has a link to the repository.


:::{seealso}
See [](source-files:repository) for more information.
:::

## Customize your left sidebar

There are a few major areas of the page that you can customize with the book theme.
The most common is the **primary sidebar** (by default, on the left of the page).

Sidebar elements are defined as HTML templates by Sphinx, Sphinx extensions, and the current theme.
You may specify which pages should contain which sidebar elements using the `html_sidebars` configuration.
We'll skip this step in this tutorial, but if you'd like to learn more, see [](sidebar-primary:items).

Let's **customize the logo of our site**.
To do so, we'll edit the `html_logo` and `html_title` configuration options.

To add a site logo, follow these steps:

1. Put an image in your documentation's root (e.g., `myimage.png`).
2. Add a line to your `conf.py` file that looks like this:

   ```python
   html_logo = "path/to/myimage.png"
   ```

   Where the path is relative to your `conf.py` file.

Next we'll **customize the title of the site**.
To do so, add a line to your `conf.py` file that looks like this:

```python
html_title = "My site title"
```

This title will now be placed underneath the logo.

## Add some margin content to a page

There are a few special kinds of content that this theme supports, largely inspired by [the Tufte CSS theme styles](https://edwardtufte.github.io/tufte-css/).
One kind of content is **margin content**.
This allows you to "pop out" content to the side of the page, in the margins.
Add some margin content to a page by adding the following directive (written with [MyST Markdown](https://myst-parser.readthedocs.io)).

```{margin} Look, some margin content!
On wider screens, this content will pop out to the side!
```

````md
```{margin} Look, some margin content!
On wider screens, this content will pop out to the side!
```
````

On wide screens, margin content will pop out to the side of the page and allow content underneath it to move upwards.
This allows you to provide extra information without interrupting the flow of information.

There are many other things that you can do with the Sphinx Book Theme.
Now that you've gotten a start, check out the other sections to the left to learn more about how to use it.

## JavaScript Code snippet

This is an example of javascript code snippet on markdown

```js
    // Line comments start with two forward slashes. Like this line.

    /* Multi line comments start with a forward slash and a star,
    and end with a star and a forward slash. */

    // Variables are used to store objects, and are defined using the keyword var.
    var the_answer = 42;

    // String objects start and end with a single quote.
    var my_variable = "I am a string";

    // String objects can also start and end with double quotes.
    // But don't mix and match them.
    var my_other_variable = "I am also a string";

    // Statements should end in a semi-colon, or the editor complains.
    var test = "I feel incomplete...";

    // Parentheses are used to pass parameters to functions.
    print("This string will print in the Console tab.");

    // Square brackets are used for selecting items within a list.
    // The zero index refers to the first item in the list.
    var my_list = ["eggplant", "apple", "wheat"];
    print(my_list[0]);

    // Curly brackets (or braces) can be used to define dictionaries (key:value pairs)
    var my_dict = { food: "bread", color: "red", number: 42 };
    // Square brackets can be used to access dictionary items by key.
    print(my_dict["color"]);
    // Or you can use the dot notation to get the same result.
    print(my_dict.color);

    // Functions can be defined as a way to reuse code and make it easier to read
    var my_hello_function = function (string) {
    return "Hello " + string + "!";
    };
    print(my_hello_function("world"));
```

