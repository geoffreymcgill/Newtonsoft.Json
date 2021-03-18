# CustomCreationConverter

The [CustomCreationConverter<T>](/api/newtonsoft/json/converters/customcreationconverter/) is a JsonConverter that provides a way to customize how an object is created during JSON deserialization. Once the object has been created it will then have values populated onto it by the serializer.

## Example

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="CustomCreationConverterObject" title="CustomCreationConverter" :::

This is an extremely simple example. A more complicated scenario could involve an object factory or service locator that resolves the object at runtime.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="CustomCreationConverterExample" title="CustomCreationConverter Example" :::

## See Also

- [CustomCreationConverter](/api/newtonsoft/json/converters/customcreationconverter/)