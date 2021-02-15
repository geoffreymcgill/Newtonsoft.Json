# Validating JSON with JSON Schema

Json.NET supports the JSON Schema standard via the [JsonSchema](T:Newtonsoft.Json.Schema.JsonSchema) and [JsonValidatingReader](T:Newtonsoft.Json.JsonValidatingReader) classes. It sits under the [Schema](N:Newtonsoft.Json.Schema) namespace.

JSON Schema is used to validate the structure and data types of a piece of JSON, similar to XML Schema for XML. You can read more about JSON Schema at [json-schema.org](http://json-schema.org/).

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Validating with JSON Schema

The simplest way to check if JSON is valid is to load the JSON into a JObject or JArray and then use the [IsValid(JToken,JsonSchema)](M:Newtonsoft.Json.Schema.Extensions.IsValid(Newtonsoft.Json.Linq.JToken,Newtonsoft.Json.Schema.JsonSchema)) method with the JSON Schema.

```csharp Validate JSON with IsValid
source: ..\Src\Newtonsoft.Json.Tests\Documentation\JsonSchemaTests.cs
region: IsValidBasic
```

To get validation error messages, use the [IsValid(JToken,JsonSchema,IList{String}@)](M:Newtonsoft.Json.Schema.Extensions.IsValid(Newtonsoft.Json.Linq.JToken,Newtonsoft.Json.Schema.JsonSchema,System.Collections.Generic.IList{System.String}@)) or [Validate(JToken,JsonSchema,ValidationEventHandler)](M:Newtonsoft.Json.Schema.Extensions.Validate(Newtonsoft.Json.Linq.JToken,Newtonsoft.Json.Schema.JsonSchema,Newtonsoft.Json.Schema.ValidationEventHandler)) overloads.

```csharp Validate JSON with IsValid
source: ..\Src\Newtonsoft.Json.Tests\Documentation\JsonSchemaTests.cs
region: IsValidMessages
```

Internally IsValid uses [JsonValidatingReader](T:Newtonsoft.Json.JsonValidatingReader) to perform the JSON Schema validation. To skip the overhead of loading JSON into a JObject/JArray, validating the JSON, and then deserializing the JSON into a class, JsonValidatingReader can be used with JsonSerializer to validate JSON while the object is being deserialized.

```csharp Validate JSON with JsonValidatingReader
source: ..\Src\Newtonsoft.Json.Tests\Documentation\JsonSchemaTests.cs
region: JsonValidatingReader
```

## Creating JSON Schemas

The simplest way to get a [JsonSchema](T:Newtonsoft.Json.Schema.JsonSchema) object is to load it from a string or a file.

```csharp Creating JSON Schemas from strings or files
source: ..\Src\Newtonsoft.Json.Tests\Documentation\JsonSchemaTests.cs
region: LoadJsonSchema
```

It is also possible to create JsonSchema objects in code.

```csharp Create new JSON Schemas in code
source: ..\Src\Newtonsoft.Json.Tests\Documentation\JsonSchemaTests.cs
region: ManuallyCreateJsonSchema
```

## See Also

- [JsonSchema](T:Newtonsoft.Json.Schema.JsonSchema)
- [JsonValidatingReader](T:Newtonsoft.Json.JsonValidatingReader)