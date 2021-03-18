# Validating JSON with JSON Schema

Json.NET supports the JSON Schema standard via the [JsonSchema](/api/newtonsoft/json/schema/jsonschema/) and [JsonValidatingReader](/api/newtonsoft/json/jsonvalidatingreader/) classes. It sits under the [Schema](N:Newtonsoft.Json.Schema) namespace.

JSON Schema is used to validate the structure and data types of a piece of JSON, similar to XML Schema for XML. You can read more about JSON Schema at [json-schema.org](http://json-schema.org/).

:::caution
**Obsolete.** JSON Schema validation has been moved to its own package. See [https://www.newtonsoft.com/jsonschema](https://www.newtonsoft.com/jsonschema) for more details.
:::

## Validating with JSON Schema

The simplest way to check if JSON is valid is to load the JSON into a JObject or JArray and then use the [IsValid(JToken,JsonSchema)](/api/newtonsoft/json/schema/extensions/#method-isvalid) method with the JSON Schema.

:::code source="../Src/Newtonsoft.Json.Tests/Documentation/JsonSchemaTests.cs" region="IsValidBasic" title="Validate JSON with IsValid" :::

To get validation error messages, use the [IsValid(JToken,JsonSchema,IList{String}@)](/api/newtonsoft/json/schema/extensions/#method-isvalid) or [Validate(JToken,JsonSchema,ValidationEventHandler)](/api/newtonsoft/json/schema/extensions/#method-validate) overloads.

:::code source="../Src/Newtonsoft.Json.Tests/Documentation/JsonSchemaTests.cs" region="IsValidMessages" title="Validate JSON with IsValid" :::

Internally IsValid uses [JsonValidatingReader](/api/newtonsoft/json/jsonvalidatingreader/) to perform the JSON Schema validation. To skip the overhead of loading JSON into a JObject/JArray, validating the JSON, and then deserializing the JSON into a class, JsonValidatingReader can be used with JsonSerializer to validate JSON while the object is being deserialized.

:::code source="../Src/Newtonsoft.Json.Tests/Documentation/JsonSchemaTests.cs" region="JsonValidatingReader" title="Validate JSON with JsonValidatingReader" :::

## Creating JSON Schemas

The simplest way to get a [JsonSchema](/api/newtonsoft/json/schema/jsonschema/) object is to load it from a string or a file.

:::code source="../Src/Newtonsoft.Json.Tests/Documentation/JsonSchemaTests.cs" region="LoadJsonSchema" title="Creating JSON Schemas from strings or files" :::

It is also possible to create JsonSchema objects in code.

:::code source="../Src/Newtonsoft.Json.Tests/Documentation/JsonSchemaTests.cs" region="ManuallyCreateJsonSchema" title="Create new JSON Schemas in code" :::

## See Also

- [JsonSchema](/api/newtonsoft/json/schema/jsonschema/)
- [JsonValidatingReader](/api/newtonsoft/json/jsonvalidatingreader/)