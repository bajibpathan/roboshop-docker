FROM python:3.9-alpine⁠ AS builder
WORKDIR /opt/server
COPY requirements.txt .
COPY *.py .
COPY payment.ini .
RUN pip3 install -r requirements.txt


FROM python:3.9-alpine
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
