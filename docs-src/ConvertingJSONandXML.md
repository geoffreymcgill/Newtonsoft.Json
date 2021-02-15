# Converting between JSON and XML

Json.NET supports converting JSON to XML and vice versa using the [XmlNodeConverter](T:Newtonsoft.Json.Converters.XmlNodeConverter).

Elements, attributes, text, comments, character data, processing instructions, namespaces, and the XML declaration are all preserved when converting between the two. The only caveat is that it is possible to lose the order of differently named nodes at the same level when they are grouped together into an array.

## Conversion Rules

- Elements remain unchanged.
- Attributes are prefixed with an @ and should be at the start of the object.
- Single child text nodes are a value directly against an element, otherwise they are accessed via #text.
- The XML declaration and processing instructions are prefixed with ?.
- Character data, comments, whitespace and significant whitespace nodes are accessed via #cdata-section, #comment, #whitespace and #significant-whitespace respectively.
- Multiple nodes with the same name at the same level are grouped together into an array.
- Empty elements are null.

If the XML created from JSON doesn't match what you want, then you will need to convert it manually.

The best approach to do this is to load your JSON into a LINQ to JSON object like JObject or JArray and then use LINQ to create an XDocument. The opposite process, using LINQ with an XDocument to create a JObject or JArray, also works. You can find out more about using LINQ to JSON with LINQ [QueryingLINQtoJSON](here).

:::
The version of Json.NET being used in your application will change what XML conversion methods are available. SerializeXmlNode/DeserializeXmlNode are available when the framework supports XmlDocument; SerializeXNode/DeserializeXNode are available when the framework supports XDocument.
:::

## SerializeXmlNode

The JsonConvert has two helper methods for converting between JSON and XML. The first is [SerializeXmlNode](Overload:Newtonsoft.Json.JsonConvert.SerializeXmlNode).

This method takes an XmlNode and serializes it to JSON text.

```csharp Converting XML to JSON with SerializeXmlNode
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConvertingJsonAndXmlTests.cs
region: SerializeXmlNode
```

Because multiple nodes with the same name at the same level are grouped together into an array, the conversion process can produce different JSON depending on the number of nodes. For example, if some XML for a user has a single `<Role>` node, then that role will be text against a JSON `"Role"` property, but if the user has multiple `<Role>` nodes, then the role values will be placed in a JSON array.

To fix this situation a custom XML attribute can be added to force a JSON array to be created.

```csharp Attribute to Force a JSON Array
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConvertingJsonAndXmlTests.cs
region: ForceJsonArray
```

## DeserializeXmlNode

The second helper method on JsonConvert is [DeserializeXmlNode](Overload:Newtonsoft.Json.JsonConvert.DeserializeXmlNode). This method takes JSON text and deserializes it into an XmlNode.

Because valid XML must have one root element, the JSON passed to DeserializeXmlNode should have one property in the root JSON object. If the root JSON object has multiple properties, then the overload that also takes an element name should be used. A root element with that name will be inserted into the deserialized XmlNode.

```csharp Converting JSON to XML with DeserializeXmlNode
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConvertingJsonAndXmlTests.cs
region: DeserializeXmlNode
```

## See Also

- [XmlNodeConverter](T:Newtonsoft.Json.Converters.XmlNodeConverter)
- [JsonConvert](T:Newtonsoft.Json.JsonConvert)