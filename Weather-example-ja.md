# 尺度 - 温度

〔訳注: この文書は，[2019年9月6日時点の](https://github.com/HajoRijgersberg/OM/blob/11097b04a28fef7e0901f24f087b2ba27d6f1c90/Weather-example.md)文書の，技術的内容を変更しない日本語訳である。〕 


When using OM, you should keep in mind that temperature is often expressed as a point on a scale, not as a measure. Generally, if we say that the temperature is 18 °C and we want to convert to Kelvin, we add 273.15 and get 291.15 K, or 64.4 °F. These are all scales; the Celsius scale, the Kelvin scale, and the Fahrenheit scale and they have different origins (zero points). I.e. for temperature scales 0 °C ≠ 0 K ≠ 0 °F.
OMを用いる際，温度が屡々測定値ではなく尺度として表現されることを心得よ。

You can still use measures to express temperatures (where 0 °C = 0 K = 0 °F) but these would specify a temperature difference. For example: 10 °C = 10 K = 18 °F.

## 例

説明の為，例えとして，2016年11月30日午前11時28分時点の[カナダ・アラート](https://ja.wikipedia.org/?curid=1642577)での気温は次のトリプルで記述される:

```turtle
_:bn1 rdf:type om:Point ;
	   om:hasScale om:CelsiusScale ;
	   om:hasNumericalValue "-24.11"^^xsd:double ;
	   weather:hasDate "2016-11-30T11:27:59:000+01:00"^^xsd:dateTime .
_:bn2 om:hasValue _:bn1 .
_:bn2 rdf:type om:ThermodynamicTemperature .
_:bn2 om:hasPhenomenon _:bn3 .
<http://sws.geonames.org/6295922/> weather:hasWeather _:bn3 ;
	   gn:name "Alert" ;
	   gn:alternateName "アラート"@ja .
```
〔訳註: `gn:alternateName "アラート"@ja`は原文には存在しない〕

where `weather` and `gn` are prefixes for other namespaces (`gn` for the [geonames](http://www.geonames.org) namespace). The reference to `weather:hasDate` in the instance of `Point` is beyond the scope of OM.
ここで`weather`及び`gn`は他の名前空間の接頭辞である（`gn`は[geonames](http://www.geonames.org)名前空間）。`Point`のインスタンスにおける`weather:hasDate`の参照はOMの範疇ではない。

この例に対するRDF図式は次の通り。

![例: アラートの天気](/images/OM-2.0-Example-Weather.png)

**図 1.** カナダ・アラートにおける気温情報のRDF図式
