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

# Copy your actual code
COPY weather.py .

# Expose a port (change if your app uses another one)
EXPOSE 8000

# Default command to run the server
CMD ["uv", "run", "python", "weather.py"]
