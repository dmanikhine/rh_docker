FROM eclipse-temurin:11.0.16.1_1-jdk-centos7 AS jre-build

# Generate smaller java runtime without unneeded files
# for now we include the full module path to maintain compatibility
# while still saving space (approx 200mb from the full distribution)
RUN jlink \
         --add-modules ALL-MODULE-PATH \
         --strip-debug \
         --no-man-pages \
         --no-header-files \
         --compress=2 \
         --output /javaruntime

#FROM registry.access.redhat.com/ubi7/ubi:7.9
FROM dmanikhine/rh_tools

ARG VERSION=4.13
ARG user=jenkins
ARG group=jenkins
ARG uid=1000
ARG gid=1000

RUN groupadd -g ${gid} ${group}
RUN useradd -c "Jenkins user" -d /home/${user} -u ${uid} -g ${gid} -m ${user}
#RUN dnf install langpacks-en glibc-all-langpacks -y

ARG AGENT_WORKDIR=/home/${user}/agent
 
#ENV LANG C.UTF-8
ENV JAVA_HOME=/opt/java/openjdk
COPY --from=jre-build /javaruntime $JAVA_HOME

 
RUN curl --create-dirs -fsSLo /usr/share/jenkins/agent.jar https://repo.jenkins-ci.org/public/org/jenkins-ci/main/remoting/${VERSION}/remoting-${VERSION}.jar \
 && chmod 755 /usr/share/jenkins \
 && chmod 644 /usr/share/jenkins/agent.jar \
 && ln -sf /usr/share/jenkins/agent.jar /usr/share/jenkins/slave.jar
 
USER ${user}
ENV AGENT_WORKDIR=${AGENT_WORKDIR}
ENV PATH "/usr/share/jenkins:${JAVA_HOME}/bin:${PATH}"

RUN mkdir /home/${user}/.jenkins && mkdir -p ${AGENT_WORKDIR}
 
VOLUME /home/${user}/.jenkins
VOLUME ${AGENT_WORKDIR}
WORKDIR /home/${user}

LABEL \
  org.opencontainers.image.vendor="IDS (dma)" \
  org.opencontainers.image.title="Unofficial RHEL Jenkins Agent Base Docker image" \
  org.opencontainers.image.version="${VERSION}"
  
USER root
COPY jenkins-agent /usr/local/bin/jenkins-agent
RUN chmod +x /usr/local/bin/jenkins-agent &&\
    ln -s /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-slave
USER ${user}

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]      
