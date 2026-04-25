# build stage
FROM python:3.12-alpine AS builder

WORKDIR /app

COPY requirements.txt .
RUN pip install --user -r requirements.txt

# final stage
FROM python:3.12-alpine

WORKDIR /app

RUN adduser -D appuser

COPY --from=builder /root/.local /home/appuser/.local
COPY . .

ENV PATH=/home/appuser/.local/bin:$PATH

USER appuser

EXPOSE 8000

HEALTHCHECK CMD wget --no-verbose --tries=1 --spider http://localhost:8000 || exit 1

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
