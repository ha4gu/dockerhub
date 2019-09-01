FROM ha4gu/ubuntu-with-curl:16.04
WORKDIR /tmp

# Install Entrykit
ENV ENTRYKIT_VERSION 0.4.0
RUN curl -OsSL https://github.com/progrium/entrykit/releases/download/v${ENTRYKIT_VERSION}/entrykit_${ENTRYKIT_VERSION}_Linux_x86_64.tgz \
  && tar -xf entrykit_${ENTRYKIT_VERSION}_Linux_x86_64.tgz \
  && rm entrykit_${ENTRYKIT_VERSION}_Linux_x86_64.tgz \
  && mv entrykit /bin/entrykit \
  && chmod +x /bin/entrykit \
  && entrykit --symlink

ENTRYPOINT [ \
  "switch", \
    "shell=/bin/bash", "--", \
  "prehook", \
    "/usr/bin/curl -OsSL https://raw.githubusercontent.com/ha4gu/tmux-build-check/master/tmux-build-check.sh", "--", \
  "/bin/bash", "./tmux-build-check.sh" ]
