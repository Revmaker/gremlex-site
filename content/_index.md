---
title: "Gremlex"
---

# Gremlex

[Gremlex](https://github.com/Revmaker/gremlex) is an Elixir client for Gremlin (Apache TinkerPop™), a simple to use library for creating Gremlin queries.

{{% notice tip %}}Gremlex is early in development and does not support all Gremlin queries. But you are always welcome to use our raw query function.
{{% /notice %}}
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
