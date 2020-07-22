FROM busybox
ENV DIST_DIR ../../dist
WORKDIR $DIST_DIR
COPY . /opt/cni/bin
ADD launch.sh /launch.sh
RUN chmod +x /launch.sh

ENV PATH=$PATH:/opt/cni/bin
VOLUME /opt/cni
WORKDIR /opt/cni/bin
