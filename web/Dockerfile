FROM nginx:alpine

# Remove default configs
RUN rm -rf /usr/share/nginx/html/* && \
    rm -rf /etc/nginx/nginx.conf && \
    rm -rf /etc/nginx/conf.d/default.conf

# Copy template config (NOT the actual config)
COPY default.conf /etc/nginx/conf.d/default.conf

# Copy static files
COPY ./static /usr/share/nginx/html

# Install gettext for envsubst
RUN apk add --no-cache gettext

# Use entrypoint script to substitute env vars
COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]