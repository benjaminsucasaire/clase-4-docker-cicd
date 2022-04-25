FROM docker:19.03.6-dind

FROM jenkins/jenkins:lts

# Add Jenkins init files

COPY src/ /usr/share/jenkins/ref/

COPY --from=docker:19.03.6-dind /usr/local/bin/docker /usr/local/bin/
COPY --chown=jenkins:jenkins plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

USER root

RUN apt-get update && \
    apt-get install -qy \
    -o APT::Install-Recommend=false -o APT::Install-Suggests=false \
    python3-venv make curl git jq 

##installs node
RUN apt-get update && \
    apt-get install -y nodejs && \
    apt-get install -y npm
##install maven
RUN apt-get update && \
    apt-get install -y maven 
##Install Java
RUN apt-get update && \
    apt-get install -y default-jdk 

COPY build/requirements.txt /build/

RUN python3 -m venv /appenv && \
    . /appenv/bin/activate && \
    pip install pip --upgrade && \
    pip install -r /build/requirements.txt

RUN 

COPY entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh
ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

CMD ["/sbin/tini","--","/usr/local/bin/jenkins.sh"]

USER root
