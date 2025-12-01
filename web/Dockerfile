FROM nginx

# Remove default files
RUN rm -f /usr/share/nginx/html/index.html /etc/nginx/conf.d/default.conf

# Copy nginx configuration
COPY default.conf /etc/nginx/nginx.conf

# Copy static files
COPY static /usr/share/nginx/html/

ENV CATALOGUE_HOST=catalogue