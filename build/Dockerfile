FROM v8tix/spinrad:0.0.4.v20200324.0910134
LABEL MAINTAINER="V8TIX"
LABEL MAIL="info@v8tix.com"
RUN ["/bin/bash", "-c", "mkdir /home/v8tix/.ssh"]
ADD \
  https://apache.ups.edu.ec/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz \
  /opt/
ADD packages /home/v8tix/packages
RUN ["/bin/bash", "-c", "chmod +x -R /home/v8tix/packages"]
RUN ["/bin/bash", "-c", "/home/v8tix/packages/packages.sh"]
RUN ["/bin/bash", "-c", "/home/v8tix/libraries/zemni/build/maven/mvn.sh"]
RUN ["/bin/bash", "-c", "/home/v8tix/libraries/zemni/system/setup/ssh/ssh.sh"]
RUN ["/bin/bash", "-c", "chmod 777 /home/v8tix/.ssh"]
RUN ["/bin/bash", "-c", "rm -rf /home/v8tix/packages"]
RUN ["/bin/bash", "-c", "/home/v8tix/libraries/zemni/system/cleanup/cleanup.sh"]
USER v8tix:v8tix
ADD --chown=v8tix:v8tix hosts/known_hosts /home/v8tix/.ssh/
ADD --chown=v8tix:v8tix entrypoint /home/v8tix/entrypoint/
ENTRYPOINT ["/home/v8tix/entrypoint/entrypoint.sh"]