FROM docker.io/hpretl/iic-osic-tools:2025.05

USER root
RUN echo 'ubuntu ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/ubuntu && \
    chmod 0440 /etc/sudoers.d/ubuntu
ADD install_nix.sh /tmp/install_nix.sh
RUN /tmp/install_nix.sh
RUN chown -R 1000:1000 /nix
RUN chmod 777 /opt
USER 1000:1000
RUN git clone https://github.com/librelane/librelane /opt/librelane
RUN bash --login -c "nix-shell --pure /opt/librelane --run 'librelane --version'"
