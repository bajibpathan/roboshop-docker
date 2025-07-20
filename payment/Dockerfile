FROM python:3.9.23-alpine3.21 AS builder
WORKDIR /opt/server
COPY requirements.txt .
COPY *.py .
COPY payment.ini .
RUN apk add --no-cache build-base python3-dev linux-headers pcre-dev
RUN apk add --no-cache uwsgi-python3
RUN pip3 install -r requirements.txt


FROM python:3.9.23-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
USER roboshop
EXPOSE 8080
COPY --from=builder /opt/server /opt/server/
CMD ["uwsgi", "--ini", "payment.ini"]



# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server
# COPY requirements.txt .
# COPY *.py .
# COPY payment.ini .
# RUN pip3 install -r requirements.txt
# CMD ["uwsgi", "--ini", "payment.ini"]
