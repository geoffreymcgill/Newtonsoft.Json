# Creating JSON

As well as parsing JSON from existing JSON strings, LINQ to JSON objects can be created from scratch to create new JSON structures.

## Manually Creating JSON

Setting values and creating objects and arrays one at a time gives you total control, but it is more verbose than other options.

```csharp Creating JSON
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonCreateNormal
```

## Creating JSON with LINQ

Declaratively creating JSON objects using LINQ is a fast way to create JSON from collections of values.

```csharp Creating JSON Declaratively
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonCreateDeclaratively
```

## Creating JSON from an object

The last option is to create a JSON object from a non-JSON type using the [Overload:Newtonsoft.Json.Linq.JObject.FromObject](Overload:Newtonsoft.Json.Linq.JObject.FromObject) method. Internally, FromObject will use the JsonSerializer to serialize the object to LINQ to JSON objects instead of text.

The example below shows creating a JSON object from an anonymous object, but any .NET type can be used with FromObject to create JSON.

```csharp Creating JSON from an Object
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonCreateFromObject
```

## See Also

- [LINQ to JSON](README.md)
- [Overload:Newtonsoft.Json.Linq.JObject.FromObject](Overload:Newtonsoft.Json.Linq.JObject.FromObject)