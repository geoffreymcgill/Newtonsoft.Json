# Debugging with Serialization Tracing

The Json.NET serializer supports logging and debugging using the [ITraceWriter](/API/newtonsoft/json/serialization/itracewriter/) interface. By assigning a trace writer you can capture serialization messages and errors and debug what happens inside the Json.NET serializer when serializing and deserializing JSON.

## ITraceWriter

A trace writer can be assigned using properties on JsonSerializerSettings or JsonSerializer.

```csharp Debugging serialization using MemoryTraceWriter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\TraceWriterTests.cs
region: MemoryTraceWriterExample
```

Json.NET has two implementations of ITraceWriter: [MemoryTraceWriter](/API/newtonsoft/json/serialization/memorytracewriter/), which keeps messages in memory for simple debugging, like the example above, and [DiagnosticsTraceWriter](/API/newtonsoft/json/serialization/diagnosticstracewriter/), which writes messages to any System.Diagnostics.TraceListeners your application is using.

## Custom ITraceWriter

To write messages using your existing logging framework, just implement a custom version of ITraceWriter.

```csharp Custom NLog TraceWriter
source: ..\Src\Newtonsoft.Json.Tests\Documentation\TraceWriterTests.cs
region: CustomTraceWriterExample
```

## See Also

- [JsonSerializer](/API/newtonsoft/json/jsonserializer/)
- [ITraceWriter](/API/newtonsoft/json/serialization/itracewriter/)
- [MemoryTraceWriter](/API/newtonsoft/json/serialization/memorytracewriter/)
- [DiagnosticsTraceWriter](/API/newtonsoft/json/serialization/diagnosticstracewriter/)