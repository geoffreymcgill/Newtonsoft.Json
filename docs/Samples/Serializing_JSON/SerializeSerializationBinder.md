# Custom SerializationBinder

This sample creates a custom [SerializationBinder](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.serializationbinder) that writes only the type name when including type data in JSON.

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/SerializeSerializationBinder.cs" region="Types" title="Types" :::

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Serializer/SerializeSerializationBinder.cs" region="Usage" title="Usage" :::
