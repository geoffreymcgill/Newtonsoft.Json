# Deserializing Partial JSON Fragments

Often when working with large JSON documents you're only interested in a small fragment of information. This scenario can be annoying when you want to deserialize that JSON fragment into .NET objects because you have to define .NET classes for the entire JSON result.

With Json.NET it is easy to get around this problem. Using LINQ to JSON you can extract the pieces of JSON you want to deserialize before passing them to the Json.NET serializer.

```csharp Fragments Object
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializingPartialJsonFragmentsObject
```

```csharp Deserializing Partial JSON Fragment Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializingPartialJsonFragmentsExample
```

## See Also

- [JsonReader](/api/newtonsoft/json/jsonreader/)
- [JsonWriter](/api/newtonsoft/json/jsonwriter/)
- [JTokenReader](/api/newtonsoft/json/linq/jtokenreader/)
- [JTokenWriter](/api/newtonsoft/json/linq/jtokenwriter/)
- [BsonReader](/api/newtonsoft/json/bson/bsonreader/)
- [BsonWriter](/api/newtonsoft/json/bson/bsonwriter/)