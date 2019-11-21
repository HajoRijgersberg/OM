# OM - 測定単位のオントロジー

〔訳注: この文書は，[2019年11月5日時点のREADME](https://github.com/HajoRijgersberg/OM/blob/11097b04a28fef7e0901f24f087b2ba27d6f1c90/README.md)の，技術的内容を変更しない日本語訳である。〕


**測定単位のオントロジー (Ontology of units of Measure; OM) 2.0**は，科学技術にとって重要な概念及び関係をモデル化する。OMは，単位・量・測定・次元に特に焦点を当てている。
OMは[OWL 2 - ウェブ・オントロジー言語](https://www.w3.org/TR/owl2-overview/)に基づいている。

**基底URI:** `http://www.ontology-of-units-of-measure.org/resource/om-2/`

**名前空間接頭辞:** `om`


#### 概要

* [測定単位のオントロジー](#om)
* [記録表オントロジー](#recordtable)
* [ライブラリ](#software)
* [旧版](#previous-versions)
* [謝辞](#acknowledgements)
* [OMについての文献](#papers)
* [OMの使用に言及している資料](#uses-of-om)
* [OMに概して言及している資料](#references-to-om)


### <a name="om"></a>測定単位のオントロジー

OMオントロジーは，測定値及び単位の定義・利用の為の種々の概念を表す，クラス・インスタンス・及びプロパティを提供する。OMは，例えば国際単位系のメートル (`om:metre`) やキログラム (`om:kilogram`) といった一般的な単位だけではなく，マイル (`om:mile`) や〔国際〕海里 (`om:nauticalMile-International`) といった他の単位から派生した単位をも提供する。多くの応用分野に対しては，ハッブル常数の単位であるキロメートル毎秒毎パーセク(km/s/Mpc) (`om:kilometrePerSecond-TimePerMegaparsec`) や花瓶に生けられた花の寿命 (`om:VaseLife`) といったより具体的な単位と量が提供されている。

OMは次の*応用分野*に対応している:

* 幾何学
* 力学
* 熱力学
* 電磁気学
* 流体力学
* 化学物理学
* 測光
* 放射測定及び放射線生物学
* 核物理学
* 天文学及び天体物理学
* 宇宙論
* 地球科学
* 気象学
* 材料科学
* 微生物学
* 経済学
* 情報技術
* 活版印刷
* 運送
* 食品工学
* 収穫後技術
* 味感・食感の力学
* 包装(梱包)

![OMのUML図](images/OM2.0-UML-diagram.png)

**図1.** OMのクラス構造を表わすUML図

例えば，林檎の径を表わすのは次のトリプルの如くなる。

```turtle
ex:_10Centimetres rdf:type om:Measure ;
  om:hasNumericalValue "10"^^xsd:double ;
  om:hasUnit om:centimeter .
ex:diameterOfApple1 om:hasValue ex:_10Centimetres ;
  a om:Diameter ;
  om:hasPhenomenon ex:apple1 .
ex:apple1 rfd:type ex:Apple .
```

ここで`ex`は他の名前空間の接頭辞である。

この例に対するRDF図式は次の通り。

![例: 林檎の大きさ](images/OMAppleExample.png)

**図 2.** 林檎の大きさが10cmであることを示すRDF図式。

次のことに注意せよ。

> OMでは，温度などの尺度は，対応する単位とは異なる方法で処理される。例えば，温度差は°CやKなどの単位を使用した目盛として表される（28 °C = 28 Kである）。一方で，28 °Cの絶対的温度は**摂氏目盛**と呼ばれ，301 Kと等しい。通常，〔絶対的量は使われず〕尺度が用いられる。[温度尺度を用いる例はこちら。](Weather-example-ja.md)
 
OMは，NIST発行の[国際単位系の使用の手引き](http://physics.nist.gov/cuu/pdf/sp811.pdf)といった幾つかの公文書標準に根差している。  
〔訳注: 日本語訳においては，加えて[JIS Z 8000](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=Z8000)「量及び単位」系列の一連の規格を，主に訳語の参考に用いた。〕

### <a name="recordtable"></a>記録表オントロジー

OMリポジトリは，既存のRDFデータ・キューブ標準の補足として，表形式データを意味的にモデル化する為の[RecordTable](https://github.com/HajoRijgersberg/OM/blob/master/record_table.ttl)語彙を収録している。
RDF記録表は，自己記述的言及を含む記録の入れ子構造を持ち，又不規則な・欠落した・及び予期しないデータに対処できる。
こうして，RDFデータ・キューブの制限を回避し，科学及び工学で生じるような複雑なデータを模型化できる。

例として，次掲の表1及び図3を考慮せよ。

![記録表の例: 表](images/TableExample.jpg)

**表1.** 例表であり，一部は図3にてRecordTableとして描かれている。グラフで描かれている升目を強調した。

![記録表の一例](images/RecordTable-Graph.png)

**図3.** RecordTableの使用例を示すRDF図式


### <a name="software"></a>ライブラリ

次に，OMの使用を補助する幾つかのライブラリを挙げる。

* [`om-java-libs`](https://github.com/dieudonne-willems/om-java-libs): 単位間変換にOMを利用するJava製ソフトウェアライブラリ。


### <a name="previous-versions"></a>旧版

旧版はwurvocプラットフォームで配布されている。

* OM 1.8: [http://www.wurvoc.org/vocabularies/om-1.8/](http://www.wurvoc.org/vocabularies/om-1.8/)


### <a name="acknowledgements"></a>謝辞

シラー大学〔訳注: ドイツの公立大学〕のJan Martin Keil氏及びSirko Schindler氏にあたっては，OMの査読をして頂いた（[Unit Ontology Review](https://github.com/fusion-jena/unit-ontology-review)及びその[文献](http://www.semantic-web-journal.net/system/files/swj1825.pdf)参照）。


### <a name="papers"></a>OMについての文献

1. H. Rijgersberg, M.L.I. Wigham, J.L. Top, “How semantics can improve engineering processes. A case of units of measure and quantities.” *Advanced Engineering Informatics*, **25**, 2, 2011, pp. 276-287.
2. H. Rijgersberg, M.F.J. van Assem, J.L. Top, “Ontology of Units of Measure and Related Concepts.” *Semantic Web*, **4**, 1, 2013, pp. 3-13.
3. Top, J., Wigham, M., Rijgersberg, H. “Semantically Enriched Spreadsheet Tables in Science and Engineering.” *SEMAPRO 2014*.
4. Mari Wigham, Hajo Rijgersberg, Martine de Vos, Jan Top. “Semantic Support for Tables using RDF Record Table.” *International Journal On Advances in Intelligent Systems*, **8** (1 and 2), 2015, 128-144.
5. Jan Martin Keil, Sirko Schindler, “Comparison and Evaluation of Ontologies for Units of Measurement.” *Semantic Web*, **1**, 2018, pp. 1-19.
6. Hajo Rijgersberg, Semantic support for quantitative research, PhD thesis, Vrije Universiteit Amsterdam, 2013.
7. Do C., Pauwels E.J. (2013) Using MathML to Represent Units of Measurement for Improved Ontology Alignment. In: Carette J., Aspinall D., Lange C., Sojka P., Windsteiger W. (eds) Intelligent Computer Mathematics. CICM 2013. Lecture Notes in Computer Science, vol 7961. Springer, Berlin, Heidelberg.
8. Markus D. Steinberg, Sirko Schindler, Jan Martin Keil, Use Cases and Suitability Metrics for Unit Ontologies.


### <a name="uses-of-om"></a>OMの使用に言及している資料（網羅せず，目下作成中）

1. D.J.M. Willems, H. Rijgersberg, J.L. Top, “Identifying and extracting quantitative data in annotated text”, *Proceedings of the Workshop on Semantic Web and Information Extraction (SWAIE 2012)*, Galway, Ireland, 2012, pp. 43-54.
2. Martine de Vos, Jan Wielemaker, Hajo Rijgersberg, Guus Schreiber, Bob Wielinga, Jan Top. Combining Information on Structure and Content to Automatically Annotate Scientific Spreadsheet Tables. *Int. J. Human-Computer Studies*, 103, 2017, pp. 63-76.
3. Bonsai, “BONSAI – Big Open Network for Sustainability Assessment Information.” 2019, https://bonsai.uno/.
4. Thorben Iggena, Daniel Kümper, Ralf Tönjes, Martin Strohbach, Pavel Smirnov, Juan A. Martinez, Sahr Thomas Acton, Roonak Rezvani, Josiane Parreira, “IoTCrawler. D4.1 IoT Data Attributes and Quality of Information.” University of Applied Sciences Osnabrück, 2019, https://iotcrawler.eu/wp-content/uploads/2019/07/D4.1_final.pdf.
5. Gkotse B., Jouvelot P., Ravotti F. (2019) IEDM: An Ontology for Irradiation Experiments Data Management. In: Hitzler P. et al. (eds) The Semantic Web: ESWC 2019 Satellite Events. ESWC 2019. Lecture Notes in Computer Science, **11762**, Springer, Cham, 2019.
6. Berrahou, S., Buche, P., Dibie-Barthelemy, J. , Roche, M., How to Extract Unit of Measure in Scientific Documents? In Proceedings of the International Conference on Knowledge Discovery and Information Retrieval and the International Conference on Knowledge Management and Information Sharing (SSTM-2013), 2013, pp. 249-256.
7. Mark S. Fox, A Foundation Ontology for Global City Indicators, University of Toronto, 2015.
8. Megan Katsumi, The Ontology of Units of Measure, https://enterpriseintegrationlab.github.io/icity/OM/doc/index-en.html.
9. Do C., Pauwels E.J. (2013) Harnessing Mathematics for Improved Ontology Alignment. In: Augusto J.C., Wichert R., Collier R., Keyson D., Salah A.A., Tan AH. (eds) Ambient Intelligence. AmI 2013. Lecture Notes in Computer Science, vol 8309. Springer, Cham.
10. Stocker M. et al. (2013) Acquisition and Representation of Knowledge for Atmospheric New Particle Formation. In: Hřebíček J., Schimak G., Kubásek M., Rizzoli A.E. (eds) Environmental Software Systems. Fostering Information Sharing. ISESS 2013. IFIP Advances in Information and Communication Technology, vol 413. Springer, Berlin, Heidelberg.
11. Soroush Samadian, Constructing and applying semantic models of clinical phenotypes to support web-embedded clinical research, PhD thesis, University of British Columbia, 2013.
12. Aurélie Thébaut, Thibault Scholash, Brigitte Charnomordic, Nadine Hilgert, Combining a sensor software with statistical analysis for modeling vine water deficit impact on grape quality, 2014.
13. Valueflows, A vocabulary for the distributed economic networks of the next economy, https://valueflo.ws/.
14. Valentina Tamma, Mauro Dragoni, Rafael Gonçalves, Agnieszka Ławrynowicz (Eds.), Ontology Engineering: 12th International Experiences and Directions Workshop on OWL, OWLED 2015, co-located with ISWC 2015, Bethlehem, PA, USA, 2015.
15. Soroush Samadian, Bruce McManus, Mark Wilkinson, Automatic detection and resolution of measurement-unit conflicts in aggregated data, BMC Med Genomics, 7 (Suppl 1), 2014. 
16. Biodiversity Information Standards TDWG, https://terms.tdwg.org/wiki/Main_Page.
17. Maxime Lefrançois, Assisting the Semanticization of data with Vocabularies, Languages, and Tools.
18. Filip Radulovic, Raúl García-Castro, The Evaluation Result Ontology, 2015, http://vocab.linkeddata.es/eval/index.html.
19. Megan Katsumi, Mark Fox, iCity Ontology Initial Release, University of Toronto, 2017.
20. Paola Espinoza-Arias, María Poveda-Villalón, Raúl García-Castro, Oscar Corcho, Ontological Representation of Smart City Data: From Devices to Cities, Appl. Sci. 9, 32, 2019.


### <a name="references-to-om"></a>OMに概して言及している資料（網羅せず，目下作成中）

1. Loli Burgueño, Tanja Mayerhofer, Manuel Wimmer, Antonio Vallecillo, “Specifying quantities in software models.” *Information and Software Technology*, **113**, 2019, pp. 82-97.
2. Lavdim Halilaj, An Approach for Collaborative Ontology Development in Distributed and Heterogeneous Environments, PhD thesis, University of Bonn, 2019.
3. Fredrik Heintz, Daniel de Leng, Semantic Information Integration with Transformations for Stream Reasoning.
4. Georgios V. Gkoutos, Paul N. Schofield, Robert Hoehndorf, “The Units Ontology: a tool for integrating units of measurement in science”, Database, 2012.
5. Gianluca Quercini, Chantal Reynaud, Entity Discovery and Annotation in Tables, EDBT/ICDT ’13, Genoa, Italy, 2013.
6. Isabel F. Cruz, Venkat R. Ganesh, Seyed Iman Mirrezaei, Semantic extraction of geographic data from web tables for big data integration, Proceedings of the 7th Workshop on Geographic Information Retrieval, Orlando, Florida, 2013, pp. 19-26.
7. Damion M. Dooley, William W.L Hsiao, Emma Griffiths, “An OBI ontology Datum Proof Sheet. Toward a harmonized treatment of categorical and scalar data entities in user interfaces”.
8. David Flater, Architecture for Software-Assisted Quantity Calculus, NIST Technical Note 1943, 2016.
9. Alexei V. Samsonovich (Ed.), Biologically Inspired Cognitive Architectures 2019, Proceedings of the Tenth Annual Meeting of the BICA Society, 2019.
10. Vladimir Cvjetkovic, Web physics ontology: Online interactive symbolic computation in physics, 2017 4th Experiment@International Conference (exp.at'17), 2017.
11. Mauro Dragoni, María Poveda-Villalón, Ernesto Jimenez-Ruiz (Eds.), OWL: Experiences and Directions – Reasoner Evaluation: 13th International Workshop, OWLED 2016, and 5th Internation Workshop, ORE 2016, Bologna, Italy, 2016.
12. Jacques Carette, David Aspinall, Christoph Lange, Petr Sojka, Wolfgang Windsteiger (Eds.), Intelligent Computer Mathematics: MKM, Calculemus, DML, and Systems and Projects 2013, Held as Part of CICM 2013, Bath, UK, 2013.
13. Cvetana Krstev, Staša Vujičić Stanković, Duško Vitas, Approximate Measures in the Culinary Domain: Ontology and Lexical Resources, 9th Language Technologies Conference, Information Society, 2014.
14. J.S. Schwarz, S. Lehnhoff, Ontology-Based Development of Smart Grid Co-Simulation Scenarios, EKAW, 2018.
15. Marco Balduini, Emanuele Della Valle, FraPPE: a vocabulary to represent heterogeneous spatio-temporal data to support visual analytics, ISWC, 2015.
