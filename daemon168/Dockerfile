FROM registry.access.redhat.com/ubi8/openjdk-8-runtime

USER root

WORKDIR /opt/ellucian/daemon

COPY . .

RUN chgrp -R 0 /opt/ellucian/daemon && \
    chmod -R g=u /opt/ellucian/daemon

USER 1001

EXPOSE 9090

CMD ["java", \
     "-Xmx512m", \
     "-cp", \
     "dmilistener.jar:lib/*", \
     "com.datatel.server.listener.DMIServerListener"]
