FROM debian:stretch-slim

RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
    	bison \
	build-essential \
	ca-certificates \
	ccache \
	cmake \
	dh-python \
	debhelper \
	devscripts \
	doxygen \
	libdistro-info-perl \
	expect \
	flex \
	gdal-bin \
	git \
	graphviz \
	grass-dev \
	libexpat1-dev \
	libfcgi-dev \
	libgdal-dev \
	libgeos-dev \
	libgsl-dev \
	libopenscenegraph-dev \
	libosgearth-dev \
	libpq-dev \
	libproj-dev \
	libqca2-dev \
	libqca2-plugin-ossl \
	libqjson-dev \
	libqscintilla2-dev \
	libqt4-dev \
	libqt4-opengl-dev \
	libqt4-sql-sqlite \
	libqtwebkit-dev \
	libqwt-dev \
	libspatialindex-dev \
	libspatialite-dev \
	libsqlite3-dev \
	libsqlite3-mod-spatialite \
	libzip-dev \
	lighttpd \
	locales \
	ninja-build \
	pkg-config \
	poppler-utils \
	pyqt4-dev-tools \
	pyqt4.qsci-dev \
	python-all \
	python-all-dev \
	python-future \
	python-gdal \
	python-mock \
	python-nose2 \
	python-psycopg2 \
	python-pyspatialite \
	python-qscintilla2 \
	python-qt4 \
	python-qt4-dev \
	python-qt4-sql \
	python-sip \
	python-sip-dev \
	python-yaml \
	qt4-dev-tools \
	qt4-doc-html \
	spawn-fcgi \
	txt2tags \
	xauth \
	xfonts-100dpi \
	xfonts-75dpi \
	xfonts-base \
	xfonts-scalable \
	xvfb \
	cmake-curses-gui\
    && rm -rf /var/lib/apt/lists/*

COPY build.sh /build.sh
RUN chmod u+x /build.sh

ENV DIST stretch

CMD ["/build.sh"]

