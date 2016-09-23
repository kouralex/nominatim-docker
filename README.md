# Nominatim Docker

100% working container for [Nominatim](https://github.com/twain47/Nominatim).

## Local Changes

- Use Finland data file as default.
- Use fi_FI.UTF-8 as the locale.
- Make it possible to use a build arg to set the data file to download.
- Update the Nominatim search.php to raise the hard-coded memory limit.

# Supported tags and respective `Dockerfile` links

- [`2.5.0`, `2.5`  (*2.5/Dockerfile*)](https://github.com/mediagis/nominatim-docker/tree/master/2.5)

Run [http://wiki.openstreetmap.org/wiki/Nominatim](http://wiki.openstreetmap.org/wiki/Nominatim) in a docker container. Clones the branch and builds it. 

Uses Ubuntu 14.04 and PostgreSQL 9.3


# Building

To rebuild the image locally execute

```
docker build -t nominatim .
```

# Changing the OSM url to download and use a different country

This example downloads the belize data during compilation:
```
docker build --build-arg OSM=http://download.geofabrik.de/central-america/belize-latest.osm.pbf  -t nominatim .
```

# Running

By default the container exposes port `8080` To run the container execute

```
# remove any existing containers
docker rm -f nominatim_container || echo "nominatim_container not found, skipping removal"
docker run -p 8080:8080 --name nominatim_container --detach nominatim
```

Check the logs of the running container

```
docker logs nominatim_container
```

Stop the container
```
docker stop nominatim_container
```

Connect to the nominatim webserver with curl. If this succeeds, open [http://localhost:8080/](http:/localhost:8080) in a web browser

```
curl "http://localhost:8080"
```