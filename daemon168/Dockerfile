FROM registry.access.redhat.com/ubi9/openjdk-21-runtime

USER root

WORKDIR /opt/ellucian/daemon

COPY . .

RUN chmod +x startlistener || true

USER 1001

EXPOSE 9090

CMD ["java", \
     "-Xmx512m", \
     "-cp", \
     "dmilistener.jar:lib/*", \
     "com.datatel.server.listener.DMIServerListener"]
