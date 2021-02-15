# Validate with validation error messages

This sample validates a [JObject](T:Newtonsoft.Json.Linq.JObject) using the [IsValid(Newtonsoft.Json.Linq.JToken,Newtonsoft.Json.Schema.JsonSchema)](M:Newtonsoft.Json.Schema.Extensions.IsValid(Newtonsoft.Json.Linq.JToken,Newtonsoft.Json.Schema.JsonSchema)) extension method and returns error messages.

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Sample

```csharp Usage
source: ..\Src\Newtonsoft.Json.Tests\Documentation\Samples\Schema\JTokenIsValidWithMessages.cs
region: Usage
```
