<!-- TITLE: Ssl Tls -->
<!-- SUBTITLE: A quick summary of Ssl Tls -->

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

