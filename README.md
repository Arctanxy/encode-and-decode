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
```
import requests
url="http://www.starbaby.cn/zhinan/609987"
req =requests.get(url)
req.encoding='utf-8' #显式地指定网页编码，一般情况可以不用
print(req.text)

```
```
html = response.read().decode('utf8',errors='replace')

然后把html变量传入Beautifulsoup()就没问题了:
soup = BeautifulSoup(html)
```
4. 如果转换之后还有问题可能是网页中包含的编码信息有误，可以使用chardetect库来探测网页真实编码。
5. python3 源文件默认是‘utf-8’编码，通常如需要utf-8编码的话不需要额外添加文件头 #coding:utf-8。
6. 控制台中的print（）会默认使用gbk编码。
7. 各种编码简介参考：http://shanchao7932297.blog.163.com/blog/static/1363624201010265449609/
