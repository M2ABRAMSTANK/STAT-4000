FROM mcr.microsoft.com/devcontainers/python:3.12

# Remove problematic yarn repo that causes GPG issues
RUN rm -f /etc/apt/sources.list.d/yarn.list 2>/dev/null || true

# Install R
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get install -y --no-install-recommends \
        r-base \
        r-base-dev \
        pandoc \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Make R library writable by vscode user
RUN chmod -R 777 /usr/local/lib/R/site-library

# Install R languageserver for VS Code R extension
RUN R -e "install.packages('languageserver', repos='https://cloud.r-project.org/')"
