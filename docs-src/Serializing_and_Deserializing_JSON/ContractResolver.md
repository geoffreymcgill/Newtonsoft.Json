# Serialization using ContractResolver

The [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver) interface provides a way to customize how the JsonSerializer serializes and deserializes .NET objects to JSON without placing attributes on your classes.

Anything that can be set on an object, collection, property, etc, using attributes or methods to control serialization can also be set using an IContractResolver.

:::
For performance you should create a contract resolver once and reuse instances when possible. Resolving contracts is slow and implementations of [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver) typically cache contracts.
:::

## DefaultContractResolver

The [DefaultContractResolver](T:Newtonsoft.Json.Serialization.DefaultContractResolver) is the default resolver used by the serializer. It provides many avenues of extensibility in the form of virtual methods that can be overridden.

## CamelCasePropertyNamesContractResolver

[CamelCasePropertyNamesContractResolver](T:Newtonsoft.Json.Serialization.CamelCasePropertyNamesContractResolver) inherits from DefaultContractResolver and simply overrides the JSON property name to be written in [camelcase](http://en.wikipedia.org/wiki/CamelCase).

```csharp ContractResolver
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: ContractResolver
```

## Custom IContractResolver Examples

```csharp Use JsonConverter with IContractResolver
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: JsonConverterContractResolver
```

This example sets a [JsonConverter](T:Newtonsoft.Json.JsonConverter) for a type using an IContractResolver. Using a contract resolver here is useful because DateTime is not your own type and it is not possible to place a JsonConverterAttribute on it.

```csharp Conditional properties with IContractResolver
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConditionalPropertiesTests.cs
region: ShouldSerializeContractResolver
```

This example sets up [ConditionalProperties](conditional serialization for a property) using an IContractResolver. This is useful if you want to conditionally serialize a property but don't want to add additional methods to your type.

## See Also

- [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver)
- [DefaultContractResolver](T:Newtonsoft.Json.Serialization.DefaultContractResolver)
- [CamelCasePropertyNamesContractResolver](T:Newtonsoft.Json.Serialization.CamelCasePropertyNamesContractResolver)