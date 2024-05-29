# databus-moss-docker

Run

```
docker compose up
```

Creates a `data` folder for gstore and an `index` folder for the lookup index


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
