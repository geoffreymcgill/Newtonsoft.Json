# Serialization Settings

JsonSerializer has a number of properties on it to customize how it serializes JSON. These can also be used with the methods on JsonConvert via the [JsonSerializerSettings](/api/newtonsoft/json/jsonserializersettings/) overloads.

## DateFormatHandling

[DateFormatHandling](/api/newtonsoft/json/dateformathandling/) controls how dates are serialized.

Member | Description
--- | ---
`IsoDateFormat` | By default Json.NET writes dates in the ISO 8601 format, e.g. `"2012-03-21T05:40Z"`.
`MicrosoftDateFormat` | Dates are written in the Microsoft JSON format, e.g. `"\/Date(1198908717056)\/"`.

## MissingMemberHandling

[MissingMemberHandling](/api/newtonsoft/json/missingmemberhandling/) controls how missing members, e.g. JSON contains a property that isn't a member on the object, are handled during deserialization.

Member | Description
--- | ---
`Ignore` | By default Json.NET ignores JSON if there is no field or property for its value to be set to during deserialization.
`Error` | Json.NET errors when there is a missing member during deserialization.

## ReferenceLoopHandling

[ReferenceLoopHandling](/api/newtonsoft/json/referenceloophandling/) controls how circular referencing objects,
e.g. a Person object referencing itself via a Manager property, are serialized.

The [Object.Equals(object)](M:System.Object.Equals(System.Object)) method is used to test whether an object is in a circular reference.
By default `Object.Equals(object)` will test whether the references are equal for reference types and private and public values
are equal for value types. Classes and structs can override this method.

Member | Description
--- | ---
`Error` | By default Json.NET will error if a reference loop is encountered (otherwise the serializer will get into an infinite loop).
`Ignore` | Json.NET will ignore objects in reference loops and not serialize them. The first time an object is encountered it will be serialized as usual but if the object is encountered as a child object of itself the serializer will skip serializing it.
`Serialize` | This option forces Json.NET to serialize objects in reference loops. This is useful if objects are nested but not indefinitely.

ReferenceLoopHandling can be used as an argument when calling the serializer, it can be set on an object's properties or a collection's items using [JsonContainerAttribute.ItemReferenceLoopHandling](/api/newtonsoft/json/jsoncontainerattribute/itemreferenceloophandling/#property-itemreferenceloophandling), customized on a property with [JsonPropertyAttribute.ReferenceLoopHandling](/api/newtonsoft/json/jsonpropertyattribute/referenceloophandling/#property-referenceloophandling) or a property's object properties or collection items using [JsonPropertyAttribute.ItemReferenceLoopHandling](/api/newtonsoft/json/jsonpropertyattribute/itemreferenceloophandling/#property-itemreferenceloophandling).

## NullValueHandling

[NullValueHandling](/api/newtonsoft/json/nullvaluehandling/) controls how null values on .NET objects are handled during serialization and how null values in JSON are handled during deserialization.

Member | Description
--- | ---
`Include` | By default Json.NET writes null values to JSON when serializing and sets null values to fields/properties when deserializing.
`Ignore` | Json.NET will skip writing JSON properties if the .NET value is null when serializing and will skip setting fields/properties if the JSON property is null when deserializing.

NullValueHandling can also be customized on individual properties with JsonPropertyAttribute.

## DefaultValueHandling

[DefaultValueHandling](/api/newtonsoft/json/defaultvaluehandling/) controls how Json.NET uses default values set using the .NET [DefaultValueAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.defaultvalueattribute) when serializing and deserializing.

Member | Description
--- | ---
`Include` | By default Json.NET will write a field/property value to JSON when serializing if the value is the same as the field/property's default value.
The Json.NET deserializer will continue setting a field/property if the JSON value is the same as the default value.
`Ignore` | Json.NET will skip writing a field/property value to JSON if the value is the same as the field/property's default value, or the custom value specified in [DefaultValueAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.defaultvalueattribute) if the attribute is present. The Json.NET deserializer will skip setting a .NET object's field/property if the JSON value is the same as the default value.

DefaultValueHandling can also be customized on individual properties with JsonPropertyAttribute.

## ObjectCreationHandling

- [ObjectCreationHandling](/api/newtonsoft/json/objectcreationhandling/) controls how objects are created and deserialized to during deserialization.

Member | Description
--- | ---
`Auto` | By default Json.NET will attempt to set JSON values onto existing objects and add JSON values to existing collections during deserialization. 
`Reuse` | Same behaviour as auto.
`Replace` | Json.NET will always recreate objects and collections before setting values to them during deserialization.

ObjectCreationHandling can also be customized on individual properties with JsonPropertyAttribute.

## TypeNameHandling

:::caution
[TypeNameHandling](/api/newtonsoft/json/typenamehandling/) should be used with caution when your application deserializes JSON from an external source.

Incoming types should be validated with a custom [ISerializationBinder](/api/newtonsoft/json/serialization/iserializationbinder/) when deserializing with a value other than `TypeNameHandling.None`.
:::

[TypeNameHandling](/api/newtonsoft/json/typenamehandling/) controls whether Json.NET includes .NET type names during serialization with a `$type` property and reads .NET type names from that property to determine what type to create during
deserialization.

Metadata properties like `$type` must be located at the beginning of a JSON object to be successfully detected during deserialization. If you can't control the order of properties in your JSON object then [MetadataPropertyHandling](/api/newtonsoft/json/metadatapropertyhandling/) can be used to remove this restriction.

The value of the `$type` property can be customized and validated by creating your own [ISerializationBinder](/api/newtonsoft/json/serialization/iserializationbinder/).

Member | Description
--- | ---
`None` | By default Json.NET does not read or write type names during deserialization.
`Objects` | Json.NET will write and use type names for objects but not collections.
`Arrays` | Json.NET will write and use type names for collections but not objects.
`Auto` | Json.NET will check whether an object/collection matches its declared property and writes the type name if they do not match, e.g. a property with a type of Mammal has a derived instance of Dog assigned. Auto will ensure that type information isn't lost when serializing/deserializing automatically without having to write type names for every object.
`All` | Json.NET will write and use type names for objects and collections.

TypeNameHandling can be used as an argument when calling the serializer, it can be set on an object's properties or a collection's items using [JsonContainerAttribute.ItemTypeNameHandling](/api/newtonsoft/json/jsoncontainerattribute/itemtypenamehandling/#property-itemtypenamehandling), customized on a property with [JsonPropertyAttribute.TypeNameHandling](/api/newtonsoft/json/jsonpropertyattribute/typenamehandling/#property-typenamehandling) or a property's object properties or collection items using [JsonPropertyAttribute.ItemTypeNameHandling](/api/newtonsoft/json/jsonpropertyattribute/itemtypenamehandling/#property-itemtypenamehandling).

## TypeNameAssemblyFormat

[FormatterAssemblyStyle](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.formatters.formatterassemblystyle) controls how type names are written during serialization.

Member | Description
--- | ---
`Simple` | By default Json.NET writes the partial assembly name with the type, e.g. System.Data.DataSet, System.Data. Note that Silverlight and Windows Phone are not able to use this format.
`Full` | Json.NET will write the full assembly name, including version number, culture and public key token.

Read more about the valid values at [FormatterAssemblyStyle](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.formatters.formatterassemblystyle).

## SerializationBinder

The [ISerializationBinder](/api/newtonsoft/json/serialization/iserializationbinder/) is used to resolve .NET types to type names during serialization and type names to .NET types during deserialization.

If TypeNameHandling is enabled then it is strongly recommended that a custom [ISerializationBinder](/api/newtonsoft/json/serialization/iserializationbinder/) is used to validate incoming type names for security reasons.

## MetadataPropertyHandling

[MetadataPropertyHandling](/api/newtonsoft/json/metadatapropertyhandling/) controls how metadata properties like `$type` and `$id` are read during deserialization.

For performance reasons by default the JsonSerializer assumes that any metadata properties are located at the beginning of a JSON object. If you are unable to guarantee the order of properties in JSON you are deserializing then `MetadataPropertyHandling.ReadAhead` removes this restriction at the cost of some performance.

Member | Description
--- | ---
`Default` | By default Json.NET will only read metadata properties that are at the beginning of a JSON object.
`ReadAhead` | Json.NET will look for metadata properties located anywhere in a JSON object.
`Ignore` | Json.NET will ignore metadata properties.

## ConstructorHandling

[ConstructorHandling](/api/newtonsoft/json/constructorhandling/) controls how constructors are used when initializing objects during deserialization.

Member | Description
--- | ---
`Default` | By default Json.NET will first look for a constructor marked with the JsonConstructorAttribute, then look for a public default constructor (a constructor that doesn't take any arguments), then check if the class has a single public constructor with arguments and finally check for a non-public default constructor. If the class has multiple public constructors with arguments an error will be thrown. This can be fixed by marking one of the constructors with the JsonConstructorAttribute.
`AllowNonPublicDefaultConstructor` | Json.NET will use a classes private default constructor before constructors with arguments if available. 

## Converters

This is the collection of JsonConverters that will be used during serialization and deserialization.

A [JsonConverter](/api/newtonsoft/json/jsonconverter/) allows JSON to be manually written during serialization and read during deserialization. This is useful for particularly complex JSON structures or for when you want to change how a type is serialized.

When a JsonConverter has been added to a JsonSerializer it will be checked for every value that is being serialized/deserialized using its CanConvert to see if it should be used. If CanConvert returns true then the JsonConverter will be used to read or write the JSON for that value. Note that while a JsonConverter gives you complete control over that values JSON, many Json.NET serialization features are no longer available like type name and reference handling.

JsonConverters can be used as an argument when calling the serializer, it can be set on an object or property using [JsonConverterAttribute](/api/newtonsoft/json/jsonconverterattribute/), it be set on an object's properties or a collection's items using [JsonContainerAttribute.ItemConverterType](/api/newtonsoft/json/jsoncontainerattribute/itemconvertertype/#property-itemconvertertype), or a property's object properties or collection items using [JsonPropertyAttribute.ItemConverterType](/api/newtonsoft/json/jsonpropertyattribute/itemconvertertype/#property-itemconvertertype).

To create your own custom converter inherit from the JsonConverter class. Read more about the built-in JsonConverters below:

- [Serializing Dates in JSON](DatesInJSON.md)
- [Converting between JSON and XML](../ConvertingJSONandXML.md)
- [CustomCreationConverter](CustomCreationConverter.md)
- [StringEnumConverter](/api/newtonsoft/json/converters/stringenumconverter/)

## ContractResolver

Internally for every .NET type the JsonSerializer will create a contract of how the type should be serialized and deserialized, based on type metadata and attributes applied to the class. Specifying a custom [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/) allows the creation of contracts to be customized.

Read more about Contract Resolvers here:

- [ContractResolver](ContractResolver.md.

## TraceWriter

The Json.NET serializer supports logging and debugging using the [ITraceWriter](/api/newtonsoft/json/serialization/itracewriter/) interface. By assigning a trace writer you can debug what happens inside the Json.NET serializer when serializing and deserializing JSON.

Read more about TraceWriters here:

- [SerializationTracing](SerializationTracing.md.

## Error

The [JsonSerializer.Error](/api/newtonsoft/json/jsonserializer/#event-error) event can catch errors during serialization and either handle the event and continue with serialization or let the error bubble up and be thrown to the application.

Read more about error handling here:

- [SerializationErrorHandling](SerializationErrorHandling.md)

## See Also

- [Serialization Guide](SerializationGuide.md)
- [Serialization Attributes](SerializationAttributes.md)
- [Serializing Dates in JSON](DatesInJSON.md)
- [JsonSerializer](/api/newtonsoft/json/jsonserializer/)
- [JsonSerializerSettings](/api/newtonsoft/json/jsonserializersettings/)
- [JsonConverter](/api/newtonsoft/json/jsonconverter/)
- [SerializationBinder](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.serializationbinder)