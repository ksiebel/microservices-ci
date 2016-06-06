FROM jhipster/jhipster
USER root
WORKDIR "/root/app"
VOLUME ["/root/app"]

RUN mkdir jhipster-speedup \
 && cd jhipster-speedup \
 && wget https://github.com/jhipster/jhipster-travis-build/archive/master.zip \
 && unzip -qq master.zip \
 && rm master.zip
