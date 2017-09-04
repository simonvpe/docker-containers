# Docker container used to automatically generate reveal.js slides from an asciidoc #

## Create the content ##

`index.adoc`

```
= Title Slide

== Slide One

* Foo
* Bar
* World

== Slide Two

Hello World - Good Bye Cruel World

[NOTE.speaker]
--
Actually things aren't that bad
--

```

## Build the docker container ##

Do this once

```bash
docker build -t asciidoctor <path>
```

## Generate the html ##

```bash
<path>/build index.adoc
```
