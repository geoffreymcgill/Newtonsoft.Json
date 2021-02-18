# Serialization Attributes

Attributes can be used to control how Json.NET serializes and deserializes .NET objects.

- [JsonObjectAttribute](/API/newtonsoft/json/jsonobjectattribute/) - Placed on classes to control how they should be serialized as a JSON object.
- [JsonArrayAttribute](/API/newtonsoft/json/jsonarrayattribute/) - Placed on collections to control how they should be serialized as a JSON array.
- [JsonDictionaryAttribute](/API/newtonsoft/json/jsondictionaryattribute/) - Placed on dictionaries to control how they should be serialized as a JSON object.
- [JsonPropertyAttribute](/API/newtonsoft/json/jsonpropertyattribute/) - Placed on fields and properties to control how they should be serialized as a property in a JSON object.
- [JsonConverterAttribute](/API/newtonsoft/json/jsonconverterattribute/) - Placed on either classes or fields and properties to specify which JsonConverter should be used during serialization.
- [JsonExtensionDataAttribute](/API/newtonsoft/json/jsonextensiondataattribute/) - Placed on a collection field or property to deserialize properties with no matching class member into the specified collection and write values during serialization.
- [JsonConstructorAttribute](/API/newtonsoft/json/jsonconstructorattribute/) - Placed on a constructor to specify that it should be used to create the class during deserialization.

## Standard .NET Serialization Attributes

As well as using the built-in Json.NET attributes, Json.NET also looks for the [SerializableAttribute](T:System.SerializableAttribute) (if IgnoreSerializableAttribute on DefaultContractResolver is set to false) [DataContractAttribute](T:System.Runtime.Serialization.DataContractAttribute), [DataMemberAttribute](T:System.Runtime.Serialization.DataMemberAttribute), and [NonSerializedAttribute](T:System.NonSerializedAttribute) and attributes when determining how JSON is to be serialized and deserialized.

:::
Json.NET attributes take precedence over standard .NET serialization attributes (e.g. if both JsonPropertyAttribute and DataMemberAttribute are present on a property and both customize the name, the name from JsonPropertyAttribute will be used).
:::

```csharp Serialization Attributes Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationAttributes
```

## Json.NET Serialization Attributes

## JsonObjectAttribute

The MemberSerialization flag on this attribute specifies whether member serialization is opt-in (a member must have the JsonProperty or DataMember attribute to be serialized), opt-out (everything is serialized by default but can be ignored with the JsonIgnoreAttribute, Json.NET's default behavior) or fields (all public and private fields are serialized and properties are ignored).

Placing the the [DataContractAttribute](T:System.Runtime.Serialization.DataContractAttribute) on a type is another way to default member serialization to opt-in.

The NamingStrategy setting on this attributes can be set to a [NamingStrategy](/API/newtonsoft/json/serialization/namingstrategy/) type that specifies how property names are serialized.

Json.NET serializes .NET classes that implement IEnumerable as a JSON array populated with the IEnumerable values. Placing the [JsonObjectAttribute](/API/newtonsoft/json/jsonobjectattribute/) overrides this behavior and forces the serializer to serialize the class's fields and properties.

## JsonArrayAttribute/JsonDictionaryAttribute

The [JsonArrayAttribute](/API/newtonsoft/json/jsonarrayattribute/) and [JsonDictionaryAttribute](/API/newtonsoft/json/jsondictionaryattribute/) are used to specify whether a class is serialized as that collection type.

The collection attributes have options to customize the JsonConverter, type name handling, and reference handling that are applied to collection items.

## JsonPropertyAttribute

JsonPropertyAttribute has a number of uses:

- By default, the JSON property will have the same name as the .NET property. This attribute allows the name to be customized.
- JsonPropertyAttribute indicates that a property should be serialized when member serialization is set to opt-in.
- It includes non-public properties in serialization and deserialization.
- It can be used to customize type name, reference, null, and default value handling for the property value.
- It can be used to customize the [NamingStrategy](/API/newtonsoft/json/serialization/namingstrategy/) of the serialized property name.
- It can be used to customize the property's collection items JsonConverter, type name handling, and reference handling.

The DataMemberAttribute can be used as a substitute for JsonPropertyAttribute.

## JsonIgnoreAttribute

Excludes a field or property from serialization.

The [NonSerializedAttribute](T:System.NonSerializedAttribute) can be used as a substitute for JsonIgnoreAttribute.

## JsonConverterAttribute

The [JsonConverterAttribute](/API/newtonsoft/json/jsonconverterattribute/) specifies which [JsonConverter](/API/newtonsoft/json/jsonconverter/) is used to convert an object.

The attribute can be placed on a class or a member. When placed on a class, the JsonConverter specified by the attribute will be the default way of serializing that class. When the attribute is on a field or property, then the specified JsonConverter will always be used to serialize that value.

The priority of which JsonConverter is used is member attribute, then class attribute, and finally any converters passed to the JsonSerializer.

```csharp JsonConverterAttribute Property Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\JsonConverterAttributeProperty.cs
region: Types
```

This example shows the JsonConverterAttribute being applied to a property.

To apply a JsonConverter to the items in a collection, use either [JsonArrayAttribute](/API/newtonsoft/json/jsonarrayattribute/), [JsonDictionaryAttribute](/API/newtonsoft/json/jsondictionaryattribute/) or [JsonPropertyAttribute](/API/newtonsoft/json/jsonpropertyattribute/) and set the ItemConverterType property to the converter type you want to use.

## JsonExtensionDataAttribute

The [JsonExtensionDataAttribute](/API/newtonsoft/json/jsonextensiondataattribute/) instructs the [JsonSerializer](/API/newtonsoft/json/jsonserializer/) to deserialize properties with no matching field or property on the type into the specified collection. During serialization the values in this collection are written back to the instance's JSON object.

:::
All extension data values will be written during serialization, even if a property the same name has already been written.
:::

This example shows the JsonExtensionDataAttribute being applied to a field, unmatched JSON properties being added to the field's collection during deserialization.

```csharp Types
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\DeserializeExtensionData.cs
region: Types
```

```csharp Usage
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\DeserializeExtensionData.cs
region: Usage
```

## JsonConstructorAttribute

The [JsonConstructorAttribute](/API/newtonsoft/json/jsonconstructorattribute/) instructs the [JsonSerializer](/API/newtonsoft/json/jsonserializer/) to use a specific constructor when deserializing a class. It can be used to create a class using a parameterized constructor instead of the default constructor, or to pick which specific parameterized constructor to use if there are multiple.

```csharp Types
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\JsonConstructorAttribute.cs
region: Types
```

```csharp Usage
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Serializer\JsonConstructorAttribute.cs
region: Usage
```

## See Also

- [JsonObjectAttribute](/API/newtonsoft/json/jsonobjectattribute/)
- [JsonArrayAttribute](/API/newtonsoft/json/jsonarrayattribute/)
- [JsonDictionaryAttribute](/API/newtonsoft/json/jsondictionaryattribute/)
- [JsonPropertyAttribute](/API/newtonsoft/json/jsonpropertyattribute/)
- [JsonConverterAttribute](/API/newtonsoft/json/jsonconverterattribute/)
- [JsonExtensionDataAttribute](/API/newtonsoft/json/jsonextensiondataattribute/)
- [JsonConstructorAttribute](/API/newtonsoft/json/jsonconstructorattribute/)