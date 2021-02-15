# Conditional Property Serialization

Json.NET has the ability to conditionally serialize properties by placing a ShouldSerialize method on a class. This functionality is similar to the [XmlSerializer ShouldSerialize feature](http://msdn.microsoft.com/en-us/library/53b8022e.aspx).

## ShouldSerialize

To conditionally serialize a property, add a method that returns boolean with the same name as the property and then prefix the method name with ShouldSerialize. The result of the method determines whether the property is serialized. If the method returns true then the property will be serialized, if it returns false then the property will be skipped.

```csharp Employee class with a ShouldSerialize method
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConditionalPropertiesTests.cs
region: EmployeeShouldSerializeExample
```

```csharp ShouldSerialize output
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConditionalPropertiesTests.cs
region: ShouldSerializeClassTest
```

## IContractResolver

ShouldSerialize can also be set using an [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver). Conditionally serializing a property using an IContractResolver is useful if you don't want to place a ShouldSerialize method on a class or you didn't declare the class and are unable to.

```csharp Conditional properties with IContractResolver
source: ..\Src\Newtonsoft.Json.Tests\Documentation\ConditionalPropertiesTests.cs
region: ShouldSerializeContractResolver
```

## See Also


- [JsonSerializer](T:Newtonsoft.Json.JsonSerializer)
- [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver)
- [JsonProperty.ShouldSerialize](P:Newtonsoft.Json.Serialization.JsonProperty.ShouldSerialize)