# Creating JSON

As well as parsing JSON from existing JSON strings, LINQ to JSON objects can be created from scratch to create new JSON structures.

## Manually Creating JSON

Setting values and creating objects and arrays one at a time gives you total control, but it is more verbose than other options.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonCreateNormal" title="Creating JSON" :::

## Creating JSON with LINQ

Declaratively creating JSON objects using LINQ is a fast way to create JSON from collections of values.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonCreateDeclaratively" title="Creating JSON Declaratively" :::

## Creating JSON from an object

The last option is to create a JSON object from a non-JSON type using the [FromObject](/API/newtonsoft/json/linq/JObject/#method-fromobject) method. Internally, FromObject will use the JsonSerializer to serialize the object to LINQ to JSON objects instead of text.

The example below shows creating a JSON object from an anonymous object, but any .NET type can be used with FromObject to create JSON.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonCreateFromObject" title="Creating JSON from an Object" :::

## See Also

- [LINQ to JSON](README.md)
- [JObject.FromObject](/API/newtonsoft/json/linq/JObject/#method-fromobject)