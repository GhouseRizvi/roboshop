FROM nginx
RUN rm -rf /usr/share/nginx/htm/index.html
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY default.conf /etc/nginx/nginx.conf
COPY static /usr/share/nginx/html/
ENV CATALOGUE_HOST="catalogues"