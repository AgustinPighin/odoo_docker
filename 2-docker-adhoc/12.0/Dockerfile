FROM local/odoo-oca:12.0
MAINTAINER Juan Jose Scarafia <jjs@adhoc.com.ar>

USER root

RUN apt-get update  -y 
RUN apt-get install -y swig libcups2-dev unixodbc-dev
RUN pip install --no-cache-dir pyodbc jwt

# Get repositories & add files
WORKDIR ${RESOURCES}
COPY ./adhoc-sources.txt ./
#RUN mkdir -p ${}
RUN python3 get_addons.py ${SOURCES}/repositories --depth=1 --sources_file=adhoc-sources.txt
WORKDIR /

# para pyafipws
# TODO activar
# RUN chmod 777 -R /usr/local/lib/python3/dist-packages/pyafipws/

# seteamos SERVER_WIDE_MODULES de los modulos incluidos
ENV SERVER_WIDE_MODULES web,server_mode,database_tools,

USER odoo
