<!-- TITLE: Mitmproxy -->
<!-- SUBTITLE: A quick summary of Mitmproxy -->

# mitmproxy

## Installation

```
brew install mitmproxy
```

or

```
brew upgrade mitmproxy
```




## Basic Usage

Serve on port 8080

`mitmproxy`


Specify a port

`mitmproxy --port 8080`



## mitmproxy UI 介紹：

* flow list - 即 request / response 清單
* flow view - 即 request / response detail
* grid editor - 即 request 編輯器



## mitmproxy 進階用法


### Interception

Reference: http://docs.mitmproxy.org/en/stable/mitmproxy.html#example-interception



* i 開啟攔截模式，並且輸入 filter 條件
* 對攔截到的項目點選 e 編輯
* 編輯完畢後，點選 a (accept) 送出




### SSL

Reference: http://docs.mitmproxy.org/en/stable/certinstall.html


到 **mitm.it (http://mitm.it/) **照著指示做即可

由於 chrome 使用 mac 的 proxy 設定，記得把 mac 的 proxy 設定中的 HTTPS 也打開。



### Scripting

* `mitmdump -s redirect.py`



* # redirect.py

```
    # 如果 request host 是 example.com，就導向到 google.com
    def request(context, flow):
        if flow.request.host == "example.com":
            flow.request.host = "google.com"
```



### Reverse Proxy 用法

```
mitmproxy -R http://example.com/ --port 80
```


### mitmweb

mitmweb 為 mitmproxy 的 web 介面，但目前仍為 beta，僅有部分功能。

使用方法：

`mitmweb`



### mitmdump

為純命令、非互動式版本的 mitmproxy 工具。



### 附錄

Filter

http://docs.mitmproxy.org/en/stable/features/filters.html



* ~q request
* ~s response
* ~b body
* ~h header
* ~u url
* ~m method
* -t content type
* & and
* | or
* -c http status code

Example

!(~qb "OK" & ~c 200)



### 常用選項

* Anti-Cache: http://docs.mitmproxy.org/en/stable/features/anticache.html
    * O → a
* Anti-Compression: 
    * O → o
* Replacement
    * http://docs.mitmproxy.org/en/stable/features/replacements.html

