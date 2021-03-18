# Querying JSON with SelectToken

[SelectToken()](/api/newtonsoft/json/linq/jtoken/#method-selecttoken) provides a method to query LINQ to JSON using a single string path to a desired [JToken](/api/newtonsoft/json/linq/jtoken/). SelectToken makes dynamic queries easy because the entire query is defined in a string.

## SelectToken

SelectToken is a method on JToken and takes a string path to a child token. SelectToken returns the child token or a null reference if a token couldn't be found at the path's location.

The path is made up of property names and array indexes separated by periods, e.g. `Manufacturers[0].Name`.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="SelectTokenComplex" title="SelectToken Example" :::

## SelectToken with JSONPath

SelectToken supports JSONPath queries. Find out more about JSONPath [here](https://goessner.net/articles/JsonPath/).

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/Samples/JsonPath/QueryJsonSelectTokenJsonPath.cs" region="Usage" title="SelectToken With JSONPath" :::

## SelectToken with LINQ

SelectToken can be used in combination with standard LINQ methods.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/LinqToJsonTests.cs" region="SelectTokenLinq" title="SelectToken With LINQ Example" :::

## See Also

- [LINQ to JSON](README.md)
- [SelectToken()](/api/newtonsoft/json/linq/jtoken/#method-selecttoken)
