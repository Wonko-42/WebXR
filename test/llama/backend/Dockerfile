FROM alpine:latest

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    git \
    wget \
    libopenblas-dev \
    libomp-dev \
    python3 \
    python3-pip

# Clone llama.cpp repository
RUN git clone https://github.com/ggerganov/llama.cpp /opt/llama.cpp

# Build llama.cpp
WORKDIR /opt/llama.cpp
RUN mkdir build && cd build && cmake .. && make

# Copy model files if needed (you need to add your model files to the llama directory)
# COPY ./models /opt/llama.cpp/models

# Expose the port the service will run on
EXPOSE 8000

# Command to run the LLaMA server
CMD ["./build/bin/server"]
