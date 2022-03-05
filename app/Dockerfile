# builder image
FROM golang:1.13-alpine3.11 as builder
RUN mkdir /build
ADD main.go /build/  
WORKDIR /build
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -a -o exercise_1 .

# generate clean, final image for end users
FROM scratch
COPY --from=builder /build/exercise_1 .

# executable
ENTRYPOINT [ "./exercise_1" ]
