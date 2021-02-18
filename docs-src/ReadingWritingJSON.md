# Basic Reading and Writing JSON

To manually read and write JSON, Json.NET provides the [JsonReader](/API/newtonsoft/json/jsonreader/) and [JsonWriter](/API/newtonsoft/json/jsonwriter/) classes.

## JsonTextReader and JsonTextWriter

:::
JsonReader and JsonWriter are low-level classes and are primarily for internal use by Json.NET. To quickly work with JSON, either the serializer - [Serializing and Deserializing JSON](Serializing_and_Deserializing_JSON/README.md) - or using [LINQ to JSON](LINQ_to_JSON/README.md) is recommended.
:::

[JsonTextReader](/API/newtonsoft/json/jsontextreader/) and [JsonTextWriter](/API/newtonsoft/json/jsontextwriter/) are used to read and write JSON text. The JsonTextWriter has a number of settings on it to control how JSON is formatted when it is written. These options include formatting, indentation character, indent count, and quote character.

```csharp Writing JSON with JsonTextWriter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ReadingAndWritingJsonTests.cs
region: ReadingAndWritingJsonText
```

JsonTextReader has settings on it for reading different date formats, time zones, and the cultures when reading text values.

```csharp Reading JSON with JsonTextReader
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ReadingAndWritingJsonTests.cs
region: ReadingJsonText
```

## JTokenReader and JTokenWriter

[JTokenReader](/API/newtonsoft/json/linq/jtokenreader/) and [JTokenWriter](/API/newtonsoft/json/linq/jtokenwriter/) read and write LINQ to JSON objects. They are located in the [Newtonsoft.Json.Linq](N:Newtonsoft.Json.Linq) namespace. These objects allow you to use LINQ to JSON objects with objects that read and write JSON, such as the JsonSerializer. For example you can deserialize from a LINQ to JSON object into a regular .NET object and vice versa.

```csharp Deserializing with JTokenReader
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ReadingAndWritingJsonTests.cs
region: ReadingAndWritingJsonLinq
```

## See Also

- [JsonReader](/API/newtonsoft/json/jsonreader/)
- [JsonWriter](/API/newtonsoft/json/jsonwriter/)
- [JTokenReader](/API/newtonsoft/json/linq/jtokenreader/)
- [JTokenWriter](/API/newtonsoft/json/linq/jtokenwriter/)
- [BsonReader](/API/newtonsoft/json/bson/bsonreader/)
- [BsonWriter](/API/newtonsoft/json/bson/bsonwriter/)