# hadolint global ignore=DL3041,DL3013
FROM registry.access.redhat.com/ubi9/python-311:1

COPY requirements.txt \
     vllm/requirements-build.txt \
     vllm/requirements-common.txt \
     vllm/requirements-cpu.txt \
     /opt/app-root/src/

USER 0

RUN chown -R 1001:0 ./

USER 1001

COPY .s2i/bin/ /opt/app-root/bin/

WORKDIR /opt/app-root/src

RUN /opt/app-root/bin/assemble

EXPOSE 8080

COPY .s2i/bin/run /opt/app-root/bin/run

ENTRYPOINT ["/opt/app-root/bin/run"]
