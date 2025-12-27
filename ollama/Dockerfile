FROM ollama/ollama:latest

# Ollama listens on localhost by default in some setups; ensure it binds to all interfaces
ENV OLLAMA_HOST=0.0.0.0:11434
ENV OLLAMA_MODELS=/models

EXPOSE 11434

# Persist pulled models
VOLUME ["/root/.ollama"]

CMD ["serve"]