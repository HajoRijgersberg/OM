# OM - Ontology of units of Measure

The **Ontology of units of Measure (OM) 2.0** models concepts and relations important to scientific research. It has a strong focus on units, quantities, measurements, and dimensions.
OM is modelled in [OWL 2 - Web Ontology Language](https://www.w3.org/TR/owl2-overview/).

**Base URI:** `http://www.ontology-of-units-of-measure.org/resource/om-2/`

**Namespace Prefix:** `om`


#### Overview

* [Ontology of units of Measure](#om)
* [RecordTable ontology](#recordtable)
* [Software](#software)
* [Previous versions](#previous-versions)
* [Acknowledgements](#acknowledgements)
* [Papers on OM](#papers)


### <a name="om"></a>Ontology of units of Measure

The OM ontology provides classes, instances, and properties that represent the different concepts used for defining and using measures and units. It includes, for instance, common units such as the SI units metre (`om:metre`) and kilogram (`om:kilogram`), but also units from other systems of units such as the mile (`om:mile`) or nautical mile (`om:nauticalMile-International`). For many application areas it includes more specific units and quantities, such as the unit of the Hubble constant: km/s/Mpc `om:kilometrePerSecond-TimePerMegaparsec`, or the quantity vaselife `om:VaseLife`.

The following *application areas* are supported by OM:

* Geometry
* Mechanics
* Thermodynamics
* Electromagnetism
* Fluid mechanics
* Chemical physics
* Photometry
* Radiometry and Radiobiology
* Nuclear physics
* Astronomy and Astrophysics
* Cosmology
* Earth science
* Meteorology
* Material science
* Microbiology
* Economics
* Information technology
* Typography
* Shipping
* Food engineering
* Post-harvest technology
* Dynamics of texture and taste
* Packaging

![The UML structure of the OM ontology](images/OM2.0-UML-diagram.png)

**Figure 1.** The UML diagram below shows the class structure of the OM ontology.

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

![Example: Alert Weather](images/OM-2.0-Example-Weather.png)

**Figure 2.** An RDF diagram of the weather information at Alert, Canada.

> In OM, scales, such as the temperature scale are handled differently than their corresponding units. For instance a temperature difference will be expresses as a measure with a unit such as °C or K, where 28°C = 28 K. On the other hand an absolute temperature of 28°C is being referred to the **Celsius scale** and is equal to 301 K. Usually, the scale is used.
 
OM is based on several official paper standards, such as: [The Guide for the Use of the International System of Units](http://physics.nist.gov/cuu/pdf/sp811.pdf), by the NIST. 

### <a name="recordtable"></a>RecordTable Ontology

Included in the OM repository is the [RecordTable](https://github.com/HajoRijgersberg/OM/blob/master/record_table.ttl) vocabulary for semantically modelling tabular data, as a supplement to the existing RDF Data Cube standard. RDF Record Table has a nested structure of records that contain self-describing observations, and is able to cope with irregular, missing and unexpected data. This allows it to escape the constraints of RDF Data Cube and to model complex data, such as that occurring in science and engineering.

### <a name="software"></a>Software

Several software packages support the use, or make use of, OM:

* [`om-java-libs`](https://github.com/dieudonne-willems/om-java-libs): A software library written in Java that uses OM to convert between units.


### <a name="previous-versions"></a>Previous versions

Previous versions were published on the wurvoc platform.

* OM 1.8: [http://www.wurvoc.org/vocabularies/om-1.8/](http://www.wurvoc.org/vocabularies/om-1.8/)


### <a name="acknowledgements"></a>Acknowledgements

We would like to thank Jan Martin Keil and Sirko Schindler of the University of Jena for reviewing OM (see [Unit Ontology Review](https://github.com/fusion-jena/unit-ontology-review)).


### <a name="papers"></a>Papers on OM
   
1. H. Rijgersberg, M.L.I. Wigham, J.L. Top, “How semantics can improve engineering processes. A case of units of measure and quantities.” *Advanced Engineering Informatics*, **25**, 2, 2011, pp. 276-287.
2.  H. Rijgersberg, M.F.J. van Assem, J.L. Top, “Ontology of Units of Measure and Related Concepts.” *Semantic Web*, **4**, 1, 2013, pp. 3-13.
3.  D.J.M. Willems, H. Rijgersberg, J.L. Top, “Identifying and extracting quantitative data in annotated text”, *Proceedings of the Workshop on Semantic Web and Information Extraction (SWAIE 2012)*, Galway, Ireland, 2012, pp. 43-54.
4. Mari Wigham, Hajo Rijgersberg, Martine de Vos, Jan Top. Semantic Support for Tables using RDF Record Table. *International Journal On Advances in Intelligent Systems*, **8** (1 and 2), 2015, 128-144.
