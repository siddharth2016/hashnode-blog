## Scraping Web - Awesome Facts

Want some awesome facts to start your day or just want to learn something new or out here for some fun !

Well, in this blog I will be sharing a script that I did over a weekend just for fun (and for a side project 😉).

What I will not discuss here:

[What is Web Scraping ?](https://realpython.com/python-web-scraping-practical-introduction/)

[How to use BeautifulSoup ?](https://realpython.com/beautiful-soup-web-scraper-python/)

<strike>How to Scrap ?</strike> That we will discuss !!

---

## TechStack

- Python
- BeautifulSoup

## Final Result (Before diving into the steps)

We will be saving all the scraped quotes in a text file. That would look something like this

![result_1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608450310404/5nvFy7Gu6.png)

## Let's Do Scraping

### Analyse The Website To Scrape

As we want to scrape the awesome facts, we are going to get that from [Computer Facts](https://gotechug.com/interesting-facts-about-computers-you-didnt-know/)

A look at webpage

![web_page.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608450361713/oe0x5c16c.png)

Now, we want facts like `1. The first electronic computer ENIAC weighed more than 27 tons and took up 1800 square feet.`, so we should take a look at its source page first and find where is this present, to get the pattern (we will use that pattern later to scrape these quotes).

![page_source.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1608450392116/w5PXyDaKu.png)

As we can see on page source, the facts start from `<p>` tag on line `475` and there are several `<p>` tags that contains these facts. If we look further, we would find that there are a lot of `<p>` tags being used within the HTML. How would we differentiate our facts with other `<p>` tags ?

If you looked hard, then you know ! There is a unique descriptor where facts are present, each fact precedes a with number (0-9) followed by (.) and space. Hence, we have our pattern 😀 

We can ignore all other `<p>` tags and take only that matches a particular pattern we identified. To match pattern, we will use regex module of python, `re`.

Hence, the pattern we identified is

- All facts are inside `<p>` tags.
- There are other contents inside `<p>` tag as well.
- To get facts, we will use regex to extract required content, leaving other `<p>` tags as it is !

### Import Required Libraries And Define Constants

Before doing the task of scraping, we need to import libraries and define some constants.

```python
# Standard Imports

import os
import re
from typing import List
from urllib.request import Request, urlopen
from bs4 import BeautifulSoup
from bs4.element import Tag
```

- `import os` will import python standard library, used to make directory and other OS stuff.
- `re` will be used to extract a pattern using some regex.
- Then we import `List` from `typing`, to explicitly [type hint](https://www.python.org/dev/peps/pep-0484/) some arguments passed to some functions.
- `Request` and `urlopen` from standard library `urllib`. They would help us to get HTML data we want.
- `BeautifulSoup` from third-party library `bs4`, this creates a easy to manage BeautifulSoup object, that represents HTML content.
- `Tag` from `bs4.element`, again to be used for type hinting.

```python
QUOTES_FILENAME = "/funfacts.txt"
QUOTES_TXT_PATH = os.getcwd() + "/funfacts"
QUOTES_FILE_PATH = QUOTES_TXT_PATH + QUOTES_FILENAME
QUOTES_URL = "https://gotechug.com/interesting-facts-about-computers-you-didnt-know/"
```

- `QUOTES_FILENAME` represents the filename of the text file where the facts will be stored.
- `QUOTES_TXT_PATH` represents the folder where the `funfacts.txt` will reside.
- `QUOTES_FILE_PATH` file path, to be used further to store data.
- `QUOTES_URL` url to webpage we want to scrape.

Why name the variables as `QUOTES` ? I had another script to scrape some great quotes and reused that same for scraping awesome facts. Need to know more about scraping quotes ? Visit [this](https://blog.codekaro.info/scraping-web-inspiring-quotes) link.

### Create BeautifulSoup Object

Now, we have some constants to play with, we will use `QUOTES_URL` to get the HTML of the page and create a BeautifulSoup object to filter our facts.

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

Steps I used to check if we are allowed to scrape the site or not

```python
import requests #pip install requests
req = requests.get(QUOTES_URL)
print(req.status_code) #should be 200, other than 200 means scraping not/partially allowed
```

### Filter Tags

With having `bs4Obj`, now it is possible to filter the HTML on `<p>` tags, we can achieve that using below functions

```python
def filter_p_tags(ptag: Tag) -> bool:
    '''
    Get required p tags only.
    '''
    return re.match(r"[0-9]+.", ptag.get_text())


def get_p_tags(bs4Obj: BeautifulSoup) -> List[Tag]:
    '''
    Get all p tags from the BeautifulSoup obj.
    Note: It is the requirement for given QUOTES_URL, it shall be different for different URL to scrap.
    '''
    allP = bs4Obj.find_all('p')
    allReleventP = list(filter(filter_p_tags, allP))
    return allReleventP
```

See how we used the `List` and `Tag` for type hints and `BeautifulSoup` as well. Type hints are not mandatory and are not checked by python, these are just for developers and know that Python will always be dynamically typed !

`allP` list contains all `<p>` tags available in HTML. We filter them using python's inbuilt `filter` function on the condition that, if text of any `<p>` tag does not have a pattern matching regex `[0-9]+.` then filter them out from `allP` list.

Pattern matching regex, we define that in function `filter_p_tags`, where we use `re.match` to match the occurence of our pattern in the given text. You can do that in `get_p_tags` itself, but I think it is better to have such task done in pure functions instead of making them in single function.

Store all relevent tags in variable `allReleventP` and return that (to be used by another function !)

### Get Facts

Now, we will create a [generator](https://realpython.com/introduction-to-python-generators/) to yield the facts we need to save in a text file. We will be using `allReleventP` variable passed to the new function.

```python
def get_all_facts(ptags: List[Tag]):
    '''
    Yield all facts present in p tags.
    '''
    for p in ptags:
        fact = re.sub(r"[0-9]+\. ", "", p.get_text())
        yield fact + "\n"
```

Here we are extracting text present in `<p>` tag. But wait !! We don't need preceding number, right ? That's why we are using `re.sub` to substitute it with empty string. Regex we used `"[0-9]+\. "`, it will take any number followed by `.` and a space.

We will use this generator in next section, inside another function.

### Save Facts

Here is the function

```python
def save_fun_facts(ptags: List[Tag]):
    '''
    Save extracted facts in a text file, create a new folder if not already present
    '''
    global QUOTES_TXT_PATH, QUOTES_FILE_PATH
    if not os.path.exists(QUOTES_TXT_PATH):
        os.mkdir(QUOTES_TXT_PATH)

    with open(QUOTES_FILE_PATH, 'w') as file:
        for txt in get_all_facts(ptags):
            file.write(txt)

    print(f'All Fun Facts written to file: {QUOTES_FILE_PATH}')
```

We take global constants `QUOTES_TXT_PATH` and `QUOTES_FILE_PATH` to be used for writing to the file. We check if the directory exists or not (the folder where we will save our file). Then we open the file in the created directory (if it not exists).

Now here comes the use of generator, we call generator on each `<p>` tag that yields text present in it.

### Main

Now the script to execute the code

```python
if __name__ == "__main__":
    bs4Obj = get_bs4_obj(QUOTES_URL)
    allP = get_p_tags(bs4Obj)
    save_fun_facts(allP)
```

If you check now, the facts should be appearing in the file created `funfacts.txt` inside the folder `/funfacts`.

---

Well, that was it, if you followed this then you now know the gist of general process for web scraping and how to scrape Awesome Facts !

It was just a drop in the ocean full of different functionalities you can achieve with web scraping, but the general idea remains the same:

1. Get the website we want to scrape.
2. Analyse the required components we need and find the pattern.
3. Create BeautifulSoup object to ease the process and access HTML without much problem.
4. Create small functions to get the task done.
5. Finally integrate all function and see the magic of the script !

---

Full python script can be found [here](https://gist.github.com/siddharth2016/758a53ac4292a7073db595570658ba6c).

GitHub [action](https://github.com/marketplace/actions/quote-readme) where this script is used. Would love to hear your feedback on this as well.

Just starting your Open Source Journey ? Don't forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Want to make a simple and awesome game from scratch ? Check [PongPong](https://github.com/siddharth2016/PongPong)

Till next time !

Namaste 🙏