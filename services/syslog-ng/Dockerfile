FROM balabit/syslog-ng:latest

RUN rm /etc/syslog-ng/syslog-ng.conf
COPY syslog-ng.conf /etc/syslog-ng/syslog-ng.conf
COPY ./services/certificates/ca.d /etc/syslog-ng/ca.d
COPY ./services/certificates/cert.d /etc/syslog-ng/cert.d