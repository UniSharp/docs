<!-- TITLE: Laravel Web Framework -->
<!-- SUBTITLE: A quick summary of Laravel Web Framework -->

# 主題式

[Laravel Custom Paginator](laravel-custom-paginator)


# 未分類

## Laravel cross sub-domain cookie 設定要點

1. 兩個站的 APP_KEY 要相同
2. session 要存在 database，才能讓兩個站一起連，因此要改 .env SESSION_DRIVER=database (新增了一個 session table)
3.  (session_domain) COOKIE_DOMAIN 要設定成 `.domain.name`
4. 如果以上都設定好，還是有問題，就把本來的 cookie 清除再重新登入。有很多 browser extension 可以用來清 cookie.