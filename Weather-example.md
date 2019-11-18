# Scales - Temperature

When using OM, you should keep in mind that temperature is often expressed as a point on a scale, not as a measure. Generally, if we say that the temperature is 18 °C and we want to convert to Kelvin, we add 273.15 and get 291.15 K, or 64.4 °F. These are all scales; the Celsius scale, the Kelvin scale, and the Fahrenheit scale and they have different origins (zero points). I.e. for temperature scales 0 °C ≠ 0 K ≠ 0 °F.

You can still use measures to express temperatures (where 0 °C = 0 K = 0 °F) but these would specify a temperature difference. For example: 10 °C = 10 K = 18 °F.

## Example

To express, for instance, the temperature at [Alert, Canada](https://en.wikipedia.org/wiki/Alert,_Nunavut) on November 30th, 2016 at 11:28 AM, we have the following triples:

	_:bn1 rdf:type om:Point ;
		   om:hasScale om:CelsiusScale ;
		   om:hasNumericalValue "-24.11"^^xsd:double ; 
		   weather:hasDate "2016-11-30T11:27:59:000+01:00"^^xsd:dateTime .
	_:bn2 om:hasValue _:bn1 .
	_:bn2 rdf:type om:ThermodynamicTemperature .
	_:bn2 om:hasPhenomenon _:bn3 .
	<http://sws.geonames.org/6295922/> weather:hasWeather _:bn3 ;
		   gn:name "Alert" .

where `weather` and `gn` are prefixes for other namespaces (`gn` for the [geonames](http://www.geonames.org) namespace). The reference to `weather:hasDate` in the instance of `Point` is beyond the scope of OM.

Below you can see a diagram of the RDF structure for this example.

![Example: Alert Weather](/images/OM-2.0-Example-Weather.png)

**Figure 1.** An RDF diagram of the weather information at Alert, Canada.
