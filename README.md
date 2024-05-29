# databus-moss-docker

Run

```
docker compose up
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
