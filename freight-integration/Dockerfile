FROM eclipse-temurin:8-jdk AS builder

ARG MULE_VERSION=3.9.0

RUN mkdir -p /opt/mule \
    && curl -fsSL \
       "https://repository.mulesoft.org/releases/org/mule/distributions/mule-standalone/${MULE_VERSION}/mule-standalone-${MULE_VERSION}.tar.gz" \
       -o /tmp/mule.tar.gz \
    && tar -xzf /tmp/mule.tar.gz \
       -C /opt/mule \
       --strip-components=1 \
    && rm /tmp/mule.tar.gz

FROM eclipse-temurin:8-jdk

ENV MULE_HOME=/opt/mule

COPY --from=builder /opt/mule /opt/mule

WORKDIR /opt/mule

CMD ["/opt/mule/bin/mule", "console"]
