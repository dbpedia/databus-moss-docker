# databus-moss-docker

Run

```
git clone https://github.com/dbpedia/databus-moss-docker.git
cd databus-moss-docker
docker compose pull
docker compose up
```

Go to 
```
http://localhost:5000
```

Login at the top right and click on your username. Alternatively go to
```
http://localhost:5000/user
```

Navigate to `Keys`, create an API key and save your key on your local machine. Your API key should look something like this:
```
OWM3ZTY3NTItNjQ2ZC00ZDE5LWE4ZTctYjc4NGFkNjkyZDFj_17784836-6dc2-4880-96ac-42a0f3570bb2
```


To create a layer on your MOSS instance, issue the following `curl`:
```
curl -X POST 'http://localhost:5001/api/save?layer=simple&resource=https://databus.openenergyplatform.org/hu_wu/test_group' \
  -H 'accept: application/json' \
  -H 'X-API-KEY: OWM3ZTY3NTItNjQ2ZC00ZDE5LWE4ZTctYjc4NGFkNjkyZDFj_17784836-6dc2-4880-96ac-42a0f3570bb2' \
  -H 'Content-Type: application/ld+json' \
  -d '{
   "@context": "https://raw.githubusercontent.com/dbpedia/databus-moss/dev/devenv/context2.jsonld",
   "@id": "https://databus.openenergyplatform.org/hu_wu/test_group",
   "isExtendedBy": {
      "@id": "#layer",
      "@type": "DatabusMetadataLayer",
      "layerName": "simple",
      "created": "2024-03-01 14:37:32"
   },
   "subject": "http://openenergy-platform.org/ontology/oeo/OEO_00000446"
}'
```

Creates a `data` folder for gstore and an `index` folder for the lookup index


## Containers

`missing`
Frontend

`dbpedia/databus-moss-server:dev` 
Server with MOSS API

`dbpedia/lookup:dev`
Lookup Server for Search API

`dbpedia/gstore:dev`
Gstore

`openlink/virtuoso-opensource-7:latest`
Triple Store Backend
