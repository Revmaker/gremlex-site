---
title: "Introduction"
date: 2018-09-28T13:52:35-07:00
weight: 3
---

## Basic Example
To get a better understanding of how to use Gremlex, it would be easier to see what a Gremlin query looks like and how it translates to a Gremlex query.

### Gremlin Query
```js
g.V().has("name","marko")
  .out("knows")
  .out("knows")
  .values("name")
```

### Gremlex Query
```js
Graph.g()
|> Graph.v()
|> Graph.has("name", "marko")
|> Graph.out("knows")
|> Graph.out("knows")
|> Graph.values("name")
|> Client.query
```

## Basic Usage
The two main modules that you'll want to use are `Gremlex.Graph` and `Gremlex.Client`.

`Gremlex.Graph` is the module that hosts all the functions needed to build a Gremlin query. The DSL is a simple set of functions that carries over a graph for every step. Once you've defined your query, you can simply call `Gremlex.Client.query/1` to perform it.

```js
iex(1)> alias Gremlex.Graph
Gremlex.Graph
iex(2)> alias Gremlex.Client
Gremlex.Client
iex(3)> Graph.g() |> Graph.v() |> Client.query
{:ok,
 [
   %Gremlex.Vertex{
     id: 1,
     label: "person",
     properties: %{age: [29], name: ["marko"]}
   }
 ]}
```

## Raw Queries
We are still early in development and thus do not have every function supported. For more complex queries, we suggest using `Client.query/1`.

```js
Client.query("""
  g.V().match(
    __.as("a").out("knows").as("b"),
    __.as("a").out("created").as("c"),
    __.as("b").out("created").as("c"),
    __.as("c").in("created").count().is(2)
  )
  .select("c").by("name")
""")
```