FROM registry.access.redhat.com/ubi9/ubi

RUN curl -L https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 -o /usr/bin/jq && chmod +x /usr/bin/jq
RUN curl -L https://github.com/mikefarah/yq/releases/download/v4.25.1/yq_linux_amd64 -o /usr/bin/yq && chmod +x /usr/bin/yq
RUN curl -L https://mirror.openshift.com/pub/openshift-v4/x86_64/clients/ocp/latest-4.9/openshift-client-linux.tar.gz | tar -xz -C /usr/bin/
RUN curl -L https://github.com/sigstore/cosign/releases/download/v1.8.0/cosign-linux-amd64 -o /usr/bin/cosign && chmod +x /usr/bin/cosign
RUN curl -L https://mirror.openshift.com/pub/openshift-v4/clients/pipeline/0.21.0/tkn-linux-amd64-0.21.0.tar.gz | tar -xz --no-same-owner -C /usr/bin/
RUN curl -L https://github.com/sigstore/rekor/releases/download/v0.5.0/rekor-cli-linux-amd64 -o /usr/bin/rekor-cli && chmod +x /usr/bin/rekor-cli
RUN curl -L https://github.com/open-policy-agent/conftest/releases/download/v0.32.0/conftest_0.32.0_Linux_x86_64.tar.gz | tar -xz --no-same-owner -C /usr/bin
RUN curl -L https://github.com/enterprise-contract/ec-cli/releases/download/snapshot/ec_linux_amd64 -o /usr/bin/ec && chmod +x /usr/bin/ec && ec version

RUN dnf -y --setopt=tsflags=nodocs install \
    git \
    skopeo \
    https://github.com/tektoncd/cli/releases/download/v0.22.0/tektoncd-cli-0.22.0_Linux-64bit.rpm \
    && dnf clean all

COPY util-scripts /appstudio-utils/util-scripts
