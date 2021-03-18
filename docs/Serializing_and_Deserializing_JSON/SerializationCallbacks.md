# Serialization Callbacks

Json.NET supports serialization callback methods. A callback can be used to manipulate an object before and after its serialization and deserialization by the JsonSerializer.

- **OnSerializing**
- **OnSerialized**
- **OnDeserializing**
- **OnDeserialized**

To tell the serializer which methods should be called during the object's serialization lifecycle, decorate a method with the appropriate attribute ([OnSerializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializingattribute), [OnSerializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializedattribute), [OnDeserializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializingattribute), [OnDeserializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializedattribute).

## Example

Example object with serialization callback methods:

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="SerializationCallbacksObject" title="Serialization Callback Attributes" :::

The example object being serialized and deserialized by Json.NET:

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="SerializationCallbacksExample" title="Serialization Callback Example" :::

## See Also

- [OnSerializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializingattribute)
- [OnSerializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializedattribute)
- [OnDeserializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializingattribute)
- [OnDeserializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializedattribute)