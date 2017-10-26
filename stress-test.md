<!-- TITLE: Stress Test -->
<!-- SUBTITLE: A quick summary of Stress Test -->

# Stress Test


## tools

### ab

#### POST Example

```
ab -c 100 -n 20000 -k -p ./postfile -m POST http://example.com/
```

### wrk

#### POST Example

```
wrk -t100 -c1000 -d 20s -s ./wrk-post.lua http://example.com/
```

wrk-post.lua

```
wrk.method = "POST"
wrk.body   = "foo=bar&baz=quux"
wrk.headers["Content-Type"] = "application/x-www-form-urlencoded"
```

references: https://github.com/wg/wrk/blob/master/scripts/post.lua

