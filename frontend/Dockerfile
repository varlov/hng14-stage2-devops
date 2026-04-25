FROM node:20-alpine AS builder

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .
RUN npm run build || true

FROM nginx:alpine

RUN adduser -D appuser

COPY --from=builder /app /usr/share/nginx/html

USER appuser

HEALTHCHECK CMD wget --no-verbose --tries=1 --spider http://localhost || exit 1
