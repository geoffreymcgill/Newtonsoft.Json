# Serialization Error Handling

Json.NET supports error handling during serialization and deserialization. Error handling lets you catch an error and choose whether to handle it and continue with serialization or let the error bubble up and be thrown in your application.

Error handling is defined through two methods: the [JsonSerializer.Error](E:Newtonsoft.Json.JsonSerializer.Error) event on JsonSerializer and the [OnErrorAttribute](T:Newtonsoft.Json.Serialization.OnErrorAttribute).

## Error Event

The [JsonSerializer.Error](E:Newtonsoft.Json.JsonSerializer.Error) event is an event handler found on [JsonSerializer](T:Newtonsoft.Json.JsonSerializer). The error event is raised whenever an exception is thrown while serializing or deserializing JSON. Like all settings found on JsonSerializer, it can also be set on [JsonSerializerSettings](T:Newtonsoft.Json.JsonSerializerSettings) and passed to the serialization methods on JsonConvert.

```csharp Serialization Error Handling
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationErrorHandling
```

In this example we are deserializing a JSON array to a collection of DateTimes. On the JsonSerializerSettings a handler has been assigned to the `Error` event which will log the error message and mark the error as handled.

The result of deserializing the JSON is three successfully deserialized dates and three error messages: one for the badly formatted string ("I am not a date and will error!"), one for the nested JSON array, and one for the null value since the list doesn't allow nullable DateTimes. The event handler has logged these messages and Json.NET has continued on deserializing the JSON because the errors were marked as handled.

One thing to note with error handling in Json.NET is that an unhandled error will bubble up and raise the event on each of its parents. For example an unhandled error when serializing a collection of objects will be raised twice, once against the object and then again on the collection. This will let you handle an error either where it occurred or on one of its parents.

```csharp Parent Error Handling
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationErrorHandlingWithParent
``` 

If you aren't immediately handling an error and only want to perform an action against it once, then you can check to see whether the [ErrorEventArgs](T:Newtonsoft.Json.Serialization.ErrorEventArgs)'s CurrentObject is equal to the OriginalObject. OriginalObject is the object that threw the error and CurrentObject is the object that the event is being raised against. They will only equal the first time the event is raised against the OriginalObject.

## OnErrorAttribute

The [OnErrorAttribute](T:Newtonsoft.Json.Serialization.OnErrorAttribute) works much like the other [SerializationAttributes](.NET serialization attributes) that Json.NET supports. To use it you simply place the attribute on a method that takes the correct parameters: a StreamingContext and an ErrorContext. The name of the method doesn't matter.

```csharp Serialization Error Handling Attribute
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationErrorHandlingAttributeObject
```

In this example accessing the Roles property will throw an
exception when no roles have been set. The HandleError method will set
the error when serializing Roles as handled and allow Json.NET to
continue serializing the class.

```csharp Serialization Error Handling Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializationErrorHandlingAttributeExample
```

## See Also

- [SerializationAttributes](SerializationAttributes.md)
- [JsonSerializer.Error](E:Newtonsoft.Json.JsonSerializer.Error)
- [OnErrorAttribute](T:Newtonsoft.Json.Serialization.OnErrorAttribute)