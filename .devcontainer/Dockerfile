FROM mcr.microsoft.com/dotnet/sdk:5.0-focal

# Install missing 'ps' command that some VS Code extensions depend on:
RUN apt-get update && \
    apt-get install -y procps

RUN  apt install -y gnupg ca-certificates && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF && \
    "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | tee /etc/apt/sources.list.d/mono-official-stable.list && \
    apt update && \
    apt install mono-complete -y

RUN groupadd -g 1000 -r core && \
    useradd -u 1000 -r -g core -m -s $(which bash) core


WORKDIR /app
ENV PATH "$PATH:/home/core/.dotnet/tools"

USER core
