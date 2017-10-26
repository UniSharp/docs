<!-- TITLE: Networking Tools -->
<!-- SUBTITLE: A quick summary of Networking Tools -->

# Networking Tools

## sniffer

### ngrep

```
sudo ngrep -W byline port 4080 <-d interface>
sudo ngrep -W byline port 4080 | egrep 'delete|insert|update'
sudo ngrep -W byline port 80 and src host 1.162.52.167
```


### tcpdump

```
sudo tcpdump src host hostname and tcp dst port 4080 and dst host example.com -A -s 5000
sudo tcpdump tcp port 4080 -A -nn -vv -s0
sudo tcpdump port 3306 -s 10000 -w - -i eth0 | strings | egrep -i 'select|insert|update|delete'
```

## trace

* mtr (traceroute)
* ping -M do -s 1472 8.8.8.8
* test port open
    - nc -zv unisharp.com 80
    - nc -zv 8.8.8.8 53

## Open port / Serving

* Sharing file through http 80 port

`nc -v -l 80 < file.ext`

* Serving current directory tree

`python -m SimpleHTTPServer`

## Scanner

* nmap:
    - sudo nmap -sS -O 192.168.2.1/24



## Speed test

### iperf
* server side: `iperf -s -p 8080`
* client side: `iperf -c <server_ip> -p 8080`

## Others

* fuser -m <directory>
* check which process id is using port
    -  `sudo fuser 3306/tcp`


* show my public IP
    - `curl ifconfig.me`
    - `curl ifconfig.co`
    - `curl ifconfig.io`