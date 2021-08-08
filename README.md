# img-fairdatapoint
Image Repository für eine modifizierte Python FDP Implementierung von https://github.com/fair-data/fairdatapoint

---------------------------------------------------------------------------------------------------------------------------

# FAIR Data Point (FDP)

[![PyPI](https://img.shields.io/pypi/v/fairdatapoint)](https://pypi.org/project/fairdatapoint/)
[![DOI](https://zenodo.org/badge/37470907.svg)](https://zenodo.org/badge/latestdoi/37470907)
[![Research Software Directory](https://img.shields.io/badge/RSD-FAIRDataPoint-red)](https://research-software.nl/software/fairdatapoint)

## Overview
Python implementation of FAIR Data Point.

FDP is a RESTful web service that enables data owners to describe and to expose their datasets (metadata) as well as data users to discover more information about available datasets according to the [FAIR Data Guiding Principles](http://www.force11.org/group/fairgroup/fairprinciples). In particular, FDP addresses the findability or discoverability of data by providing machine-readable descriptions (metadata) at four hierarchical levels:

*FDP -> catalogs -> datasets -> distributions*

FDP software specification can be found [here](https://github.com/FAIRDataTeam/FAIRDataPoint-Spec/blob/master/spec.md).
Other implementations are also available, e.g. [Java implementation](https://github.com/DTL-FAIRData/FAIRDataPoint)

### Demo server
A demo server of this Python implementation is http://fdp.fairdatapoint.nl/


## Installation
To install FDP From PyPi, do
```bash
pip install fairdatapoint
```

## Running
```bash
fdp-run localhost 80
```

The [Swagger UI](https://swagger.io/tools/swagger-ui/) is enabled for FDP service, and you can have a try by visiting http://localhost.


## Deploy with Docker
Check [fairdatapoint-service](https://github.com/CunliangGeng/fairdatapoint-service).


## Web API documentation
FAIR Data Point (FDP) exposes the following endpoints (URL paths):

| Endpoint |  GET  | POST |  PUT | DELETE     |
|--------------|:--------------:|:-----------------:|:--------------:|:--------------:
| fdp | Output fdp metadata | Create new fdp metadata | Update fdp metadata | Not Allowed |
| catalog     | Output all catalog IDs   | Create new catalog metadata| Not Allowed | Not Allowed |
| dataset     | Output all dataset IDs   | Create new dataset metadata| Not Allowed | Not Allowed |
| distribution  | Output all distribution IDs  | Create new distribution metadata| Not Allowed | Not Allowed |
| catalog/\<catalogID\> | Output \<catalogID\> metadata | Not Allowed | Update \<catalogID\> metadata | Remove \<catalogID\> metadata |
| dataset/\<datasetID\> | Output \<datasetID\> metadata | Not Allowed | Update \<datasetID\> metadata | Remove \<datasetID\> metadata |
| distribution/\<distributionID\> | Output \<distributionID\> metadata | Not Allowed | Update \<distributionID\> metadata | Remove \<distributionID\> metadata |


### Access endpoints to request metadata programmatically
FDP: `curl -iH 'Accept: text/turtle' [BASE URL]/fdp`
Catalog: `curl -iH 'Accept: text/turtle' [BASE URL]/catalog/catalog01`
Dataset: `curl -iH 'Accept: text/turtle' [BASE URL]/dataset/dataset01`
Distribution: `curl -iH 'Accept: text/turtle' [BASE URL]/distribution/dist01`

### FDP supports the following RDF serializations (MIME-types):
* Turtle: `text/turtle`
* N-Triples: `application/n-triples`
* N3: `text/n3`
* RDF/XML: `application/rdf+xml`
* JSON-LD: `application/ld+json`
