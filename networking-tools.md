<!-- TITLE: Networking Tools -->
<!-- SUBTITLE: A quick summary of Networking Tools -->

# Networking Tools


## ngrep

```
sudo ngrep -W byline port 4080 <-d interface>
sudo ngrep -W byline port 4080 | egrep 'delete|insert|update'
sudo ngrep -W byline port 80 and src host 1.162.52.167
```
