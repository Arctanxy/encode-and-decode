# encode-and-decode

python中文编码问题的小结

1. python中通常将Unicode作为中间编码，进行转换过渡。

2. 很多网站都会在<head>中包含编码信息，如：<meta charset="utf-8" />这样的信息。

3. 将数据爬取下来之后要将网页的代码转换成‘utf-8’。

```
html = urlopen("https://fengshenfeilian.github.io/")
bsObj = BeautifulSoup(html)
content = bsObj.find("div", {"id":"mw-content-text"}).get_text()
content = bytes(content, "UTF-8")
content = content.decode("UTF-8")
```

```
from urllib.request import urlopen
textPage = urlopen("https://fengshenfeilian.github.io/")
print(str(textPage.read(),'utf-8'))
```
