FROM nginx:alpine

# Remove default config
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copy main nginx config
COPY nginx.conf /etc/nginx/nginx.conf

# Copy site config
COPY default.conf /etc/nginx/conf.d/

# Copy static files
COPY static /usr/share/nginx/html/

ENV CATALOGUE_HOST=catalogue