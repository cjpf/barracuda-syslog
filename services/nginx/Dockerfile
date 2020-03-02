FROM nginx:1.17-alpine

# Copy nginx config
COPY ./services/nginx/nginx.conf /etc/nginx/nginx.conf

# Remove default server config
RUN rm /etc/nginx/conf.d/default.conf

# Copy certificates for SSL
COPY ./services/certificates/cert.d/cert.pem /etc/nginx/ssl-bundle.crt
COPY ./services/certificates/cert.d/key.pem /etc/nginx/ssl.key

# Server config for standalone API
COPY ./services/nginx/api_server.conf /etc/nginx/conf.d

# Server config for full stack, API and web interface
# COPY interface_nginx.conf /etc/nginx/nginx.conf
# COPY interface_server.conf /etc/nginx/conf.d

