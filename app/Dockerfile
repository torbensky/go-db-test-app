#### BUILDER ####

# Setup builder
FROM golang:alpine AS builder
COPY . /go/src/github.com/torbensky/go-postgres-connection-test/app/
WORKDIR /go/src/github.com/torbensky/go-postgres-connection-test/app/

# Build app
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /go/bin/app .

#### RUNTIME ####
FROM scratch
EXPOSE 4567
COPY --from=builder /go/bin/app /app
ENTRYPOINT ["/app"]
