ARG BUILD_FROM=ghcr.io/music-assistant/server
FROM ${BUILD_FROM}

# Set custom environment variables
ENV HTTP_PROXY=10.0.0.1:8080
ENV HTTPS_PROXY=10.0.0.1:8080

# The base image already contains the Music Assistant server
# This Dockerfile extends it with custom environment configuration
