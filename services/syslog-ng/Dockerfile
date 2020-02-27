FROM balabit/syslog-ng:latest

RUN rm /etc/syslog-ng/syslog-ng.conf
COPY syslog-ng.conf /etc/syslog-ng/syslog-ng.conf
COPY ca.d /etc/syslog-ng/ca.d
COPY cert.d /etc/syslog-ng/cert.d
