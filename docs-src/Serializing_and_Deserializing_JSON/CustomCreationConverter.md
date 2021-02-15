# CustomCreationConverter

The [CustomCreationConverter<T>](T:Newtonsoft.Json.Converters.CustomCreationConverter) is a JsonConverter that provides a way to customize how an object is created during JSON deserialization. Once the object has been created it will then have values populated onto it by the serializer.

## Example

```csharp CustomCreationConverter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: CustomCreationConverterObject
```

This is an extremely simple example. A more complicated scenario could involve an object factory or service locator that resolves the object at runtime.

```csharp CustomCreationConverter Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: CustomCreationConverterExample
```

## See Also

- [CustomCreationConverter](T:Newtonsoft.Json.Converters.CustomCreationConverter)