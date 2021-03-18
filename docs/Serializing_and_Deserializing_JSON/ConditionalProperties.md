# Conditional Property Serialization

Json.NET has the ability to conditionally serialize properties by placing a ShouldSerialize method on a class. This functionality is similar to the [XmlSerializer ShouldSerialize feature](http://msdn.microsoft.com/en-us/library/53b8022e.aspx).

## ShouldSerialize

To conditionally serialize a property, add a method that returns boolean with the same name as the property and then prefix the method name with ShouldSerialize. The result of the method determines whether the property is serialized. If the method returns true then the property will be serialized, if it returns false then the property will be skipped.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/ConditionalPropertiesTests.cs" region="EmployeeShouldSerializeExample" title="Employee class with a ShouldSerialize method" :::

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/ConditionalPropertiesTests.cs" region="ShouldSerializeClassTest" title="ShouldSerialize output" :::

## IContractResolver

ShouldSerialize can also be set using an [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/). Conditionally serializing a property using an IContractResolver is useful if you don't want to place a ShouldSerialize method on a class or you didn't declare the class and are unable to.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/ConditionalPropertiesTests.cs" region="ShouldSerializeContractResolver" title="Conditional properties with IContractResolver" :::

## See Also

- [JsonSerializer](/api/newtonsoft/json/jsonserializer/)
- [IContractResolver](/api/newtonsoft/json/serialization/icontractresolver/)
- [JsonProperty.ShouldSerialize](/api/newtonsoft/json/serialization/jsonproperty/#property-shouldserialize)