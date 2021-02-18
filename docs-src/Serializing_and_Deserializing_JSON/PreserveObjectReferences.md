# Preserving Object References

By default Json.NET will serialize all objects it encounters by value. If a list contains two Person references and both references point to the same object, then the JsonSerializer will write out all the names and values for each reference.

```csharp Preserve Object References Off
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: PreservingObjectReferencesOff
```

In most cases this is the desired result, but in certain scenarios writing the second item in the list as a reference to the first is a better solution. If the above JSON was deserialized now, then the returned list would contain two completely separate Person objects with the same values. Writing references by value will also cause problems on objects where a circular reference occurs.

## PreserveReferencesHandling

Setting [PreserveReferencesHandling](/api/newtonsoft/json/preservereferenceshandling/) will track object references when serializing and deserializing JSON.

```csharp Preserve Object References On
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: PreservingObjectReferencesOn
``` 

The first Person in the list is serialized with the addition of an object ID. The second Person in JSON is now only a reference to the first.

With PreserveReferencesHandling on, now only one Person object is created on deserialization and the list contains two references to it, mirroring what we started with.

Metadata properties like `$id` must be located at the beginning of a JSON object to be successfully detected during deserialization. If you can't control the order of properties in your JSON object then [MetadataPropertyHandling](/api/newtonsoft/json/metadatapropertyhandling/) can be used to remove this restriction.

:::
References cannot be preserved when a value is set via a non-default constructor. With a non-default constructor, child values must be created before the parent value so they can be passed into the constructor, making tracking reference impossible. [ISerializable](T:System.Runtime.Serialization.ISerializable) types are an example of a class whose values are populated with a non-default constructor and won't work with PreserveReferencesHandling.
:::

## IsReference

The PreserveReferencesHandling setting on the JsonSerializer will change how all objects are serialized and deserialized. For fine grain control over which objects and members should be serialized as a reference there is the IsReference property on the JsonObjectAttribute, JsonArrayAttribute and JsonPropertyAttribute.

Setting IsReference on JsonObjectAttribute or JsonArrayAttribute to true will mean the JsonSerializer will always serialize the type the attribute is against as a reference. Setting IsReference on the JsonPropertyAttribute to true will serialize only that property as a reference.

```csharp IsReference
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: PreservingObjectReferencesAttribute
```

## IReferenceResolver

To customize how references are generated and resolved the [IReferenceResolver](/api/newtonsoft/json/serialization/ireferenceresolver/) interface is available to inherit from and use with the JsonSerializer.

## See Also

- [PreserveReferencesHandling](/api/newtonsoft/json/preservereferenceshandling/)