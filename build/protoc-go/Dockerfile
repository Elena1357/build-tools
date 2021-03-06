FROM golang:1.14

RUN apt-get update && \
    apt-get install -y unzip python3 python3-pip

RUN curl -OL https://github.com/protocolbuffers/protobuf/releases/download/v3.13.0/protoc-3.13.0-linux-x86_64.zip && \
    unzip -o protoc-3.13.0-linux-x86_64.zip -d /usr/local bin/protoc && \
    unzip -o protoc-3.13.0-linux-x86_64.zip -d /usr/local include/* && \
    rm -rf protoc-3.13.0-linux-x86_64.zip

RUN go get -u github.com/golang/protobuf/protoc-gen-go && \
    go get -u github.com/gogo/protobuf/proto && \
    go get -u github.com/gogo/protobuf/gogoproto && \
    go get -u github.com/gogo/protobuf/protoc-gen-gofast && \
    go get -u github.com/gogo/protobuf/protoc-gen-gogo && \
    go get -u github.com/gogo/protobuf/protoc-gen-gogofast && \
    go get -u github.com/gogo/protobuf/protoc-gen-gogofaster && \
    go get -u github.com/gogo/protobuf/protoc-gen-gogoslick && \
    go get -u github.com/pseudomuto/protoc-gen-doc/cmd/protoc-gen-doc && \
    go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway && \
    go get -u github.com/envoyproxy/protoc-gen-validate

RUN mkdir -p /go/src/github.com/google && \
    git clone --branch master https://github.com/google/protobuf /go/src/github.com/google/protobuf && \
    git clone --branch master https://github.com/openconfig/gnmi /go/src/github.com/openconfig/gnmi && \
    mkdir -p /go/src/github.com/ &&\
    wget "https://github.com/grpc/grpc-web/releases/download/1.0.7/protoc-gen-grpc-web-1.0.7-linux-x86_64" --quiet && \
    mv protoc-gen-grpc-web-1.0.7-linux-x86_64 /usr/local/bin/protoc-gen-grpc-web && \
    chmod +x /usr/local/bin/protoc-gen-grpc-web

RUN pip3 install --pre "betterproto[compiler]"

WORKDIR "/go/src/github.com/"

ENTRYPOINT ["/bin/bash"]
