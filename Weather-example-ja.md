# 尺度 - 温度

〔訳注: この文書は，[2019年11月5日時点のWeather-example.md](https://github.com/HajoRijgersberg/OM/blob/11097b04a28fef7e0901f24f087b2ba27d6f1c90/Weather-example.md)の，技術的内容を変更しない日本語訳である。〕 

OMを用いる際，温度が屡々<ruby>測度<rp>(</rp><rt>measure</rt><rp>)</rp></ruby>ではなく<ruby>尺度<rp>(</rp><rt>scale</rt><rp>)</rp></ruby>上の位置として表現されることを心得よ。
一般に，温度が摂氏18度であり絶対温度に変更したいならば，273.15を加算して291.15 K（又は華氏64.4度）にする。
今述べた数値は全て摂氏尺度，絶対温度尺度，そして華氏尺度という尺度であって，三者の原点（数値が零になる位置）は異なる。
換言すれば，温度尺度については摂氏0度，絶対温度0度，華氏0度は相異なる。

温度の表現に測度を用いることは依然可能である（この場合0 °C = 0 K = 0 °F）が，しかしそれらが指し示すのは温度差である。具体例: 10 °C = 10 K = 18 °F。

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

ここで`weather`及び`gn`は他の名前空間の接頭辞である（`gn`は[geonames](http://www.geonames.org)名前空間）。`Point`のインスタンスにおける`weather:hasDate`の参照はOMの範疇ではない。

この例に対するRDF図式は次の通り。

![例: アラートの天気](/images/OM-2.0-Example-Weather.png)

**図 1.** カナダ・アラートにおける気温情報のRDF図式
