FROM python:3.9.0-alpine
ADD app/ /app
WORKDIR /app
EXPOSE 8000
RUN addgroup -g 1001 web &&\
    adduser -D -u 1001 -G web web &&\
    chown 1001:1001 /home/web &&\
    chown web:web /app

USER web
ENTRYPOINT ["python3", "-m", "http.server", "8000"]