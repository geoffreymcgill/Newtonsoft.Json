# JsonObjectAttribute opt-in serialization

This sample uses [JsonObjectAttribute](T:Newtonsoft.Json.JsonObjectAttribute) and [MemberSerialization](T:Newtonsoft.Json.MemberSerialization) to specify that  only properties that have been explicitly specified with [JsonPropertyAttribute](T:Newtonsoft.Json.JsonPropertyAttribute) should be serialized.

## Sample

```csharp Types
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\JsonObjectAttributeOptIn.cs
region: Types
```

```csharp Usage
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\JsonObjectAttributeOptIn.cs
region: Usage
```
