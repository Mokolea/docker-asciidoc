# docker-asciidoc [![Size](https://img.shields.io/microbadger/image-size/mokolea/asciidoc.svg)](https://hub.docker.com/r/mokolea/asciidoc) [![Layers](https://img.shields.io/microbadger/layers/mokolea/asciidoc.svg)](https://hub.docker.com/r/mokolea/asciidoc)

Test AsciiDoc (includes [pandoc](https://hub.docker.com/r/mokolea/pandoc))

[![Release](https://img.shields.io/github/release/Mokolea/docker-asciidoc.svg)](https://github.com/Mokolea/docker-asciidoc/releases)

## AsciiDoc
 - http://asciidoc.org/
 - http://asciidoc.org/userguide.html

## Usage
 - Start container from current asciidoc-project directory: `$ docker run -it -v $(pwd):/data --name asciidoc -h asciidoc mokolea/asciidoc:latest`
 - Optional: Set user and group IDs to override the default image user (1000:1000) by using parameter:
    - `-u root` for root user
    - `-u $(id -u):$(id -g)` for current host user (experimental - does not work without additional configuration)
 - Subsequent use of the same container: `$ docker start -ai asciidoc`
 - Start bash shell in the already running container: `$ docker exec -it asciidoc bash`

## Test
```
docker@asciidoc:/data$ asciidoc --version
asciidoc 8.6.9
docker@asciidoc:/data$ 

docker@asciidoc:/data$ docbook2pdf --version
DocBook-utils version 0.6.14 (jw version 1.1)
docker@asciidoc:/data$ 

docker@asciidoc:/data$ asciidoc -b docbook hello-world.adoc && docbook2pdf hello-world.xml
Using catalogs: /etc/sgml/catalog
Using stylesheet: /usr/share/docbook-utils/docbook-utils.dsl#print
Working on: /data/hello-world.xml
Done.
docker@asciidoc:/data$ 
```

## TODO
 - Add hello-world.adoc

## Done
 - Setup appropriate user to not run tools (asciidoc, docbook2pdf, ...) as root and so not have generated files from root in host file system

-- Mario
