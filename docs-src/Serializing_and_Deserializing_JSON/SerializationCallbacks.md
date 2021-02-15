# Serialization Callbacks

Json.NET supports serialization callback methods. A callback can be used to manipulate an object before and after its serialization and deserialization by the JsonSerializer.

- **OnSerializing**
- **OnSerialized**
- **OnDeserializing**
- **OnDeserialized**

To tell the serializer which methods should be called during the object's serialization lifecycle, decorate a method with the appropriate attribute ([OnSerializingAttribute](T:System.Runtime.Serialization.OnSerializingAttribute), [OnSerializedAttribute](T:System.Runtime.Serialization.OnSerializedAttribute), [OnDeserializingAttribute](T:System.Runtime.Serialization.OnDeserializingAttribute), [OnDeserializedAttribute](T:System.Runtime.Serialization.OnDeserializedAttribute)).

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

- [OnSerializingAttribute](T:System.Runtime.Serialization.OnSerializingAttribute)
- [OnSerializedAttribute](T:System.Runtime.Serialization.OnSerializedAttribute)
- [OnDeserializingAttribute](T:System.Runtime.Serialization.OnDeserializingAttribute)
- [OnDeserializedAttribute](T:System.Runtime.Serialization.OnDeserializedAttribute)