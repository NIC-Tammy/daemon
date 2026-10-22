FROM registry.access.redhat.com/ubi8/openjdk-8-runtime

USER root

RUN microdnf install -y procps-ng && \
    microdnf clean all

RUN microdnf install -y ksh93 && \
    microdnf clean all

WORKDIR /opt/ellucian/daemon

COPY . .

RUN chgrp -R 0 /opt/ellucian/daemon && \
    chmod -R g=u /opt/ellucian/daemon

RUN mkdir -p /opt/ellucian/test && \
    chgrp -R 0 /opt/ellucian/test && \
    chmod -R g+rwx /opt/ellucian/test

USER 1001

EXPOSE 9090

CMD ["java", \
     "-Xmx512m", \
     "-cp", \
     "dmilistener.jar:lib/*", \
     "com.datatel.server.listener.DMIServerListener"]
