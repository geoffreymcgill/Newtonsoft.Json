# Validate with validation error messages

This sample validates a [JObject](/api/newtonsoft/json/linq/jobject/) using the [IsValid(JToken,JsonSchema)](/api/newtonsoft/json/schema/extensions/#method-isvalid) extension method and returns error messages.

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Schema/JTokenIsValidWithMessages.cs" region="Usage" title="Usage" :::
