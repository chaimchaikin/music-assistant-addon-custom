ARG BUILD_FROM=ghcr.io/music-assistant/server
FROM ${BUILD_FROM}

# Install mitmproxy
RUN apk add --no-cache mitmproxy

# Set up mitmproxy to run in local mode
# ENV HTTP_PROXY=localhost:8080
# ENV HTTPS_PROXY=localhost:8080
ENV REQUESTS_CA_BUNDLE=/root/.mitmproxy/mitmproxy-ca-cert.pem

# Start mitmproxy in local mode alongside Music Assistant
CMD mitmproxy --mode local --set block_global=false & exec /bin/bash /entrypoint.sh
