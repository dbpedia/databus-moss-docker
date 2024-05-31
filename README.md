# databus-moss-docker

Run

```
docker compose up
```

Creates a `data` folder for gstore and an `index` folder for the lookup index. Frontend will be running on

```
http://localhost:5000
```

Create layers from

```
http://localhost:5000/create-layer
```

## MOSS API

### Saving layers

`POST api/save?repo=REPO&path=PATH` with document in body

Example: REPO=databus.dbpedia.org, PATH=janfo/testgroup/testartifact/simple.jsonld

Example Body:
```
{
    "@context" : "https://raw.githubusercontent.com/dbpedia/databus-moss/dev/devenv/context2.jsonld",
    "@id" : "https://databus.openenergyplatform.org/hu_wu/test_group/",
    "isExtendedBy" :  {
        "@id" : "#layer",
        "@type" : "DatabusMetadataLayer",
        "layerName": "simple",
        "created" : "2024-03-01 14:37:32"
    }
}
```

Example curl:
```
curl -X POST "http://localhost:5001/api/save?repo=databus.dbpedia.org&path=kurzum/provider.example.com/dataset1/2018.03.11/test.jsonld" -H "Content-Type: application/json" -d '{
    "@context" : "https://raw.githubusercontent.com/dbpedia/databus-moss/dev/devenv/context2.jsonld",
    "@id" : "https://databus.openenergyplatform.org/hu_wu/test_group/",
    "isExtendedBy" :  {
        "@id" : "#layer",
        "@type" : "DatabusMetadataLayer",
        "layerName": "simple",
        "created" : "2024-03-01 14:37:32"
    }
}' -i
```

### Annotating layers (not fully implemented, not sure if needed)
Adds a DatabusMetadataLayer header to a JSON-LD document

`POST /api/annotate?layerName=LAYERNAME&databusResource=DATABUSRESOURCE` with document in body


## Containers

`dbpedia/databus-moss-client:dev`
Frontend using Svelte. Running on port `5000`

`dbpedia/databus-moss-server:dev` 
Server with MOSS API. Running on port `5001`

`dbpedia/lookup:dev`
Lookup Server for Search API. Running on port `5002`

`dbpedia/gstore:dev`
Gstore. Running on port `5003`

`openlink/virtuoso-opensource-7:latest`
Triple Store Backend. Running on port `5004`
