# Debugging with Serialization Tracing

The Json.NET serializer supports logging and debugging using the [ITraceWriter](T:Newtonsoft.Json.Serialization.ITraceWriter) interface. By assigning a trace writer you can capture serialization messages and errors and debug what happens inside the Json.NET serializer when serializing and deserializing JSON.

## ITraceWriter

A trace writer can be assigned using properties on JsonSerializerSettings or JsonSerializer.

```csharp Debugging serialization using MemoryTraceWriter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\TraceWriterTests.cs
region: MemoryTraceWriterExample
```

Json.NET has two implementations of ITraceWriter: [MemoryTraceWriter](T:Newtonsoft.Json.Serialization.MemoryTraceWriter), which keeps messages in memory for simple debugging, like the example above, and [DiagnosticsTraceWriter](T:Newtonsoft.Json.Serialization.DiagnosticsTraceWriter), which writes messages to any System.Diagnostics.TraceListeners your application is using.

## Custom ITraceWriter

To write messages using your existing logging framework, just implement a custom version of ITraceWriter.

```csharp Custom NLog TraceWriter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\TraceWriterTests.cs
region: CustomTraceWriterExample
```

## See Also

- [JsonSerializer](T:Newtonsoft.Json.JsonSerializer)
- [ITraceWriter](T:Newtonsoft.Json.Serialization.ITraceWriter)
- [MemoryTraceWriter](T:Newtonsoft.Json.Serialization.MemoryTraceWriter)
- [DiagnosticsTraceWriter](T:Newtonsoft.Json.Serialization.DiagnosticsTraceWriter)