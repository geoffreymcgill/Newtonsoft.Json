# Validate with validation error events

This sample validates a [JObject](/API/newtonsoft/json/linq/jobject/) using the [IsValid(JToken,JsonSchema)](/API/newtonsoft/json/schema/extensions/#method-isvalid) extension method and raises an event for each validation error.

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Sample

```csharp Usage
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Schema\JTokenValidateWithEvent.cs
region: Usage
```
