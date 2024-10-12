FROM fedora:latest

RUN dnf update -y && \
    dnf install -y \
    curl \
    git \
    helix \
    zsh \
    fzf \
    ripgrep \
    fd-find \
    && dnf clean all

RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
RUN source ~/.zshrc

# Install mise
RUN curl https://mise.run | sh
RUN echo 'eval "$(~/.local/bin/mise activate zsh)"' >> ~/.zshrc
RUN echo 'export PATH="$HOME/.local/share/mise/shims:$PATH"' >> ~/.zprofile

# Install NodeJS using mise
RUN mise use --global node@lts

# Install TypeScript and TypeScript Language Server
RUN npm install -g typescript typescript-language-server

# Set the working directory
WORKDIR /workspaces

# Set the default command
CMD ["/bin/zsh"]
