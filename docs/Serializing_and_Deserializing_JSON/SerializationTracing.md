# Debugging with Serialization Tracing

The Json.NET serializer supports logging and debugging using the [ITraceWriter](/api/newtonsoft/json/serialization/itracewriter/) interface. By assigning a trace writer you can capture serialization messages and errors and debug what happens inside the Json.NET serializer when serializing and deserializing JSON.

## ITraceWriter

A trace writer can be assigned using properties on JsonSerializerSettings or JsonSerializer.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/TraceWriterTests.cs" region="MemoryTraceWriterExample" title="Debugging serialization using MemoryTraceWriter" :::

Json.NET has two implementations of ITraceWriter: [MemoryTraceWriter](/api/newtonsoft/json/serialization/memorytracewriter/), which keeps messages in memory for simple debugging, like the example above, and [DiagnosticsTraceWriter](/api/newtonsoft/json/serialization/diagnosticstracewriter/), which writes messages to any System.Diagnostics.TraceListeners your application is using.

## Custom ITraceWriter

To write messages using your existing logging framework, just implement a custom version of ITraceWriter.

:::code source="../../Src/Newtonsoft.Json.Tests/Documentation/TraceWriterTests.cs" region="CustomTraceWriterExample" title="Custom NLog TraceWriter" :::

## See Also

- [JsonSerializer](/api/newtonsoft/json/jsonserializer/)
- [ITraceWriter](/api/newtonsoft/json/serialization/itracewriter/)
- [MemoryTraceWriter](/api/newtonsoft/json/serialization/memorytracewriter/)
- [DiagnosticsTraceWriter](/api/newtonsoft/json/serialization/diagnosticstracewriter/)