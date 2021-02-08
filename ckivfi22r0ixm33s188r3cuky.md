## Scraping Web - Inspiring Quotes

Feeling lack of inspiration and motivation or just want to learn something new or out here for some fun !

Well, in this blog I will be sharing a script that I did over a weekend just for fun (and for a side project 😉).

What I will not discuss here:

[What is Web Scraping ?](https://realpython.com/python-web-scraping-practical-introduction/)

[How to use BeautifulSoup ?](https://realpython.com/beautiful-soup-web-scraper-python/)

<strike>How to Scrape ?</strike> That we will discuss !!

---

## TechStack

- Python
- BeautifulSoup

## Final Result (Before diving into the steps)

We will be saving all the scraped quotes in a text file. That would look something like this

![result_1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608363790935/28khzHZVn.png)

## Let's Do Scraping

### Analyse The Website To Scrape

As we want to scrape the inspirational quotes, we are going to get that from [Great Computer Quotes](http://www.devtopics.com/101-more-great-computer-quotes/)

A look at webpage

![web_page.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608363862089/ww18iG4g0.png)

Now, we want quotes like `“I do not fear computers. I fear lack of them.” - Isaac Asimov`, so we should take a look at its source page first and find where is this quote present, to get the pattern (we will use that pattern later to scrape these quotes).

![page_source.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608363910303/nffXFtBsF.png)

As we can see on page source, the quotes start from `<ol>` tag on line `182` and there are several `<ol>` tags that contains the quotes inside `<li>` tags. If we look further down the page or just `ctrl+f` or `cmd+f` the `<ol>`, we find that comments are also inside these tags.

![comments_tag.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608363945573/f-Gp-zo-j.png)

We can ignore these comments and take only quotes present in `<ol>` tags with no `class="commentlist"` attribute.

Hence, the pattern we identified is 💡

- All quotes are inside `<ol>` tags.
- There are comments inside `<ol>` tag as well.
- We can ignore the comments by leveraging `class="commentlist"` attribute of `<ol>` tag.

### Import Required Libraries And Define Constants

Before doing the task of scraping, we need to import libraries and define some constants.

```python
# Standard Imports

import os
from typing import List
from urllib.request import Request, urlopen
from bs4 import BeautifulSoup
from bs4.element import Tag
```

- `import os` will import python standard library, used to make directory and other OS stuff.
- Then we import `List` from `typing`, to explicitly [type hint](https://www.python.org/dev/peps/pep-0484/) some arguments passed to some functions.
- `Request` and `urlopen` from standard library `urllib`. They would help us to get HTML data we want.
- `BeautifulSoup` from third-party library `bs4`, this creates an easy to manage BeautifulSoup object, that represents HTML content.
- `Tag` from `bs4.element`, again to be used for type hinting.

```python
QUOTES_FILENAME = "/quotes.txt"
QUOTES_TXT_PATH = os.getcwd() + "/quotes"
QUOTES_FILE_PATH = QUOTES_TXT_PATH + QUOTES_FILENAME
QUOTES_URL = "http://www.devtopics.com/101-more-great-computer-quotes/"
```

- `QUOTES_FILENAME` represents the filename of the text file where the quotes will be stored.
- `QUOTES_TXT_PATH` represents the folder where the `quotes.txt` will reside.
- `QUOTES_FILE_PATH` file path, to be used further to store data.
- `QUOTES_URL` url to webpage we want to scrape.

### Create BeautifulSoup Object

Now, we have some constants to play with, we will use `QUOTES_URL` to get the HTML content of the page and create a BeautifulSoup object to filter our quotes.

```python
def get_bs4_obj(url: str) -> BeautifulSoup:
    '''
    Get BeautifulSoup object for given QUOTES_URL.
    '''
    req = Request(url, headers={'User-Agent': 'Mozilla/5.0'})
    html = urlopen(req).read()
    bs4Obj = BeautifulSoup(html, 'html.parser')
    return bs4Obj
```

We create a function `get_bs4_obj` that takes `url` a string type object and returns the required object `bs4Obj`.

- `Request` helps us to bypass the security that is blocking the use of `urllib` based on the user agent. Hence, we need to give `Mozilla` or any other browser user agent to let us access their source page.
- Then we do `urlopen` with the defined user agent in `Request` and read it's content.
- At last we create `BeautifulSoup` object using `html.parser` to parse the html contents and return the required object.

*It may be possible that the website has a legit reason for us to not access their page using default user agent (python's urllib), but when we try to check for if it is okay to scrape, the result status code is 200. Hence, we can scrape the site.*

Steps I used to check if we are allowed to scrape the site or not

```python
import requests #pip install requests
req = requests.get(QUOTES_URL)
print(req.status_code) #should be 200, other than 200 means scraping not/partially allowed
```

### Filter Tags

With having `bs4Obj`, now it is possible to filter the HTML on `<ol>` tags, we can achieve that using below function

```python
def get_ol_tags(bs4Obj: BeautifulSoup) -> List[Tag]:
    '''
    Get all ol tags from the bs4 obj.
    Note: It is the requirement for given QUOTES_URL, it shall be different for different URL to scrap.
    '''
    allOL = bs4Obj.find_all('ol')
    allReleventOL = list(filter(lambda ol: ol.attrs.get('class')!=['commentlist'], allOL))
    return allReleventOL
```

See how we used the `List` and `Tag` for type hints and `BeautifulSoup` as well. Type hints are not mandatory and are not checked by python, these are just for developers and know that Python will always be dynamically typed !

`allOL` list contains all `<ol>` tags available in HTML. We filter them using python's inbuilt `filter` function on the condition that, if attribute of any `<ol>` tag has `class` equivalent to `'commentlist'` then filter them out from `allOL` list.

Store all relevent tags in variable `allReleventOL` and return that (to be used by another function !)

### Get Quotes

Now, we will create a [generator](https://realpython.com/introduction-to-python-generators/) to yield the quotes we need to save in a text file. We will be using `allReleventOL` variable passed to the new function.

```python
def get_all_quotes(oltags: List[Tag]):
    '''
    Yield all qoutes present in OL tags.
    '''
    for ol in oltags:
        yield ol.find('li').get_text()
```

It is self explanatory, here we are extracting text present in `<li>` tag.

We will use this generator in next section, inside another function.

### Save Quotes

Here is the function !

```python
def save_qoutes(oltags: List[Tag]):
    '''
    Save extracted qoutes in a text file, create a new folder if not already present
    '''
    global QUOTES_TXT_PATH, QUOTES_FILE_PATH
    if not os.path.exists(QUOTES_TXT_PATH):
        os.mkdir(QUOTES_TXT_PATH)

    with open(QUOTES_FILE_PATH, 'w') as file:
        for txt in get_all_quotes(oltags):
            file.write(txt)

    print(f'All Quotes written to file: {QUOTES_FILE_PATH}')
```

We take global constants `QUOTES_TXT_PATH` and `QUOTES_FILE_PATH` to be used while writing to the file. We check if the directory exists or not (the folder where we will save our file). Then we open the file in the created directory (if not exists).

Now here comes the use of generator, we call generator on each `<ol>` tag that yields text of `<li>` tags. Something fishy here ? Yeah you got it right, we are using `ol.find('li')` that should return first `<li>` tag, but how come all `<li>` tags are getting returned ? Because it is the error in HTML file !

`<li>&#8220;I do not fear computers. I fear lack of them.&#8221;<br /><em>&#8212; Isaac Asimov<br />&nbsp; </em>`

Here, there is no `</li>` tag to mark its end !! Hence it takes the start of `<li>` and marks the end whenever it encounters a `</li>` tag, which happens to be before `</ol>` tag 😄

![li_before_ol.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608364260841/hWjepOa8E.png)

### Main

Now the script to execute the code

```python
if __name__ == "__main__":
    bs4Obj = get_bs4_obj(QUOTES_URL)
    olTags = get_ol_tags(bs4Obj)
    save_qoutes(olTags)
```

If you check now, the quotes should be appearing in the file created `quotes.txt` inside the folder `/quotes`.

---

Well, that was it, if you followed this then you now know the gist of general process for web scraping and how to scrape Inspirational Quotes !

It was just a drop in the ocean full of different functionalities you can achieve with web scraping, but the general idea remains the same:

1. Get the website we want to scrape.
2. Analyse the required components we need and find the pattern.
3. Create BeautifulSoup object to ease the process and access HTML without much problem.
4. Create small functions to get the task done.
5. Finally integrate all function and see the magic of the script !

---

Full python script can be found [here](https://gist.github.com/siddharth2016/1d2879c7f1f9f28011d5013c3f7c7be4).

GitHub [action](https://github.com/marketplace/actions/quote-readme) where this script is used. Would love to hear your feedback on this as well.

Just starting you Open Source Journey ? Don't forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Want to make a simple and awesome game from scratch ? Check [PongPong](https://github.com/siddharth2016/PongPong)

Till next time !

Namaste 🙏