FROM golang:1.14-alpine as builder

RUN apk add --no-cache make gcc musl-dev linux-headers git

WORKDIR /go/go-opera
COPY . .

ARG GOPROXY=direct
RUN go mod download

RUN export GIT_COMMIT=$(git rev-list -1 HEAD) && \
    export GIT_DATE=$(git log -1 --date=short --pretty=format:%ct) && \
    export CGO_ENABLED=1 && \
    go build \
	-ldflags "-s -w -X github.com/Fantom-foundation/go-opera/cmd/opera/launcher.gitCommit=$GIT_COMMIT -X github.com/Fantom-foundation/go-opera/cmd/opera/launcher.gitDate=$GIT_DATE" \
	-o /tmp/opera \
	./cmd/opera



FROM alpine:latest

RUN apk add --no-cache ca-certificates

COPY --from=builder /tmp/opera /

EXPOSE 5050 18545 18546 18547 19090

ENTRYPOINT ["/opera"]