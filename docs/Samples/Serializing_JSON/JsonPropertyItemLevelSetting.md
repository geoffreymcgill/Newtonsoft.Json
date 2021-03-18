# JsonPropertyAttribute items setting

This sample uses [JsonPropertyAttribute](/api/newtonsoft/json/jsonpropertyattribute/) to change how the property value's items are serialized, e.g. setting ItemIsReference to true on a property with a collection will serialize all the collection's items with reference tracking enabled.

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/JsonPropertyItemLevelSetting.cs" region="Types" title="Types" :::

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/JsonPropertyItemLevelSetting.cs" region="Usage" title="Usage" :::
