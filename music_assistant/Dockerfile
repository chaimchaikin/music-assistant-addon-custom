ARG BUILD_FROM=ghcr.io/music-assistant/server
FROM ${BUILD_FROM}

# Install mitmproxy
RUN apk add --no-cache mitmproxy

# Set up mitmproxy to run in local mode
# ENV HTTP_PROXY=localhost:8080
# ENV HTTPS_PROXY=localhost:8080
ENV REQUESTS_CA_BUNDLE=/root/.mitmproxy/mitmproxy-ca-cert.pem

# Start mitmproxy in local mode alongside Music Assistant
CMD echo "Starting mitmproxy in local mode..." && \
    mitmproxy --mode local --set block_global=false > /tmp/mitmproxy.log 2>&1 & \
    MITM_PID=$! && \
    sleep 2 && \
    if ps -p $MITM_PID > /dev/null 2>&1; then \
        echo "✓ mitmproxy is running (PID: $MITM_PID)" && \
        echo "mitmproxy logs available at /tmp/mitmproxy.log"; \
    else \
        echo "✗ mitmproxy failed to start - check /tmp/mitmproxy.log"; \
    fi && \
    exec /bin/bash /entrypoint.sh
