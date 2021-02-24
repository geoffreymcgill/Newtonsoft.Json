# Serializing and Deserializing JSON

The quickest method of converting between JSON text and a .NET object is using the [JsonSerializer](/api/newtonsoft/json/jsonserializer/). The JsonSerializer converts .NET objects into their JSON equivalent and back again by mapping the .NET object property names to the JSON property names and copies the values for you.

## JsonConvert

For simple scenarios where you want to convert to and from a JSON string, the [SerializeObject()](/API/newtonsoft/json/jsonconvert/#method-serializeobject) and [DeserializeObject()](/API/newtonsoft/json/jsonconvert/#method-deserializeobject) methods on JsonConvert provide an easy-to-use wrapper over JsonSerializer.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="SerializeObject" title="Serializing and Deserializing JSON with JsonConvert" :::

SerializeObject and DeserializeObject both have overloads that take a [JsonSerializerSettings](/api/newtonsoft/json/jsonserializersettings/) object. JsonSerializerSettings lets you use many of the JsonSerializer settings listed below while still using the simple serialization methods.

## JsonSerializer

For more control over how an object is serialized, the [JsonSerializer](/api/newtonsoft/json/jsonserializer/) can be used directly. The JsonSerializer is able to read and write JSON text directly to a stream via [JsonTextReader](/api/newtonsoft/json/jsontextreader/) and [JsonTextWriter](/api/newtonsoft/json/jsontextwriter/). Other kinds of JsonWriters can also be used, such as [JTokenReader](/API/newtonsoft/json/linq/JTokenReader/)/[JTokenWriter](/API/newtonsoft/json/linq/JTokenWriter/), to convert your object to and from LINQ to JSON objects, or [BsonReader](/API/newtonsoft/json/bson/bsonreader/)/[BsonWriter](/API/newtonsoft/json/bson/bsonwriter/), to convert to and from BSON.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="JsonSerializerToStream" title="Serializing JSON to a Stream with JsonSerializer" :::

JsonSerializer has a number of properties on it to customize how it serializes JSON. These can also be used with the methods on JsonConvert via the JsonSerializerSettings overloads.

You can read more about the available JsonSerializer settings here:

- [SerializationSettings](SerializationSettings.md)

## See Also

- [Serialization Guide](SerializationGuide.md)
- [Serialization Settings](SerializationSettings.md)
- [Serialization Attributes](SerializationAttributes.md)
- [Deserializing Partial JSON Fragments](SerializingJSONFragments.md)
- [JsonConvert](/api/newtonsoft/json/jsonconvert/)
- [JsonSerializer](/api/newtonsoft/json/jsonserializer/)
- [JsonSerializerSettings](/api/newtonsoft/json/jsonserializersettings/)