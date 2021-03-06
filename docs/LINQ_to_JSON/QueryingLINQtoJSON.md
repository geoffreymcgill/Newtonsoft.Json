﻿# Querying JSON with LINQ

LINQ to JSON provides a number of methods for getting data from its objects. The index methods on JObject/JArray let you quickly get data by its property name on an object or index in a collection, while [JToken.Children](/api/newtonsoft/json/linq/jtoken/#method-children) lets you get ranges of data as `IEnumerable<JToken>` to then query using LINQ.

## Getting values by Property Name or Collection Index

The simplest way to get a value from LINQ to JSON is to use the [JToken.Item(object)](/api/newtonsoft/json/linq/jtoken/#property-item) index on JObject/JArray and then cast the returned [JValue](/api/newtonsoft/json/linq/jvalue/) to the type you want.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonSimpleQuerying" title="Getting JSON Values" :::

## Querying with LINQ

JObject/JArray can also be queried using LINQ. [JToken.Children](/api/newtonsoft/json/linq/jtoken/#method-children) returns the children values of a JObject/JArray as an `IEnumerable<JToken>` that can then be queried with the standard Where/OrderBy/Select LINQ operators.

:::
[JToken.Children](/api/newtonsoft/json/linq/jtoken/#method-children) returns all the children of a token. If it is a JObject it will return a collection of properties to work with, and if it is a JArray you will get a collection of the array's values.
:::

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonQuerying" title="Querying JSON" :::

LINQ to JSON can also be used to manually convert JSON to a .NET object.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonDeserializeObject" title="Deserializing Using LINQ Objects" :::

Manually serializing and deserializing between .NET objects is useful when you are working with JSON that doesn't closely match your .NET objects.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonDeserializeExample" title="Deserializing Using LINQ Example" :::

## See Also

- [LINQ to JSON](README.md)
- [JToken.Item(object)](/api/newtonsoft/json/linq/jtoken/#property-item)
- [JToken.Children](/api/newtonsoft/json/linq/jtoken/#method-children)