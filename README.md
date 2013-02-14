# SublimePelican: Pelican integration to Sublime Text 2

**SublimePelican** is a plugin for [Pelican](http://getpelican.com/) integration to [Sublime Text 2](http://www.sublimetext.com/2).

The plugin prepares metadata fields for you, with the ability to fill in date and slug fields automatically.

## Installation

You can install the SublimePelican plugin with or without Git.
Support for the [Package Control plugin](http://wbond.net/sublime_packages/package_control) is pending pull request.

### Installation without Git

1.  Download the [latest source from GitHub](https://nodeload.github.com/jsliang/sublime-pelican/zip/master).
2.  Copy the `sublime-pelican-master` folder to your **Sublime Text 2 "Packages" directory**.
3.  Renamed the `sublime-pelican-master` folder to `Pelican`.

The **Sublime Text 2 "Packages" directory** is located at:

-   OS X: `~/Library/Application Support/Sublime Text 2/Packages/`
-   Linux: `~/.config/sublime-text-2/Packages/`
-   Windows: `%APPDATA%/Sublime Text 2/Packages/`

### Installation with Git

Clone this repository into your **Sublime Text 2 "Packages" directory**:

    git clone https://github.com/jsliang/sublime-pelican.git
    mv sublime-pelican Pelican

which is equivalent to:

    git clone https://github.com/jsliang/sublime-pelican.git Pelican

The **Sublime Text 2 "Packages" directory** is located at:

-   OS X: `~/Library/Application Support/Sublime Text 2/Packages/`
-   Linux: `~/.config/sublime-text-2/Packages/`
-   Windows: `%APPDATA%/Sublime Text 2/Packages/`

## Usage

### Access commands from Command Palette

1.  After installation, bring up the Command Palette (OS X: `Command+Shift+P` on OS X, Linux/Windows: `Control+Shift+P`).
2.  Type `Pelican` in Command Palette to view a list of available commands.

### Access commands from Context Menu

Right click on a file being edit, and access the commands under the **Pelican** item.

## SublimePelican Commands

*   **Pelican: New Article (Markdown)** and **Pelican: New Article (reStructuredText)**

    These commands open a new article and have metadata fields prepared for you.

    Metadata are generated according to your metadata template.
    Refer to [Settings](#settings) > [Customizable metadata template](#customizable-metadata-template) for instructions on metadata template customization.

*   **Pelican: Insert Metadata**

    This command inserts metadata field to current article.

    Metadata fields are inserted in the same order as your metadata template.
    Fields not listed in the metadata template are preserved too.

*   **Pelican: Update Article Date**

    This command updates the date metadata field to current date and time.

*   **Pelican: Update Slug using Title**

    This command generates the slug field from article title.

## Settings

For the latest information on what SublimePelican settings are available, select the menu item Preferences > Package Settings > Pelican > Settings - Default.

DO NOT edit the settings in "Settings - Default" as changes will be lost when SublimePelican is updated.
Instead, customize your settings in Preferences > Package Settings > Pelican > Settings - User.

### Smart metadata fields generation

#### Slug generation

*   **force_slug_regeneration**

    By default, slug is not automatically generated if a slug has been defined in the article.
    Set to `true` to force slug regeneration.

    Default value: `false`

*   **generate_slug_from_title**

    -   Set to `"none"` to disable slug generation

    -   Set to `"title_change"` to generate slug when article title changes

        Note that when set to `"title_change"`, slug will be regenerated everytime you type in the title line, even if `force_slug_regeneration` is set to `false`.

    -   Set to `"save"` to generate slug on save

        By default, slug is not automatically generated if a slug has been defined in the article.
        This is to prevent unwanted slug change.
        If you want to force slug regeneration on each save, you have to set `force_slug_regeneration` to `true`.

    Default value: `"save"`

### Customizable metadata template

*   **article_metadata_template**

    Metadata template for Markdown & reStructuredText articles.

    Default value:

```
{
    // Metadata template for Markdown articles
    "md":
        [
            "title: %(title)s",
            "slug: %(slug)s",
            "date: %(date)s",
            "tags: %(tags)s",
            "category: %(category)s",
            "author: %(author)s",
            "lang: %(lang)s",
            "summary: %(summary)s"
        ],

    // Metadata template for reStructuredText articles
    "rst":
        [
            ":title: %(title)s",
            ":slug: %(slug)s",
            ":date: %(date)s",
            ":tags: %(tags)s",
            ":category: %(category)s",
            ":author: %(author)s",
            ":lang: %(lang)s",
            ":summary: %(summary)s"
        ]
}
```

### Others

*   **filepath_filter**

    Filename filter for Pelican articles, written in a Python regular expression.
    This is to prevent automatic slug generation annoyly effects other Markdown/reStrcturedText files that are not Pelican articles.

    By default, only Markdown/reStructuredText files under `content/` directory are deemed as Pelican article files.

    Default value: `"content/.*\\.(md|markdown|mkd|rst)$"`


## TODOs

* Build system integration
* Auto-completions for categories / tags
* More flexible **filepath_filter**: automatically retrieve the value of `INPUTDIR` variable from Pelican directory's `Makefile`
* Slug generation for non-ascii characters (unidecode?)

## License

SublimePelican is licensed under the MIT license.

Copyright (c) 2013, Jui-Shan Liang &lt;jenny@jsliang.com&gt;

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.