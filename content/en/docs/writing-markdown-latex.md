+++
title = "Writing content with Markdown, LaTeX, and Shortcodes"

date = 2016-04-17
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.
weight = 70

math = true
diagram = true

linktitle = "Writing content"
[menu.docs]
  parent = "content"
  weight = 30
+++

Rich content can be written in Academic using **Markdown**, [**LaTeX math**](https://en.wikibooks.org/wiki/LaTeX/Mathematics), and **Shortcodes**. This article gives an overview of the most common formatting options, including features that are exclusive to Academic.<!--more-->

{{% alert note %}}
*Shortcodes* are plugins which are bundled with Academic or inherited from [Hugo](http://gohugo.io/extras/shortcodes/). Additionally, **HTML** may be written in Markdown documents for advanced formatting.
{{% /alert %}}

## Sub-headings

    ## Heading 2
    ### Heading 3
    #### Heading 4
    ##### Heading 5
    ###### Heading 6

## Emphasis

    Italics with _underscores_.

    Bold with **asterisks**.

    Combined emphasis with **asterisks and _underscores_**.

    Strikethrough with ~~two tildes~~.

## Lists
### Ordered

    1. First item
    2. Another item

### Unordered 

    * First item
    * Another item

### Todo

Todo lists can be written in Academic by using the standard Markdown syntax:

```markdown
- [x] Write math example
- [x] Write diagram example
- [ ] Do something else
```

renders as

- [x] Write math example
- [x] Write diagram example
- [ ] Do something else

## Images

Images may be added to a page by either placing them in your `static/img/` media library or in your [page's folder](https://gohugo.io/content-management/page-bundles/), and then referencing them using one of the following notations:

A figure from your `static/img/` media library:

    {{</* figure library="true" src="image.jpg" title="A caption" lightbox="true" */>}}

A figure within a [page's folder](https://gohugo.io/content-management/page-bundles/) (e.g. `content/post/hello/`) :

    {{</* figure src="image.jpg" title="A caption" lightbox="true" */>}}

A numbered figure with caption:

    {{</* figure src="image.jpg" title="A caption" numbered="true" lightbox="true" */>}}

A general image:

    ![alternative text for search engines](/img/image.jpg)

## Image gallery

**To add an image gallery to a page bundle:**

1. Create a gallery album folder within your [page bundle](https://gohugo.io/content-management/page-bundles/) (i.e. within your page's own folder)
2. Add images to your new album folder
3. Paste `{{</* gallery album="<ALBUM FOLDER>" */>}}` where you would like the gallery to appear in the page content, changing the album parameter to match the name of your album folder

Optionally, to add captions for your images, add the following instances to the end of your page's front matter:

```yaml
gallery_item:
- album: <ALBUM FOLDER>
  image: <IMAGE NAME>.jpg
  caption: Write your image caption here
```

**Alternatively, create an image gallery with images from the internet or your `static/img/` media library:**

1. Add gallery images to within your `static/img/` media library folder
2. Reference your images at the end of the front matter of a content file in the form:

        gallery_item:
        - album: gallery
          image: boards.jpg
          caption: A caption
        - album: gallery
          image: https://raw.githubusercontent.com/gcushen/hugo-academic/master/images/theme-dark.png
          caption: Another caption
    
3. Display the gallery somewhere within your page content by using `{{</* gallery */>}}`

{{% alert note %}}
For *docs* pages (i.e. pages using the courses and documentation layout), gallery images must be placed in the `static/` media library using the second approach (due to limitations of Hugo).
{{% /alert %}}

## Videos

The following kinds of video may be added to a page.

**Local video file**

Videos may be added to a page by either placing them in your `static/img/` media library or in your [page's folder](https://gohugo.io/content-management/page-bundles/), and then referencing them using one of the following notations.

A video from your `static/img/` media library:

    {{</* video library="1" src="my_video.mp4" controls="yes" */>}}
    
A video within a [page's folder](https://gohugo.io/content-management/page-bundles/) (e.g. `content/post/hello/`):

    {{</* video src="my_video.mp4" controls="yes" */>}}

**Youtube**:

    {{</* youtube w7Ft2ymGmfc */>}}

**Vimeo**:

    {{</* vimeo 146022717 */>}}

## Links

    [I'm a link](https://www.google.com)
    [A post]({{</* ref "/post/my-page-name/index.md" */>}})
    [A publication]({{</* ref "/publication/my-page-name/index.md" */>}})
    [A project]({{</* ref "/project/my-page-name/index.md" */>}})
    [A relative link from one post to another post]({{</* relref "../my-page-name/index.md" */>}})
    [Scroll down to a page section with heading *Hi*](#hi)
    
To enable linking to a file, such as a PDF, first place the file in your `static/files/` folder and then link to it using the following form:

    {{%/* staticref "files/cv.pdf" "newtab" */%}}Download my CV{{%/* /staticref */%}}

The optional `"newtab"` argument for `staticref` will cause the link to be opened in a new tab.

### Tags and Categories

Use `{{</* list_tags */>}}` to provide a list of linked tags or `{{</* list_categories */>}}` to provide a list of linked categories.

## Emojis

See the [Emoji cheat sheet](http://www.webpagefx.com/tools/emoji-cheat-sheet/) for available emoticons. The following serves as an example, but you should remove the spaces between each emoji name and pair of semicolons:

    I : heart : Academic : smile :
    
I :heart: Academic :smile:

## Icons

Since **v4.8+**, Academic enables you to use a wide range of [icons from _Font Awesome_ and _Academicons_]({{< relref "page-builder.md#icons" >}}) in addition to [emojis](#emojis).

Here are some examples using the _icon_ shortcode to render icons:

```markdown
{{</* icon name="terminal" pack="fas" */>}} Terminal  
{{</* icon name="python" pack="fab" */>}} Python  
{{</* icon name="r-project" pack="fab" */>}} R
```

renders as

{{< icon name="terminal" pack="fas" >}} Terminal  
{{< icon name="python" pack="fab" >}} Python  
{{< icon name="r-project" pack="fab" >}} R

Optionally, left and right padding can be added to an icon using the `padding_left="3"` and `padding_right="3"` options, respectively.

## Blockquote

    > This is a blockquote.

> This is a blockquote.

## Highlight quote

    This is a {{</* hl */>}}highlighted quote{{</* /hl */>}}.

This is a {{< hl >}}highlighted quote{{< /hl >}}.

## Mention a user

To mention someone, type `{{%/* mention "username" */%}}` where `username` corresponds to a user account in Academic.

_Requires Academic v4.6+._

## Footnotes

    I have more [^1] to say.
    
    [^1]: Footnote example.

I have more [^1] to say.
[^1]: Footnote example.

## Embed Documents

The following kinds of document may be embedded into a page.

To embed **Google Documents** (e.g. slide deck), click *File > Publish to web > Embed* in Google Docs and copy the URL within the displayed `src="..."` attribute. Then paste the URL in the form:

    {{</* gdocs src="https://docs.google.com/..." */>}}

## Diagrams

Academic supports a Markdown extension for diagrams. You can enable this feature by toggling the `diagram` option in your `config/_default/params.toml` file or by adding `diagram: true` to your page front matter. Then insert your [Mermaid diagram syntax](https://mermaidjs.github.io) within a *mermaid* code block as seen below and that's it. _Note: Academic v4.4.0+ is required to make diagrams._

An example **flowchart**:

    ```mermaid
    graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
    ```

renders as

```mermaid
graph TD;
  A-->B;
  A-->C;
  B-->D;
  C-->D;
```

An example **sequence diagram**:

    ```mermaid
    sequenceDiagram
      participant Alice
      participant Bob
      Alice->John: Hello John, how are you?
      loop Healthcheck
          John->John: Fight against hypochondria
      end
      Note right of John: Rational thoughts <br/>prevail...
      John-->Alice: Great!
      John->Bob: How about you?
      Bob-->John: Jolly good!
    ```

renders as

```mermaid
sequenceDiagram
  participant Alice
  participant Bob
  Alice->John: Hello John, how are you?
  loop Healthcheck
      John->John: Fight against hypochondria
  end
  Note right of John: Rational thoughts <br/>prevail...
  John-->Alice: Great!
  John->Bob: How about you?
  Bob-->John: Jolly good!
```

An example **Gantt diagram**:

    ```mermaid
    gantt
      dateFormat  YYYY-MM-DD
      section Section
      A task           :a1, 2014-01-01, 30d
      Another task     :after a1  , 20d
      section Another
      Task in sec      :2014-01-12  , 12d
      another task      : 24d
    ```

renders as

```mermaid
gantt
  dateFormat  YYYY-MM-DD
  section Section
  A task           :a1, 2014-01-01, 30d
  Another task     :after a1  , 20d
  section Another
  Task in sec      :2014-01-12  , 12d
  another task      : 24d
```

### Advanced diagrams

More advanced diagrams can be created in the open source [draw.io](https://draw.io) editor. The editor has support for almost any type of diagram, from simple to complex. A diagram can be easily embedded in Academic by choosing **File > Embed > SVG** in the [draw.io](https://draw.io) editor and pasting the generated code into your page.

Alternatively, a diagram can be exported as an [image](#images) from any drawing software, or a [document/slide](#embed-documents) containing a diagram can be embedded.

## Code highlighting

Pass the *language* of the code, such as `python`, as a parameter after three backticks:

    ```python
    # Example of code highlighting
    input_string_var = input("Enter some data: ")
    print("You entered: {}".format(input_string_var))
    ```
Result:

```python
# Example of code highlighting
input_string_var = input("Enter some data: ")
print("You entered: {}".format(input_string_var))
```

### Highlighting options

The Academic theme uses [highlight.js](https://highlightjs.org) for source code highlighting, and highlighting is enabled by default for all pages. However, several configuration options are supported that allow finer-grained control over highlight.js.

The following table lists the supported options for configuring highlight.js, along with their expected type and a short description. A "yes" in the **config.toml** column means the value can be set globally in `config.toml`, and a "yes" in the **preamble** column means that the value can be set locally in a particular page's preamble.

option                | type    | description                     | config.toml | preamble
----------------------|---------|---------------------------------|-------------|---------
`highlight`           | boolean | enable/disable highlighting     | yes         | yes
`highlight_languages` | slice   | choose additional languages     | yes         | no
`highlight_style`     | string  | choose a highlighting style     | yes         | no


#### Option `highlight`

The `highlight` option allows enabling or disabling the inclusion of highlight.js, either globally or for a particular page. If the option is unset, it has the same effect as if you had specified `highlight = true`. That is, the highlight.js javascript and css files will be included in every page. If you'd like to only include highlight.js files on pages that actually require source code highlighting, you can set `highlight = false` in `params.toml`, and then override it by setting `highlight: true` in the preamble of any pages that require source code highlighting. Conversely, you could enable highlighting globally, and disable it locally for pages that do not require it. Here is a table that shows whether highlighting will be enabled for a page, based on the values of `highlight` set in `params.toml` and/or the page's preamble.

config.toml   | page front matter  | highlighting enabled for page?
--------------|----------------|-------------------------------
unset or true | unset or true  | yes
unset or true | false          | no
false         | unset or false | no
false         | true           | yes

#### Option `highlight_languages`

The `highlight_languages` option allows you to specify additional languages that are supported by highlight.js, but are not considered "common" and therefore are not supported by default. For example, if you want source code highlighting for Go and clojure in all pages, set `highlight_languages = ["go", "clojure"]` in `params.toml`. If, on the other hand, you want to enable a language only for a specific page, you can set `highlight_languages` in that page's preamble.

The `highlight_languages` options specified in `config.toml` and in a page's preamble are additive. That is, if `params.toml` contains, `highlight_languages = ["go"]` and the page's preamble contains `highlight_languages: ["ocaml"]`, then javascript files for *both* go and ocaml will be included for that page.

If the `highlight_languages` option is set, then the corresponding javascript files will be served from the [cdnjs server](https://cdnjs.com/libraries/highlight.js/). To see a list of available languages, visit the [cdnjs page](https://cdnjs.com/libraries/highlight.js/) and search for links with the word "languages".

The `highlight_languages` option provides an easy and convenient way to include support for additional languages to be severed from a CDN. If serving unmodified files from cdnjs doesn't meet your needs, you can include javascript files for additional language support via one of the methods described in the [customization guide]({{< relref "customization.md#add-scripts-js" >}}).

#### Option `highlight_style`

The `highlight_style` option allows you to select an alternate css style for highlighted code. For example, if you wanted to use the solarized-dark style, you could set `highlight_style = "solarized-dark"` in `params.toml`.

If the `highlight_style` option is unset, the default is to use the file `/css/highlight.min.css`, either the one provided by the Academic theme, or else the one in your local `static` directory.  The `/css/highlight.min.css` file provided by Academic is equivalent to the `github` style from highlight.js.

If the `highlight_style` option *is* set, then `/css/highlight.min.css` is ignored, and the corresponding css file will be served from the [cdnjs server](https://cdnjs.com/libraries/highlight.js/). To see a list of available styles, visit the [cdnjs page](https://cdnjs.com/libraries/highlight.js/) and search for links with the word "styles".

See the [highlight.js demo page](https://highlightjs.org/static/demo/) for examples of available styles.

{{% alert note %}}
Not all styles listed on the [highlight.js demo page](https://highlightjs.org/static/demo/) are available from the [cdnjs server](https://cdnjs.com/libraries/highlight.js/). If you want to use a style that is not served by cdnjs, just leave `highlight_style` unset, and place the corresponding css file in `/static/css/highlight.min.css`.
{{% /alert %}}

{{% alert note %}}
If you don't want to change the default style that ships with Academic but you do want the style file served from the [cdnjs server](https://cdnjs.com/libraries/highlight.js/), set `highlight_style = "github"` in `params.toml`.
{{% /alert %}}

The `highlight_style` option is only recognized when set in `params.toml`. Setting `highlight_style` in your page's preamble has no effect.

## Jupyter Notebook

[**View the guide to blogging with Jupyter Notebooks**]({{< relref "jupyter.md" >}}).

## Twitter tweet

To include a single tweet, pass the tweet’s ID from the tweet's URL as parameter to the shortcode:

    {{</* tweet 666616452582129664 */>}}

## GitHub gist

    {{</* gist USERNAME GIST-ID  */>}}

## $\rm \LaTeX$ math

Academic supports a Markdown extension for $\LaTeX$ math. You can enable this feature by toggling the `math` option in your `config/_default/params.toml` file.

{{% alert warning %}}
Prior to Academic v4.7, you'll also need to add `markup: mmark` to your page front matter in order to display math.
{{% /alert %}}

To render *inline* or *block* math, wrap your LaTeX math with `$...$` or `$$...$$`, respectively.

Example **math block**:

```tex
$$\gamma_{n} = \frac{ 
\left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T 
\left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}
{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}$$
```

renders as

$$\gamma_{n} = \frac{ \left | \left (\mathbf x_{n} - \mathbf x_{n-1} \right )^T \left [\nabla F (\mathbf x_{n}) - \nabla F (\mathbf x_{n-1}) \right ] \right |}{\left \|\nabla F(\mathbf{x}_{n}) - \nabla F(\mathbf{x}_{n-1}) \right \|^2}$$

Example **inline math** `$\nabla F(\mathbf{x}_{n})$` renders as $\nabla F(\mathbf{x}_{n})$.

Example **multi-line math** using the `\\` math linebreak:

```tex
$$f(k;p_0^*) = \begin{cases} p_0^* & \text{if }k=1, \\
1-p_0^* & \text {if }k=0.\end{cases}$$
```

renders as

$$f(k;p_0^*) = \begin{cases} p_0^* & \text{if }k=1, \\
1-p_0^* & \text {if }k=0.\end{cases}$$

{{% alert warning %}}
As Hugo and Academic attempt to parse YAML, Markdown, and LaTeX content in the abstract field for publications and talks, Markdown special characters need to be escaped in any math within the abstract fields by using a backslash to prevent the math being parsed as Markdown. The following tips may help:

- escape each LaTeX backslash (`\`) with an extra backslash, yielding `\\`
- escape each LaTeX underscore (`_`) with two backslashes, yielding `\\_`

Hence, `abstract: "${O(d_{\max})}$"` becomes `abstract: "${O(d\\_{\\max})}$"`.
{{% /alert %}}

## Table

Code:

```Markdown
| Command           | Description                    |
| ------------------| ------------------------------ |
| `hugo`            | Build your website.            |
| `hugo serve -w`   | View your website.             |
```

Result:

| Command           | Description                    |
| ------------------| ------------------------------ |
| `hugo`            | Build your website.            |
| `hugo serve -w`   | View your website.             |


## Asides

Academic supports a Markdown extension for asides, also referred to as *alerts*.

Asides are a useful feature that **add side content such as notes, hints, or warnings to your articles**. They are especially handy when writing educational tutorial-style articles or documentation.

You can enable this feature either by using the _Alert_ shortcode below. The paragraph will render as an aside with the default *note* style:

    {{%/* alert note */%}}
    A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
    {{%/* /alert */%}}

This will display the following *note* block:

{{% alert note %}}
A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
{{% /alert %}}

Alternatively, a warning can be displayed to the reader using the the _warning_ option:

    {{%/* alert warning */%}}
    Here's some important information...
    {{%/* /alert */%}}

This will display the following *warning* notice to the reader:

{{% alert warning %}}
Here's some important information...
{{% /alert %}}

## Table of Contents

A table of contents may be particularly useful for long posts or tutorial/documentation type content. Use the `{{%/* toc */%}}` shortcode anywhere you wish within your Markdown content to automatically generate a table of contents.

_Note: the `toc` shortcode may not yet function correctly in **Hugo v0.60+** due to a known Hugo limitation. As a temporary workaround, `markup: blackfriday` can be added to a page's front matter to enable use of `toc` shortcode._
