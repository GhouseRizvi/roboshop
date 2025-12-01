FROM nginx:alpine

# Remove default Nginx configuration
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copy custom Nginx configuration
COPY default.conf /etc/nginx/conf.d/

# Copy static files
COPY static /usr/share/nginx/html/

# Set environment variable
ENV CATALOGUE_HOST=catalogue