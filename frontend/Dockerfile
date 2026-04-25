FROM nginx:alpine

# create non-root user
RUN adduser -D appuser

# copy app files
COPY . /usr/share/nginx/html

# switch user
USER appuser

# healthcheck (REQUIRED)
HEALTHCHECK CMD wget --no-verbose --tries=1 --spider http://localhost || exit 1
