Citation
========
Rachit Agarwal, Tarek Elsaleh, Elias Tragos, "GDPR-inspired IoT Ontology enabling Semantic Interoperability, Federation of Deployments and Privacy Preserving Applications", (Submitted) 2020

Abstract
========

---

Modifications performed
========
![Ontology](https://github.com/ragarwa2/fiesta-priv/blob/master/ontology.png)

Privacy graph
=======
![privacy](https://github.com/ragarwa2/fiesta-priv/blob/master/privacygraph.png)

Ontology Connections 
======
![Ontology Connections](https://github.com/ragarwa2/fiesta-priv/blob/master/connections.png)


Sample SPARQL Query
===================
```sparql
	# relevant PREFIX
	select ?sensor
	where {
	 # Below is the Augmented part
	 <USER_URI> a con:AllowedParty .
	 <USER_URI> priv:hasPermission  ?permission .
	 ?permission con:permission_given_for_activity ?action .
	 ?action a iot-taxonomy:Discovery .
	 ?action con:activity_has_purpose ?purpose .
	 ?purpose a iot-taxonomy:KnowSensorsInTheArea . 
	 ?permission Con:permission_given_for_data ?sensor .
	 # Below is the original user defined 'where' clause
	 ?sensor sosa:isHostedBy ?platform .
	 ?platform geo:location ?point.
	 ?point geo:lat ?lat . 
	 ?point geo:long ?lng . 
	 FILTER (?lng > -50 && ?lng < 50 && ?lat < 100 && ?lat > 0 ) 
	}
```

Authors
=======
- [Rachit Agarwal](https://rachit.gitlab.com), Inria Paris
- [Tarek Elsaleh](https://github.com/telsaleh), University of Surrey, UK
- Elias Tragos, Insight Center for Data Analytics, UCD

Tools used
==========
- Ontology Documentation: 
	- [Widoco](https://github.com/dgarijo/Widoco)
- Ontology Validation: 
	- [OOPS](http://smart-ics.ee.surrey.ac.uk/fiesta/ontology/fiesta-priv/OOPSevaluation/oopsEval.html#)
	- [Vapour](http://linkeddata.uriburner.com:8000/vapour?uri=http%3A%2F%2Fpurl.org%2Fiot%2Fontology%2Ffiesta-priv%23&acceptRdfXml=1&defaultResponse=dontmind&userAgent=#)


General Information
===================
The ontology file is fiesta-priv.owl and the taxonomy file is iot-taxonomy-lite.owl. Nonetheless, other format files are also made available. The available code, source of the ontology documentation, deploys it along with necessary files


Do you have a problem? Open an issue at [https://github.com/ragarwa2/fiesta-priv](https://github.com/ragarwa2/fiesta-priv)

