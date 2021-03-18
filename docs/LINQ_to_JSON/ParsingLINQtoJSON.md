# Parsing JSON

LINQ to JSON has methods available for parsing JSON from a string or loading JSON directly from a file.

## Parsing JSON text

JSON values can be read from a string using [Parse(string)](/api/newtonsoft/json/linq/jtoken/#method-parse).

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonCreateParse" title="Parsing a JSON Object from text" :::

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonCreateParseArray" title="Parsing a JSON Array from text" :::

## Loading JSON from a file

JSON can also be loaded directly from a file using [ReadFrom(JsonReader)](/api/newtonsoft/json/linq/jtoken/#method-readfrom).

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="LinqToJsonReadObject" title="Reading JSON from a file" :::

## See Also

- [LINQ to JSON](README.md)
- [Parse(string)](/api/newtonsoft/json/linq/jtoken/#method-parse)
- [ReadFrom(JsonReader)](/api/newtonsoft/json/linq/jtoken/#method-readfrom)