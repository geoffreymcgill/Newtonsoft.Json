# Serializing Collections

Json.NET has excellent support for serializing and deserializing collections of objects.

## Serializing Collections

To serialize a collection - a generic list, array, dictionary, or your own custom collection - simply call the serializer with the object you want to get JSON for. Json.NET will serialize the collection and all of the values it contains.

```csharp Serializing Collections
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializingCollectionsSerializing
```

## Deserializing Collections

To deserialize JSON into a .NET collection, just specify the collection type you want to deserialize to. Json.NET supports a wide range of collection types.

```csharp Deserializing Collections
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializingCollectionsDeserializing
```

## Deserializing Dictionaries

Using Json.NET you can also deserialize a JSON object into a .NET generic dictionary. The JSON object's property names and values will be added to the dictionary.

```csharp Deserializing Dictionaries
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializingCollectionsDeserializingDictionaries
```

## See Also

- [Serialization Guide](SerializationGuide.md)
- [JsonConvert](/api/newtonsoft/json/jsonconvert/)
- [JsonSerializer](/api/newtonsoft/json/jsonserializer/)