FROM registry.access.redhat.com/jboss-eap-6/eap-openshift:6.4 

MAINTAINER Andrew Block

# Deployable Environment Variables
ENV TICKET_MONSTER_NEXUS_HOST cicd.ose.example.com
ENV TICKET_MONSTER_NEXUS_PORT 8081
ENV TICKET_MONSTER_GROUP_ID org.jboss.examples
ENV TICKET_MONSTER_ARTIFACT_ID ticket-monster
ENV TICKET_MONSTER_VERSION 2.7.0-SNAPSHOT
ENV TICKET_MONSTER_PACKAGING war

# Curl to JBoss Server
RUN curl -L -sf -o /opt/eap/standalone/deployments/${TICKET_MONSTER_ARTIFACT_ID}-${TICKET_MONSTER_VERSION}.${TICKET_MONSTER_PACKAGING} "http://${TICKET_MONSTER_NEXUS_HOST}:${TICKET_MONSTER_NEXUS_PORT}/nexus/service/local/artifact/maven/redirect?r=public&g=${TICKET_MONSTER_GROUP_ID}&a=${TICKET_MONSTER_ARTIFACT_ID}&v=${TICKET_MONSTER_VERSION}&p=${TICKET_MONSTER_PACKAGING}"

# Start EAP
ENTRYPOINT ["/opt/eap/bin/openshift-launch.sh"]