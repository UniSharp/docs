<!-- TITLE: Ssl Tls -->
<!-- SUBTITLE: A quick summary of Ssl Tls -->


# 憑證申請、設定
大略步驟

1. 產生 server key 與 CSR，將 CSR 寄給憑證機構
2. 憑證機構寄回 certificate (cer / crt)
3. 憑證機構有時會同時寄回中繼憑證，或自行從網站上下載
4. 將中繼憑證與 certificate concat 成 pem 格式
5. 將中繼憑證、certificate 與 server key 設定在 server 上

nginx 的設定範例

```
server {
      listen 443 ssl;
        server_name your_domain.com;
        ssl_certificate /etc/nginx/ssl/nginx.crt; # => 這裡把中繼憑證與 cerficate concat 起來（如是 self-sign 則不用）
        ssl_certificate_key /etc/nginx/ssl/nginx.key;
}
```

----
# Checking
## with openssl s_client

```
openssl s_client -connect example.com:443 -prexit -showcerts
```

## with ssl labs online tool

https://www.ssllabs.com/ssltest/




## 驗證 certificate （機構簽發的憑證）是否正確

```
openssl x509 -in <certificate.cer> -text -noout
```



## 驗證 server key 是否正確

```
openssl rsa -in server.key -check
```


## 驗證 server key 與 certificate 是否 match

```
 openssl x509 -noout -modulus -in domain.cer | openssl md5
> (stdin)= foo

openssl rsa -noout -modulus -in server.key | openssl md5
> (stdin)= foo
```



# Others


### get cacert.pem

```
 wget --no-check-certificate https://curl.haxx.se/ca/cacert.pem
 ```



### Create CSR using existing private key

```
openssl req -new -key server.key -out req.csr
```

