Abstract
========

Experimentation is crucial for building systems that can evolve to meet high levels of service quality. IoT data that belong to users and from which their personal information can be inferred are frequently shared in the background with third parties for experimentation and building quality services. This data sharing raises privacy concerns especially since in most cases the data are gathered and shared without the user's knowledge or consent. With the introduction of GDPR, experimentation platforms that federate data from different testbeds and data providers must be privacy enabled. We propose an IoT ontology built using available standards that enhances privacy, enables semantic interoperability between testbeds, and allows experimentation. On top, we propose recommendations on how to efficiently use our proposed ontology within IoT testbeds or an IoT data federating platform. Our ontology is evaluated for different quality assessment criteria using standard ontology evaluation tools.

Modifications performed
========
![Ontology](https://github.com/ragarwa2/fiesta-priv/ontology.png)

Privacy graph
=======
![privacy](https://github.com/ragarwa2/fiesta-priv/privacygraph.png)

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
- Tarek Elsaleh, UniS
- Elias Tragos, Insight Center for Data Analytics, UCD

Tools used
==========
- Ontology Documentation: [Widoco](https://github.com/dgarijo/Widoco)

General Information
===================
The ontology file is fiesta-priv.owl and the taxonomy file is iot-taxonomy-lite.owl. Nonetheless, other format files are also made available. The available code source of the ontology documentation and deploys it along with necessary files


Do you have a problem? Open an issue at [https://github.com/ragarwa2/fiesta-priv](https://github.com/ragarwa2/fiesta-priv)
