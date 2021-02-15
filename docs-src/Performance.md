# Performance Tips

Out of the box Json.NET is faster than DataContractJsonSerializer and JavaScriptSerializer. Here are some tips to make it go even faster.

## Reuse Contract Resolver

The [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver) resolves .NET types to contracts that are used during serialization inside JsonSerializer. Creating a contract involves inspecting a type with slow reflection, so contracts are typically cached by implementations of IContractResolver like [DefaultContractResolver](T:Newtonsoft.Json.Serialization.DefaultContractResolver).

To avoid the overhead of recreating contracts every time you use JsonSerializer you should create the contract resolver once and reuse it. Note that if you are not using a contract resolver then a shared internal instance is automatically used when serializing and deserializing.

```csharp Reuse ContractResolver
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: ReuseContractResolver
```

## Optimize Memory Usage

To keep an application consistently fast, it is important to minimize the amount of time the .NET framework spends performing [garbage collection](http://msdn.microsoft.com/en-us/library/ms973837.aspx). Allocating too many objects or allocating very large objects can slow down or even halt an application while garbage collection is in progress.

To minimize memory usage and the number of objects allocated, Json.NET supports serializing and deserializing directly to a stream. Reading or writing JSON a piece at a time, instead of having the entire JSON string loaded into memory, is especially important when working with JSON documents greater than 85kb in size to avoid the JSON string ending up in the [large object heap](http://msdn.microsoft.com/en-us/magazine/cc534993.aspx).

```csharp Deserialize String
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: DeserializeString
```

```csharp Deserialize Stream
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: DeserializeStream
```

## JsonConverters

Passing a [JsonConverter](T:Newtonsoft.Json.JsonConverter) to SerializeObject or DeserializeObject provides a simple way to completely change how an object is serialized. There is, however, a small amount of overhead; the CanConvert method is called for every value to check whether serialization should be handled by that JsonConverter.

There are a couple of ways to continue to use JsonConverters without any overhead. The simplest way is to specify the JsonConverter using the [JsonConverterAttribute](T:Newtonsoft.Json.JsonConverterAttribute). This attribute tells the serializer to always use that converter when serializing and deserializing the type, without the check.

```csharp Use JsonConverter with JsonConverterAttribute
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: JsonConverterAttribute
```

If the class you want to convert isn't your own and you're unable to use an attribute, a JsonConverter can still be used by creating your own [IContractResolver](T:Newtonsoft.Json.Serialization.IContractResolver).

```csharp Use JsonConverter with IContractResolver
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: JsonConverterContractResolver
```

The IContractResolver in the example above will set all DateTimes to use the JavaScriptDateConverter.

## Manually Serialize

The absolute fastest way to read and write JSON is to use JsonTextReader/JsonTextWriter directly to manually serialize types. Using a reader or writer directly skips any of the overhead from a serializer, such as reflection.

```csharp Manually serialize using JsonTextWriter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\PerformanceTests.cs
region: ReaderWriter
```

If performance is important and you don't mind writing more code to get it, then this is your best choice. You can read more about using JsonReader/JsonWriter here:

- [ReadingWritingJSON](ReadingWritingJSON.md)

## Benchmarks

![Json.NET Performance](performance.png)

## See Also

- [JsonSerializer](T:Newtonsoft.Json.JsonSerializer)
- [JsonConverter](T:Newtonsoft.Json.JsonConverter)
- [JsonConverterAttribute](T:Newtonsoft.Json.JsonConverterAttribute)
- [JsonTextWriter](T:Newtonsoft.Json.JsonTextWriter)
- [JsonTextReader](T:Newtonsoft.Json.JsonTextReader)