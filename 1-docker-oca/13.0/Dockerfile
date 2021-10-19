FROM local/docker-odoo:13.0
MAINTAINER Agustin Pighin <agustinpighin@Gmail.com>

USER root

# Get repositories & add files
WORKDIR ${RESOURCES}
COPY ./oca-sources.txt ./
#RUN mkdir -p ${EXTRA_ADDONS}
RUN python3 get_addons.py ${SOURCES}/repositories --depth=1 --sources_file=oca-sources.txt

WORKDIR /
USER odoo
