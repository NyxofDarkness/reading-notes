# Reading

## Web Scrape with Python in 4 minutes

> Web scraping is a technique to automatically access and extract large amounts of information from a website, which can save a huge amount of time and effort.

## Important Notes

- Read through the website’s Terms and Conditions to understand how you can legally use the data. Most sites prohibit you from using the data for commercial purposes.

- Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.

> It is important to understand the basics of HTML in order to successfully web scrape.

Get these libraries:

``` python
import requests
import urllib.request
import time
from bs4 import BeautifulSoup
```

> set the url to the website and access the site with our requests library:

``` python
url = 'http://web.mta.info/developers/turnstile.html'
response = requests.get(url)
```

> Next we parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure

``` python
soup = BeautifulSoup(response.text, “html.parser”)
```

> We use the method .findAll to locate all of our ```<a>``` tags:

``` python
soup.findAll('a')
```

> Next, let’s extract the actual link that we want;

``` python
one_a_tag = soup.findAll(‘a’)[38]
link = one_a_tag[‘href’]
```

> We provide request.urlretrieve with two parameters: file url and the filename. For my files, I named them “turnstile_180922.txt”, “turnstile_180901”, etc.

``` python
download_url = 'http://web.mta.info/developers/'+ link
urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
```

> include this line of code so that we can pause our code for a second so that we are not spamming the website with requests

``` python
time.sleep(1)
```

### Bookmark/Skim

[x] Beautiful Soup
