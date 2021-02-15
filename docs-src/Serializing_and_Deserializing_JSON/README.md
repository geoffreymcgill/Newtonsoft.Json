# Serializing and Deserializing JSON

The quickest method of converting between JSON text and a .NET object is using the [JsonSerializer](T:Newtonsoft.Json.JsonSerializer). The JsonSerializer converts .NET objects into their JSON equivalent and back again by mapping the .NET object property names to the JSON property names and copies the values for you.

## JsonConvert

For simple scenarios where you want to convert to and from a JSON string, the [Overload:Newtonsoft.Json.JsonConvert.SerializeObject](Overload:Newtonsoft.Json.JsonConvert.SerializeObject) and [Overload:Newtonsoft.Json.JsonConvert.DeserializeObject](Overload:Newtonsoft.Json.JsonConvert.DeserializeObject) methods on JsonConvert provide an easy-to-use wrapper over JsonSerializer.

```csharp Serializing and Deserializing JSON with JsonConvert
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializeObject
```

SerializeObject and DeserializeObject both have overloads that take a [JsonSerializerSettings](T:Newtonsoft.Json.JsonSerializerSettings) object. JsonSerializerSettings lets you use many of the JsonSerializer settings listed below while still using the simple serialization methods.

## JsonSerializer

For more control over how an object is serialized, the [JsonSerializer](T:Newtonsoft.Json.JsonSerializer) can be used directly. The JsonSerializer is able to read and write JSON text directly to a stream via [JsonTextReader](T:Newtonsoft.Json.JsonTextReader) and [JsonTextWriter](T:Newtonsoft.Json.JsonTextWriter). Other kinds of JsonWriters can also be used, such as

[JTokenReader](T:Newtonsoft.Json.Linq.JTokenReader) T:Newtonsoft.Json.Linq.JTokenWriter](T:Newtonsoft.Json.Linq.JTokenReader</codeEntityReference>/<codeEntityReference>T:Newtonsoft.Json.Linq.JTokenWriter), to convert your object to and from LINQ to JSON objects, or [Bson.BsonReader</codeEntityReference>/<codeEntityReference>T:Newtonsoft.Json.Bson.BsonWriter](T:Newtonsoft.Json.Bson.BsonReader</codeEntityReference>/<codeEntityReference>T:Newtonsoft.Json.Bson.BsonWriter), to convert to and from BSON.

```csharp Serializing JSON to a Stream with JsonSerializer
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: JsonSerializerToStream
```

JsonSerializer has a number of properties on it to customize how it serializes JSON. These can also be used with the methods on JsonConvert via the JsonSerializerSettings overloads.

You can read more about the available JsonSerializer settings here:

- [SerializationSettings](SerializationSettings.md)

## See Also

- [SerializationGuide](SerializationGuide.md)
- [SerializationSettings](SerializationSettings.md)
- [SerializationAttributes](SerializationAttributes.md)
- [SerializingJSONFragments](SerializingJSONFragments.md)
- [JsonConvert](T:Newtonsoft.Json.JsonConvert)
- [JsonSerializer](T:Newtonsoft.Json.JsonSerializer)
- [JsonSerializerSettings](T:Newtonsoft.Json.JsonSerializerSettings)