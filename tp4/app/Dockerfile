FROM debian
RUN apt-get update -y
RUN apt-get install -y curl tar build-essential
COPY forum/ /app
EXPOSE 80/tcp
RUN curl -O "https://dl.google.com/go/go1.19.3.linux-arm64.tar.gz"
RUN tar xvf "go1.19.3.linux-arm64.tar.gz"
RUN mv go /usr/local/
WORKDIR /app
RUN /usr/local/go/bin/go build -o forum /app/server/server.go 
RUN /usr/local/go/bin/go build -o setupforadmin /app/setupadmin/setupadmin.go
RUN rm -rf *.go server test README.MD go.* setupadmin
CMD [ "/app/forum" ]
