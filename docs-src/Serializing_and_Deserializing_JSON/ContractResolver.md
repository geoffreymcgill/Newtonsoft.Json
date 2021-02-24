# Serialization using ContractResolver

The [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/) interface provides a way to customize how the JsonSerializer serializes and deserializes .NET objects to JSON without placing attributes on your classes.

Anything that can be set on an object, collection, property, etc, using attributes or methods to control serialization can also be set using an IContractResolver.

:::
For performance you should create a contract resolver once and reuse instances when possible. Resolving contracts is slow and implementations of [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/) typically cache contracts.
:::

## DefaultContractResolver

The [DefaultContractResolver](/api/newtonsoft/json/serialization/defaultcontractresolver/) is the default resolver used by the serializer. It provides many avenues of extensibility in the form of virtual methods that can be overridden.

## CamelCasePropertyNamesContractResolver

[CamelCasePropertyNamesContractResolver](/api/newtonsoft/json/serialization/camelcasepropertynamescontractresolver/) inherits from DefaultContractResolver and simply overrides the JSON property name to be written in [camelcase](http://en.wikipedia.org/wiki/CamelCase).

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ContractResolver" title="ContractResolver" :::

## Custom IContractResolver Examples

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/PerformanceTests.cs" region="JsonConverterContractResolver" title="Use JsonConverter with IContractResolver" :::

This example sets a [JsonConverter](/api/newtonsoft/json/jsonconverter/) for a type using an IContractResolver. Using a contract resolver here is useful because DateTime is not your own type and it is not possible to place a JsonConverterAttribute on it.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/ConditionalPropertiesTests.cs" region="ShouldSerializeContractResolver" title="Conditional properties with IContractResolver" :::

This example sets up [ConditionalProperties](conditional serialization for a property) using an IContractResolver. This is useful if you want to conditionally serialize a property but don't want to add additional methods to your type.

## See Also

- [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/)
- [DefaultContractResolver](/api/newtonsoft/json/serialization/defaultcontractresolver/)
- [CamelCasePropertyNamesContractResolver](/api/newtonsoft/json/serialization/camelcasepropertynamescontractresolver/)