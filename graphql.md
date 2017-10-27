<!-- TITLE: Graph QL -->
<!-- SUBTITLE: A quick summary of Graph Ql -->

# GraphQL

## tools

### Document Generator

Generate GraphQL Document from GraphQL Schema

```
yarn add @2fd/graphdoc
./node_modules/.bin/graphdoc -s schema.graphql -o dist
```


## Graphcool Framework

Graphcool framework was open-sourced, and is available to deploy to local docker.

https://github.com/graphcool/framework

```
mkdir graphcool-framework
cd graphcool-framework
yarn add graphcool
./node_modules/.bin/graphcool init
# edit types.graphql
# edit graphcool.yml
./node_modules/.bin/graphcool local up
./node_modules/.bin/graphcool deploy
# choose local docker
```

output 

```
Here are your GraphQL Endpoints:

  Simple API:        http://localhost:60000/simple/v1/cj99l7p6j000401244gnsjn5k
  Relay API:         http://localhost:60000/relay/v1/cj99l7p6j000401244gnsjn5k
  Subscriptions API: ws://localhost:60000/subscriptions/v1/cj99l7p6j000401244gnsjn5k
```