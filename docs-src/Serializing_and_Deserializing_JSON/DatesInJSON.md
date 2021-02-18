# Serializing Dates in JSON

DateTimes in JSON are hard.

The problem comes from the [JSON spec](http://www.ietf.org/rfc/rfc4627.txt) itself: there is no literal syntax for dates in JSON. The spec has objects, arrays, strings, integers, and floats, but it defines no standard for what a date looks like.

## Dates and Json.NET

The default format used by Json.NET is the [ISO 8601 standard](http://en.wikipedia.org/wiki/ISO_8601): `"2012-03-19T07:22Z"`.

Prior to Json.NET 4.5 dates were written using the Microsoft format: `"\/Date(1198908717056)\/"`. If you want to use this format, or you want to maintain compatibility with Microsoft JSON serializers or older versions of Json.NET, then change the [DateFormatHandling](/API/newtonsoft/json/dateformathandling/)
setting to MicrosoftDateFormat.

The [DateTimeZoneHandling](/API/newtonsoft/json/datetimezonehandling/) setting can be used to convert a DateTime's [DateTimeKind](T:System.DateTimeKind) when serializing. For example set DateTimeZoneHandling to Utc to serialize all DateTimes as UTC dates. Note that this setting does not effect DateTimeOffsets.

If your dates don't follow the ISO 8601 standard, then the DateFormatString setting can be used to customize the format of date strings that are read and written using .NET's [custom date and time format syntax](https://msdn.microsoft.com/en-us/library/8kb3ddd4.aspx).

## DateTime JsonConverters

With no standard for dates in JSON, the number of possible different formats when interoping with other systems is endless. Fortunately Json.NET has a solution to deal with reading and writing custom dates: JsonConverters. A JsonConverter is used to override how a type is serialized.

```csharp DateTime JsonConverters Example
source: ..\Src\Newtonsoft.Json.Tests\Documentation\SerializationTests.cs
region: SerializingDatesInJson
``` 

Simply pass the JsonConverter you wish to use to the Json.NET serializer.

## JavaScriptDateTimeConverter

The JavaScriptDateTimeConverter class is one of the two DateTime JsonConverters that come with Json.NET. This converter serializes a DateTime as a [JavaScript Date object](http://msdn.microsoft.com/en-us/library/cd9w2te4.aspx): `new Date(1234656000000)`

Technically this is invalid JSON according to the spec, but all browsers and some JSON frameworks, including Json.NET, support it.

## IsoDateTimeConverter

:::
From Json.NET 4.5 and onwards dates are written using the ISO 8601 format by default, and using this converter is unnecessary.
:::

IsoDateTimeConverter serializes a DateTime to an [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) formatted string: `"2009-02-15T00:00:00Z"`

The IsoDateTimeConverter class has a property, DateTimeFormat, to further customize the formatted string.

## See Also

- [DateFormatHandling](/API/newtonsoft/json/dateformathandling/)
- [DateTimeZoneHandling](/API/newtonsoft/json/datetimezonehandling/)
- [JavaScriptDateTimeConverter](/API/newtonsoft/json/converters/javascriptdatetimeconverter/)
- [IsoDateTimeConverter](/API/newtonsoft/json/converters/isodatetimeconverter/)