# Use slim Python base
FROM python:3.11-slim AS base

# Set working directory
WORKDIR /app

# Copy dependency files first for caching
COPY pyproject.toml uv.lock ./

# Install uv package manager
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv

# Install dependencies (no dev dependencies)
RUN uv sync --frozen --no-dev

# Copy your actual server code
COPY weather_server/ ./weather_server/

# Default command to run your server
CMD ["uv", "run", "python", "-m", "weather_server"]
