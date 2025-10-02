# Use slim Python base
FROM python:3.11-slim AS base

# Set working directory
WORKDIR /app

# Copy dependency files first (better caching)
COPY pyproject.toml uv.lock ./

# Install uv package manager
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv

# Install dependencies (without dev packages)
RUN uv sync --frozen --no-dev

# Copy your actual server code
COPY weather.py .

# Expose a port (only used if HTTP transport mode is enabled later)
EXPOSE 8000
