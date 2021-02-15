# Json.NET vs .NET Serializers

Json.NET offers many features not found in the JavaScriptSerializer and DataContractSerializer that come with .NET.

## Feature Comparison

&nbsp; | Json.NET | DataContractJsonSerializer | JavaScriptSerializer
--- | --- | --- | --- |
Supports JSON | :white_check_mark: | :white_check_mark: | :white_check_mark:
Supports BSON | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports JSONPath | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports .NET 2.0 | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports .NET 3.5 | :white_check_mark: | :white_check_mark: | :white_check_mark:
Supports .NET 4.0 | :white_check_mark: | :white_check_mark: | :white_check_mark:
Supports .NET 4.5 | :white_check_mark: | :white_check_mark: | :white_check_mark:
Supports Silverlight | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Supports Windows Phone | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Supports Windows Store | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Supports Xamarin | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Open Source | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
MIT License | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
LINQ to JSON | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Thread Safe | :white_check_mark: | :white_check_mark: | :white_check_mark:
XPath-like JSON query syntax | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Indented JSON support | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
[Efficient dictionary serialization](http://stackoverflow.com/questions/1207731/how-can-i-deserialize-json-to-a-simple-dictionarystring-string-in-asp-net) | :white_check_mark: | :no_entry_sign: | :white_check_mark:
[Nonsensical dictionary serialization](http://stackoverflow.com/questions/4559991/any-way-to-make-datacontractjsonserializer-serialize-dictionaries-properly) | :no_entry_sign: | :white_check_mark: | :no_entry_sign:
Deserializes IList, IEnumerable, ICollection, IDictionary properties | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes circular references | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports serializing objects by reference | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Deserializes polymorphic properties and collections | :white_check_mark: | :white_check_mark: | :white_check_mark:
Serializes and deserializes multidimensional arrays | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports including type names with JSON | :white_check_mark: | :white_check_mark: | :white_check_mark:
Globally customize serialization process | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Supports excluding null values when serializing | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports SerializationBinder | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Conditional property serialization | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Includes line number information in errors | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Converts XML to JSON and JSON to XML | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
JSON Schema validation | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
JSON Schema generation from .NET types | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Camel case JSON property names | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Non-default constructors support | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serialization error handling | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports populating an existing object | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Efficiently serializes byte arrays as base64 text | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Handles NaN, Infinity, -Infinity and undefined | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Handles JavaScript constructors | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes .NET 4.0 dynamic objects | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes ISerializable objects | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports serializing enums to their text name | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
JSON recursion limit support | :white_check_mark: | :white_check_mark: | :white_check_mark:
Attribute property name customization | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Attribute property order customization | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Attribute property required customization | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Supports ISO8601 dates | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports JavaScript constructor dates | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports Microsoft AJAX dates | :white_check_mark: | :white_check_mark: | :white_check_mark:
Unquoted property names support | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Raw JSON support | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports reading and writing comments | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes anonymous types | :white_check_mark: | :no_entry_sign: | :white_check_mark:
Deserializes anonymous types | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Opt-in mode serialization | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Opt-out mode serialization | :white_check_mark: | :no_entry_sign: | :white_check_mark:
Field (Serializable) mode serialization | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Efficiently stream reading and writing JSON | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Single or double quote JSON content | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports overriding a type's serialization | :white_check_mark: | :no_entry_sign: | :white_check_mark:
Supports OnDeserialized, OnSerializing, OnSerialized and OnDeserializing attributes | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Supports serializing private properties | :white_check_mark: | :white_check_mark: | :no_entry_sign:
DataMember attribute support | :white_check_mark: | :white_check_mark: | :no_entry_sign:
MetdataType attribute support | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
DefaultValue attribute support | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes DataSets and DataTables | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes Entity Framework | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes nHibernate | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Case-insensitive property deserialization | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Diagnostic tracing | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Serializes read-only and immutable collections | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports serialization extension data | :white_check_mark: | :white_check_mark: | :no_entry_sign:
Serializes F# discriminated unions | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Serializes F# collections | :white_check_mark: | :no_entry_sign: | :no_entry_sign:
Supports merging JSON | :white_check_mark: | :no_entry_sign: | :no_entry_sign:

## Benchmarks

![Json.NET Performance](performance.png)