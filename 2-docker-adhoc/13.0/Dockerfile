FROM local/odoo-oca:13.0
MAINTAINER Agustin Pighin <agustinpighin@gmail.com>

USER root

RUN apt-get update  -y 
RUN apt-get install -y swig libcups2-dev unixodbc-dev
RUN pip install --no-cache-dir pyodbc jwt
RUN pip install m2crypto

# Get repositories & add files
WORKDIR ${RESOURCES}
COPY ./adhoc-sources.txt ./
#RUN mkdir -p ${}
RUN python3 get_addons.py ${SOURCES}/repositories --depth=1 --sources_file=adhoc-sources.txt
WORKDIR /

# para pyafipws
 RUN chmod 777 -R /usr/local/lib/python3.7/site-packages/pyafipws/

# seteamos SERVER_WIDE_MODULES de los modulos incluidos
ENV SERVER_WIDE_MODULES web,server_mode,database_tools,

USER odoo
