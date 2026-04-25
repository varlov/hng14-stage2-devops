FROM python:3.12-alpine

WORKDIR /app

RUN adduser -D workeruser

COPY . .

USER workeruser

CMD ["python", "worker.py"]
