# Querying JSON with SelectToken

[SelectToken()](/API/newtonsoft/json/linq/JToken/#method-selecttoken) provides a method to query LINQ to JSON using a single string path to a desired [JToken](/api/newtonsoft/json/linq/jtoken/). SelectToken makes dynamic queries easy because the entire query is defined in a string.

## SelectToken

SelectToken is a method on JToken and takes a string path to a child token. SelectToken returns the child token or a null reference if a token couldn't be found at the path's location.

The path is made up of property names and array indexes separated by periods, e.g. `Manufacturers[0].Name`.

```csharp SelectToken Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: SelectTokenComplex
```

## SelectToken with JSONPath

SelectToken supports JSONPath queries. Find out more about JSONPath [here](https://goessner.net/articles/JsonPath/).

```csharp SelectToken With JSONPath
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\JsonPath\QueryJsonSelectTokenJsonPath.cs
region: Usage
```

## SelectToken with LINQ

SelectToken can be used in combination with standard LINQ methods.

```csharp SelectToken With LINQ Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: SelectTokenLinq
```

## See Also

- [LINQ to JSON](README.md)
- [SelectToken()](/API/newtonsoft/json/linq/JToken/#method-selecttoken)
