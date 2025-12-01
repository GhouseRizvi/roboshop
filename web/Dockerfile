FROM almalinux:8

# Update and install nginx
RUN dnf update -y && \
    dnf install -y nginx && \
    dnf clean all

# Remove default files
RUN rm -rf /usr/share/nginx/html/*

# Copy nginx configuration
COPY default.conf /etc/nginx/nginx.conf

# Copy static files
COPY static /usr/share/nginx/html/

# Set permissions
RUN chown -R nginx:nginx /usr/share/nginx/html && \
    chmod -R 755 /usr/share/nginx/html

# Expose port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
