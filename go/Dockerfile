FROM golang:1.20 AS builder

WORKDIR /usr/src/app

COPY go.mod ./

RUN go mod download && go mod verify

COPY . .

RUN go build -v -o /usr/local/bin/app ./...


CMD ["app"]

FROM scratch
WORKDIR /usr/src/app

COPY --from=builder /usr/local/bin/app /usr/local/bin/app 

CMD ["app"]

