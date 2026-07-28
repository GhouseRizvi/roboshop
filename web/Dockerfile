FROM nginx:alpine

# Copy config directly (no environment variable substitution needed)
COPY default.conf /etc/nginx/conf.d/default.conf
COPY ./static /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]