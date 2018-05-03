FROM debian:stretch-slim

COPY deb/libqgis-analysis*.deb \
     deb/libqgis-networkanalysis*.deb \
     deb/libqgis-app*.deb \
     deb/libqgis-core*.deb \
     deb/libqgis-customwidgets*.deb \
     deb/libqgisgrass7*.deb \
     deb/libqgis-gui*.deb \
     deb/libqgis-native*.deb \
     deb/libqgispython*.deb \
     deb/libqgis-server*.deb \
     deb/python-qgis*.deb \
     deb/qgis-common*.deb \
     deb/qgis-providers*.deb \
     deb/qgis-server*.deb \
     /qgis/

#COPY extra/* /usr/local/share/fonts/truetype/myfonts/


RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        spawn-fcgi \
        xauth \
        xvfb \ 
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-core*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-analysis*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-gui*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-customwidgets_*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-app*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgisgrass7-*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgispython*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-server*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/python-qgis-common_*~stretch1_all.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/libqgis-networkanalysis*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/qgis-providers-common_*~stretch1_all.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/qgis-providers_*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/python-qgis_*~stretch1_amd64.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/qgis-common_*~stretch1_all.deb \
     && apt install --no-install-recommends --no-install-suggests -y /qgis/qgis-server_*~stretch1_amd64.deb \
  #  && apt install --no-install-recommends --no-install-suggests -y /qgis/*.deb \
     && rm -rf /var/lib/apt/lists/*


RUN useradd -m qgis

#RUN chown -R qgis:qgis /usr/local/share/fonts/truetype/myfonts


ENV TINI_VERSION v0.17.0
#ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
ADD extra/tini /tini
RUN chmod +x /tini

ENV QGIS_PREFIX_PATH /usr
ENV QGIS_SERVER_LOG_FILE /var/log/qgisserver.log
ENV QGIS_SERVER_LOG_LEVEL 0
ENV QGIS_DEBUG 1

RUN ["chmod", "777", "/usr/share/qgis/resources"]
RUN ["chmod", "777", "/usr/share/qgis/resources/srs-template.db"]
RUN ["cp", "/usr/share/qgis/resources/srs-template.db" , "/usr/share/qgis/resources/srs.db"]

USER qgis
WORKDIR /home/qgis


CMD ["/tini", "--", "xvfb-run", "-a", \
     "spawn-fcgi", "-p", "5555", "-n", "-d", "/home/qgis", \
     "/usr/lib/cgi-bin/qgis_mapserv.fcgi"]
