FROM registry.ci.openshift.org/ocp/builder:rhel-8-golang-1.15-openshift-4.8 AS builder
WORKDIR /go/src/github.com/openshift/cert-manager-operator
COPY . .
RUN make build --warn-undefined-variables

FROM registry.ci.openshift.org/ocp/4.8:base
COPY --from=builder /go/src/github.com/openshift/cert-manager-operator/cert-manager-operator /usr/bin/
COPY manifests /manifests
LABEL io.openshift.release.operator=true
