# Docker QGIS

This repository includes materials for building and running two Docker images: `qgis-build` and
`qgis-exec`.

It is devoted to the 2.18.18 version of QGIS-server, and may not work for other version : dependencies may change, and thus Dockerfile as well.

The `qgis-build` image can be used for building QGIS from (2.18.18) source. Debian packages of QGIS are
created.

The `qgis-exec` image can be used for executing QGIS Server. The image is built either from official
QGIS packages downloaded from http://qgis.org/debian or from local QGIS packages generated using the
`qgis-build` image.
