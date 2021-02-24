# JsonObjectAttribute force object serialization

This sample uses [JsonObjectAttribute](/api/newtonsoft/json/jsonobjectattribute/) to serialize a class that implements [IEnumerable](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.ienumerable) as a JSON object instead of a JSON array.

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/JsonObjectAttributeOverrideIEnumerable.cs" region="Types" title="Types" :::

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/JsonObjectAttributeOverrideIEnumerable.cs" region="Usage" title="Usage" :::
