FROM ubuntu:22.04

# Use supervisor to manage services
RUN apt-get update && apt-get install -y \
    supervisor \
    && rm -rf /var/lib/apt/lists/*

# Install XFCE
RUN apt-get update && apt-get install -y \
    xfce4 \
    && rm -rf /var/lib/apt/lists/*
# Fix "Failed to execute default terminal emulator. Input/output error."
# Ref: https://askubuntu.com/a/1118319
# Ref: https://discourse.ubuntu.com/t/ctrl-alt-t-opens-xterm/60235/2
RUN apt-get update && apt-get install -y \
    xfce4-terminal \
    && rm -rf /var/lib/apt/lists/*
RUN update-alternatives --set x-terminal-emulator /usr/bin/xfce4-terminal.wrapper

# Install TigerVNC
RUN apt-get update && apt-get install -y \
    tigervnc-standalone-server \
    && rm -rf /var/lib/apt/lists/*

# Configure supervisor to manage the TigerVNC server
RUN cat <<EOF > /etc/supervisor/conf.d/tigervnc.conf
[program:tigervnc]
command=/usr/bin/vncserver :0 -geometry 1920x1080 -depth 24 -localhost no
stderr_logfile=/var/log/tigervnc.err.log
stdout_logfile=/var/log/tigervnc.out.log
EOF

# Set the password for VNC
RUN touch ~/.Xauthority
ARG TIGERVNC_PASSWORD
RUN mkdir -p ~/.vnc && \
    echo "${TIGERVNC_PASSWORD}" | vncpasswd -f > ~/.vnc/passwd && \
    chmod 600 ~/.vnc/passwd

CMD ["/usr/bin/supervisord", "-n"]
