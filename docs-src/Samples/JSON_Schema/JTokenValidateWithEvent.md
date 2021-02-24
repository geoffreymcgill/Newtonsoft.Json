# Validate with validation error events

This sample validates a [JObject](/api/newtonsoft/json/linq/jobject/) using the [IsValid(JToken,JsonSchema)](/api/newtonsoft/json/schema/extensions/#method-isvalid) extension method and raises an event for each validation error.

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Schema/JTokenValidateWithEvent.cs" region="Usage" title="Usage" :::
