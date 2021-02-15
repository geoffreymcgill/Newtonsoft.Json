# Validate with validation error events

This sample validates a [JObject](T:Newtonsoft.Json.Linq.JObject) using the [IsValid(JToken,JsonSchema)](M:Newtonsoft.Json.Schema.Extensions.IsValid(Newtonsoft.Json.Linq.JToken,Newtonsoft.Json.Schema.JsonSchema)) extension method and raises an event for each validation error.

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Sample

```csharp Usage
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Schema\JTokenValidateWithEvent.cs
region: Usage
```
