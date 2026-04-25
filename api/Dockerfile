FROM python:3.12-alpine

WORKDIR /app

# create non-root user
RUN adduser -D appuser

# install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# copy app
COPY . .

# switch to non-root user
USER appuser

EXPOSE 8000

# healthcheck (REQUIRED)
HEALTHCHECK CMD wget --no-verbose --tries=1 --spider http://localhost:8000 || exit 1

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
