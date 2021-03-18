# Custom IContractResolver

This sample creates a custom [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/) that only serializes a type's properties that begin with a specified character.

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/CustomContractResolver.cs" region="Types" title="Types" :::

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/CustomContractResolver.cs" region="Usage" title="Usage" :::
