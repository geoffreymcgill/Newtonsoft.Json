# Parsing JSON

LINQ to JSON has methods available for parsing JSON from a string or loading JSON directly from a file.

## Parsing JSON text

JSON values can be read from a string using [Parse(String)](M:Newtonsoft.Json.Linq.JToken.Parse(System.String)).

```csharp
lang="cs" source="..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs" region="LinqToJsonCreateParse" title="Parsing a JSON Object from text
```

```csharp Parsing a JSON Array from text
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonCreateParseArray
```

## Loading JSON from a file

JSON can also be loaded directly from a file using [ReadFrom(JsonReader)](M:Newtonsoft.Json.Linq.JToken.ReadFrom(Newtonsoft.Json.JsonReader)).

```csharp Reading JSON from a file
source: ..\Src\Newtonsoft.Json.Tests\Documentation\LinqToJsonTests.cs
region: LinqToJsonReadObject
```

## See Also

- [LINQ to JSON](LINQ_to_JSON/README.md)
- [Parse(String)](M:Newtonsoft.Json.Linq.JToken.Parse(System.String))
- [ReadFrom(JsonReader)](M:Newtonsoft.Json.Linq.JToken.ReadFrom(Newtonsoft.Json.JsonReader))