ARG SRC_DIR="/home/jian/go1.19/src/github.com/ceph-csi/"
ARG GO_ARCH

#-- Final container
FROM hub.easystack.cn/captain/cephcsi:testold

ARG SRC_DIR

LABEL maintainers="Ceph-CSI Authors" \
    version=${CSI_IMAGE_VERSION} \
    architecture=${GO_ARCH} \
    description="Ceph-CSI Plugin"


RUN  rm /usr/local/bin/cephcsi

COPY _output/cephcsi /usr/local/bin/cephcsi

# verify that all dynamically linked libraries are available
RUN [ $(ldd /usr/local/bin/cephcsi | grep -c '=> not found') = '0' ]

ENTRYPOINT ["/usr/local/bin/cephcsi"]
