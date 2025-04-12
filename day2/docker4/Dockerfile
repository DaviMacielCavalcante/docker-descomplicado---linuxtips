FROM golang:1.18 AS buildando

WORKDIR /app

COPY hello.go ./

RUN go mod init hello

RUN go build -o /app/hello

FROM alpine:3.15.9

COPY --from=buildando /app/hello /app/hello

ENV APP="Hello World"

ARG GIROPOPS="strigus"

ENV GIROPOPS=$GIROPOPS

RUN echo "Giropops is: $GIROPOPS"

CMD [ "/app/hello" ]