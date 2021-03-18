# Reducing Serialized JSON Size

One of the common problems encountered when serializing .NET objects to JSON is that the JSON ends up containing a lot of unwanted properties and values. This can be especially significant when returning JSON to the client. More JSON means more bandwidth and a slower website.

To solve the issue of unwanted JSON, Json.NET has a range of built-in options to fine-tune what gets written from a serialized object.

## JsonIgnoreAttribute and DataMemberAttribute

By default Json.NET will include all of a class's public properties and fields in the JSON it creates. Adding the [JsonIgnoreAttribute](/api/newtonsoft/json/jsonignoreattribute/) to a property tells the serializer to always skip writing it to the JSON result.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeOptOut" title="Opt-out Serialization Example" :::

If a class has many properties and you only want to serialize a small subset of them, then adding JsonIgnore to all the others will be tedious and error prone. The way to tackle this scenario is to add the [DataContractAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.datacontractattribute) to the class and [DataMemberAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.datamemberattribute) to the properties to serialize. This is opt-in serialization - only the properties you mark up will be serialized, unlike opt-out serialization using JsonIgnoreAttribute.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeOptIn" title="Opt-in Serialization Example" :::

## Formatting

JSON written by the serializer with an option of [Formatting](/api/newtonsoft/json/formatting/) set to Indented produces nicely formatted, easy-to-read JSON that is great for readability when you are developing. `Formatting.None` on the other hand keeps the JSON result small, skipping all unnecessary spaces and line breaks to produce the most compact and efficient JSON possible.

## NullValueHandling

[NullValueHandling](/api/newtonsoft/json/nullvaluehandling/) is an option on the JsonSerializer and controls how the serializer handles properties with a null value. By setting a value of NullValueHandling.Ignore the JsonSerializer skips writing any properties that have a value of null.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeNullValueHandlingObject" title="NullValueHandling Class" :::

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeNullValueHandlingExample" title="NullValueHandling Ignore Example" :::

NullValueHandling can also be customized on individual properties using the [JsonPropertyAttribute](/api/newtonsoft/json/jsonpropertyattribute/). The JsonPropertyAttribute value of NullValueHandling will override the setting on the JsonSerializer for that property.

## DefaultValueHandling

[DefaultValueHandling](/api/newtonsoft/json/defaultvaluehandling/) is an option on the JsonSerializer and controls how the serializer handles properties with a default value. Setting a value of DefaultValueHandling.Ignore will make the JsonSerializer skip writing any properties that have a default value to the JSON result. For object references this will be null. For value types like int and DateTime the serializer will skip the default uninitialized value for that value type.

Json.NET also allows you to customize what the default value of an individual
property is using the [DefaultValueAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.defaultvalueattribute). For example, if a string property called Department always returns an empty string in its default state and you don't want that empty string in your JSON, then placing the DefaultValueAttribute on Department with that value will mean Department is no longer written to JSON unless it has a value.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeDefaultValueHandlingObject" title="DefaultValueHandling Class" :::

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeDefaultValueHandlingExample" title="DefaultValueHandling Ignore Example" :::

DefaultValueHandling can also be customized on individual properties using the [JsonPropertyAttribute](/api/newtonsoft/json/jsonpropertyattribute/). The JsonPropertyAttribute value of DefaultValueHandling will override the setting on the JsonSerializer for that property.

## IContractResolver

For more flexibility, the [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/) provides an interface to customize almost every aspect of how a .NET object gets serialized to JSON, including changing serialization behavior at runtime.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeContractResolverObject" title="IContractResolver Class" :::

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/SerializationTests.cs" region="ReducingSerializedJsonSizeContractResolverExample" title="IContractResolver Example" :::

## See Also

- [Formatting](/api/newtonsoft/json/formatting/)
- [JsonIgnoreAttribute](/api/newtonsoft/json/jsonignoreattribute/)
- [DefaultValueHandling](/api/newtonsoft/json/defaultvaluehandling/)
- [NullValueHandling](/api/newtonsoft/json/nullvaluehandling/)