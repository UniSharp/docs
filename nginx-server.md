<!-- TITLE: Nginx Server -->
<!-- SUBTITLE: A quick summary of Nginx Server -->

# Header

## Example of wildcard (regular expression) server_name matching

```
server {
    listen 80;
    listen [::]:80;
    server_name  ~^(?<name>.+?).unisharp.com$;

    root /var/www/deploy/$name/public;
    index index.php index.html;

    include /etc/nginx/php;
}
```