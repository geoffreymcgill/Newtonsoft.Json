# JsonObjectAttribute opt-in serialization

This sample uses [JsonObjectAttribute](/api/newtonsoft/json/jsonobjectattribute/) and [MemberSerialization](/api/newtonsoft/json/memberserialization/) to specify that  only properties that have been explicitly specified with [JsonPropertyAttribute](/api/newtonsoft/json/jsonpropertyattribute/) should be serialized.

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/JsonObjectAttributeOptIn.cs" region="Types" title="Types" :::

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/JsonObjectAttributeOptIn.cs" region="Usage" title="Usage" :::
