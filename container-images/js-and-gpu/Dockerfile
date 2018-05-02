FROM graphistry/gpu-base:9.1

RUN apt-get update && apt-get install -y \
        build-essential \
        curl && \
    curl -sL http://deb.nodesource.com/setup_9.x | bash && \
    apt-get update && apt-get install -y nodejs && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get remove -y build-essential curl