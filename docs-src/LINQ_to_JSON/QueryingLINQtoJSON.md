# Querying JSON with LINQ

LINQ to JSON provides a number of methods for getting data from its objects. The index methods on JObject/JArray let you quickly get data by its property name on an object or index in a collection, while [JToken.Children](/API/newtonsoft/json/linq/jtoken/#method-children) lets you get ranges of data as `IEnumerable<JToken>` to then query using LINQ.

## Getting values by Property Name or Collection Index

The simplest way to get a value from LINQ to JSON is to use the [JToken.Item(object)](/API/newtonsoft/json/linq/jtoken/#property-item)(object) index on JObject/JArray and then cast the returned [JValue](/API/newtonsoft/json/linq/jvalue/) to the type you want.

```csharp Getting JSON Values
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonSimpleQuerying
```

## Querying with LINQ

JObject/JArray can also be queried using LINQ. [JToken.Children](/API/newtonsoft/json/linq/jtoken/#method-children) returns the children values of a JObject/JArray as an `IEnumerable<JToken>` that can then be queried with the standard Where/OrderBy/Select LINQ operators.

:::
[JToken.Children](/API/newtonsoft/json/linq/jtoken/#method-children) returns all the children of a token. If it is a JObject it will return a collection of properties to work with, and if it is a JArray you will get a collection of the array's values.
:::

```csharp Querying JSON
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonQuerying
```

LINQ to JSON can also be used to manually convert JSON to a .NET object.

```csharp Deserializing Using LINQ Objects
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonDeserializeObject
```

Manually serializing and deserializing between .NET objects is useful when you are working with JSON that doesn't closely match your .NET objects.

```csharp Deserializing Using LINQ Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonDeserializeExample
```

## See Also

- [LINQ to JSON](README.md)
- [JToken.Item(object)](/API/newtonsoft/json/linq/jtoken/#property-item)(object)
- [JToken.Children](/API/newtonsoft/json/linq/jtoken/#method-children)