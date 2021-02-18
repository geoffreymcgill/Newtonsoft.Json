# Serialization Callbacks

Json.NET supports serialization callback methods. A callback can be used to manipulate an object before and after its serialization and deserialization by the JsonSerializer.

- **OnSerializing**
- **OnSerialized**
- **OnDeserializing**
- **OnDeserialized**

To tell the serializer which methods should be called during the object's serialization lifecycle, decorate a method with the appropriate attribute ([OnSerializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializingattribute), [OnSerializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializedattribute), [OnDeserializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializingattribute), [OnDeserializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializedattribute).

## Example

Example object with serialization callback methods:

```csharp Serialization Callback Attributes
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationCallbacksObject
```

The example object being serialized and deserialized by Json.NET:

```csharp Serialization Callback Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationCallbacksExample
```

## See Also

- [OnSerializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializingattribute)
- [OnSerializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.onserializedattribute)
- [OnDeserializingAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializingattribute)
- [OnDeserializedAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ondeserializedattribute)