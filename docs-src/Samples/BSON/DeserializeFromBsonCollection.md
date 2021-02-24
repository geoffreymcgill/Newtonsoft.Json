# Deserialize a Collection from BSON

This sample sets [BsonReader.ReadRootValueAsArray](/api/newtonsoft/json/bson/bsonreader/#property-readrootvalueasarray) to `true` so the root BSON value is correctly read as an array instead of an object and deserializes BSON to a collection.

## Sample

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Bson/DeserializeFromBsonCollection.cs" region="Types" title="Types" :::

:::code source="../../../Src/Newtonsoft.Json.Tests/Documentation/Samples/Bson/DeserializeFromBsonCollection.cs" region="Usage" title="Usage" :::