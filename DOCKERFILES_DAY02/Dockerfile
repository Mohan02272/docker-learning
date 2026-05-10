FROM ubuntu

RUN apt update && \
    apt install -y nginx curl vim && \
    apt clean

CMD ["nginx", "-g", "daemon off;"]
