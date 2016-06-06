FROM jhipster/jhipster
USER root
WORKDIR "/root/app"
VOLUME ["/root/app"]

RUN mkdir jhipster-speedup
RUN cd jhipster-speedup

RUN wget https://github.com/jhipster/jhipster-travis-build/archive/master.zip
RUN unzip -qq master.zip
RUN rm master.zip
