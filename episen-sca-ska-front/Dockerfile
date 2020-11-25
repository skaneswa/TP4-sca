FROM httpd:2.4
LABEL maintainer="sakana.kaneswaran@gmail.com" \
      org.label-schema.schema-version="1.0" \
	  org.label-schema.build-date="22-11-2020" \
	  org.label-schema.name="sakanakns/episen-sca-ska-front" \
 	  org.label-schema.description="front with an input, to save order" \
	  org.label-schema.url="http://192.168.99.100:8080/index.html" \
	  org.label-schema.vcs-url="https://github.com/skaneswa/episen-sca-ska-front.git" \
 	  org.label-schema.docker.cmd="docker run -d -it --name front --link backend -p 80:80 sakanakns/episen-sca-ska-front"

COPY ./WebContent/ /usr/local/apache2/htdocs/
EXPOSE 80:80

