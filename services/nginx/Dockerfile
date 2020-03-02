FROM nginx:1.17-alpine

# Remove default server config
RUN rm /etc/nginx/conf.d/default.conf

# For standalone API
COPY api_server.conf /etc/nginx/conf.d

# For full stack, API and web interface
# COPY interface_nginx.conf /etc/nginx/nginx.conf
# COPY interface_server.conf /etc/nginx/conf.d