FROM golang:1.10 AS builder              
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app . # Компилируем приложение специально для дальнейшего запуска в Alpine
# 
# 
FROM alpine:latest                       
WORKDIR /root/
COPY --from=builder ./app .              
EXPOSE 8080
CMD ["./app"]

# FROM golang:1.10 
# WORKDIR /app 
# COPY . .
# RUN go build -o main . 
# CMD ["/app/main"]

# FROM python:3.6-alpine3.8                     
# COPY 1.py /app/                               
# WORKDIR /app                                  
# ENTRYPOINT ["python3", "/app/1.py"]           