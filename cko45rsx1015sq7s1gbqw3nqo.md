---
title: "How To Convert Markdown To HTML Using Python"
seoDescription: "In this article, we are going to see how we can use Python to convert GitHub flavoured Markdown text to HTML."
datePublished: Fri Apr 30 2021 10:13:37 GMT+0000 (Coordinated Universal Time)
cuid: cko45rsx1015sq7s1gbqw3nqo
slug: how-to-convert-markdown-to-html-using-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1619777451810/ZA8Qucyrp.png
tags: github, programming, python, markdown, automation

---

In this article, we are going to see how we can use python to convert GitHub flavoured markdown text to HTML. We will go through a python library, what are its benefits and how we can leverage it for automated conversion.

So, without any further ado, let's get started!

---

### What Are We Going To Use?

We are going to use Python and one of its awesome 3rd party library, [gh-md-to-html](https://github.com/phseiff/github-flavored-markdown-to-html).

To install `gh-md-to-html` run the following command on terminal:

```bash
$ pip install gh-md-to-html
Collecting gh-md-to-html
  Downloading gh_md_to_html-1.11.4-py3-none-any.whl (59 kB)
     |████████████████████████████████| 59 kB 5.9 MB/s 
Collecting shellescape
  Downloading shellescape-3.8.1-py2.py3-none-any.whl (3.1 kB)
Collecting Pillow>=8.0.1
  Downloading Pillow-8.2.0-cp38-cp38-macosx_10_10_x86_64.whl (2.8 MB)
     |████████████████████████████████| 2.8 MB 4.8 MB/s 
Collecting webcolors
  Downloading webcolors-1.11.1-py3-none-any.whl (9.9 kB)
Collecting requests
  Using cached requests-2.25.1-py2.py3-none-any.whl (61 kB)
Collecting beautifulsoup4
  Using cached beautifulsoup4-4.9.3-py3-none-any.whl (115 kB)
Collecting soupsieve>1.2
  Downloading soupsieve-2.2.1-py3-none-any.whl (33 kB)
Collecting idna<3,>=2.5
  Using cached idna-2.10-py2.py3-none-any.whl (58 kB)
Collecting certifi>=2017.4.17
  Using cached certifi-2020.12.5-py2.py3-none-any.whl (147 kB)
Collecting chardet<5,>=3.0.2
  Using cached chardet-4.0.0-py2.py3-none-any.whl (178 kB)
Collecting urllib3<1.27,>=1.21.1
  Using cached urllib3-1.26.4-py2.py3-none-any.whl (153 kB)
Installing collected packages: urllib3, soupsieve, idna, chardet, certifi, webcolors, shellescape, requests, Pillow, beautifulsoup4, gh-md-to-html
Successfully installed Pillow-8.2.0 beautifulsoup4-4.9.3 certifi-2020.12.5 chardet-4.0.0 gh-md-to-html-1.11.4 idna-2.10 requests-2.25.1 shellescape-3.8.1 soupsieve-2.2.1 urllib3-1.26.4 webcolors-1.11.1
$
```

As we can see, this library depends on a lot of other libraries and is not a pure library like `pytube` discussed [here](download-youtube-videos-using-python-your-own-youtube-downloader).

### Advantages

Advantages include (from its official documentation):

* Let's you specify the markdown to convert as a string, as a repository path, as a local file name or as a hyperlink.
* Pulls any images referenced in the markdown files from the web/ your local storage and places them in a directory relative to your specified website root, so the resulting file structure is host-ready for static sites. Multiple arguments allow the customization of the saving locations, but the images will always be referenced correctly in the resulting HTML files. This is especially useful since it reflects GitHub's behaviour to serve cached copies of README images instead of linking to them directly, reducing tracking and possibly downscaling overlarge images in the process.
* Creates all links as root-relative hyperlinks and lets you specify the root directory as well as the locations for CSS and images, but uses smart standard values for everything.
* Supports inline LaTeX-formulas (use `$`-formula-`$` to use them), which GitHub usually doesn't. gh-md-to-html uses [LaTeX](https://www.tug.org/texlive/) and [dvisvgm](https://dvisvgm.de/) if they are both installed (advantage: fast, requires no internet), and otherwise the [Codecogs EqnEditor](https://latex.codecogs.com/) (advantage: doesn't require you to install 3 GB of LaTeX libraries) to achieve this.
* Supports exporting to pdf with or without Github styling, using the [pdfkit](https://pypi.org/project/pdfkit/) python module (if it is installed).
* Tested and optimized to look good when using [DarkReader](https://github.com/darkreader/darkreader) (the .js-module as well as the browser extension). This is especially relevant considering that DarkReader doesn't usually shift the colours of SVG images, and the formulas added by gh-md-to-html's formula support are embedded as inline svg. gh-md-to-html ensured that the formulas are the same colour as the text, shifted in accordance with DarkReader's current/enabled colorscheme.
* Supports umlauts and other non-ascii-characters in plain text as well as in multiline code blocks, which the github REST api usually doesn't.
* Allows you to choose which tool or module to use at its core for the basic markdown to html conversion.
* Styles its output with github's README-css (can be turned off).

Whilst using pandoc to convert from markdown to pdf usually yields more beautiful results (pandoc uses LaTeX, after all), gh-md-to-html has its own set of advantages when it comes to quickly converting complex files for a homework assignment or other purposes where reliability weights more than beauty. pandoc's md-to-pdf-conversion acts quite unusual when it comes to images, nested lists, multiline bullet point entries, or formulas, and gh-md-to-html does not.

### Converting Markdown To HTML

Now, let's create a simple script that converts markdown text to HTML using `gh-md-to-html`.

Add the following code to a file, name it whatever you like, say `mdtohtmldemo.py`:

```python
#./ mdtohtmldemo.py

import gh_md_to_html

html = gh_md_to_html.main('md-to-html/sample.txt')
print(html)
```

Where the markdown contents are as follows (notice that we are using it as a text file, but it is not necessary, we can use `.md` files directly):

```text
# This is a sample markdown

Hello World!

> Feel free to add your own markdown here.
```

After running the above script for given markdown content, we get the below output:

```html
<?xml version='1.0' encoding='UTF-8'?>
<link href="/github-markdown-css/github-css.css" rel="stylesheet"/>
<meta charset="utf-8" content="text/html"/>
<div class="gist">
<style class="formula-style">
        svg.gh-md-to-html-formula {
            fill: black;
        }
    </style>
<div class="gist-file"> <!-- This is the class that is responsible for the boxing! -->
<div class="gist-data">
<div class="js-gist-file-update-container js-task-list-container file-box">
<div class="file" id="article-sample">
<div class="Box-body readme blob js-code-block-container p-5 p-xl-6" id="file-docker-image-pull-md-readme" style="margin-left: 40px; margin-right: 40px; margin-top: 20px; margin-bottom: 20px">
<article class="markdown-body entry-content container-lg" itemprop="text">
<h1 id="user-content-this-is-a-sample-markdown">
<a aria-hidden="true" class="anchor" href="#user-content-this-is-a-sample-markdown" id="user-content-this-is-a-sample-markdown"><span aria-hidden="true" class="octicon octicon-link"></span></a>This is a sample markdown</h1>
<p>Hello World!</p>
<blockquote>
<p>Feel free to add your own markdown here.</p>
</blockquote>
</article>
</div>
</div>
</div>
</div>
</div>
</div>
```

If we notice, it created a CSS `/github-markdown-css/github-css.css` in our local directory where we ran the script similar to what github uses.

There is an output HTML file also created with the same name as `sample.html`, if we open it in a browser, we get the following output:

![samplehtml.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619777354750/rohnVAw8s.png)

---

Well, that's it from me. If you followed this, you would be seeing an autogenerated HTML file for your markdown file.

Try different functions, methods and utilities it provides and use them with your projects as needed.

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏