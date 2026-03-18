FROM mcr.microsoft.com/devcontainers/base:ubuntu

ARG TARGETARCH

# Install Quarto CLI + Typst CLI at build time so they are preinstalled in the container image.
RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
      ca-certificates \
      curl \
      xz-utils; \
    rm -rf /var/lib/apt/lists/*; \
    case "${TARGETARCH}" in \
      amd64) QUARTO_ARCH="amd64" ;; \
      arm64) QUARTO_ARCH="arm64" ;; \
      *) echo "Unsupported TARGETARCH for Quarto: ${TARGETARCH}"; exit 1 ;; \
    esac; \
    QUARTO_TAG="$(curl -fsSLI -o /dev/null -w '%{url_effective}' https://github.com/quarto-dev/quarto-cli/releases/latest | sed -E 's#.*/tag/(v[0-9.]+)$#\1#')"; \
    QUARTO_VERSION="${QUARTO_TAG#v}"; \
    curl -fsSL -o /tmp/quarto.deb "https://github.com/quarto-dev/quarto-cli/releases/download/${QUARTO_TAG}/quarto-${QUARTO_VERSION}-linux-${QUARTO_ARCH}.deb"; \
    apt-get update; \
    apt-get install -y /tmp/quarto.deb; \
    rm -f /tmp/quarto.deb; \
    rm -rf /var/lib/apt/lists/*; \
    TYPST_TAG="$(curl -fsSLI -o /dev/null -w '%{url_effective}' https://github.com/typst/typst/releases/latest | sed -E 's#.*/tag/(v[0-9.]+)$#\1#')"; \
    case "${TARGETARCH}" in \
      amd64) TYPST_ARCH="x86_64" ;; \
      arm64) TYPST_ARCH="aarch64" ;; \
      *) echo "Unsupported TARGETARCH for Typst: ${TARGETARCH}"; exit 1 ;; \
    esac; \
    TYPST_TAR="typst-${TYPST_ARCH}-unknown-linux-musl.tar.xz"; \
    curl -fsSL -o /tmp/typst.tar.xz "https://github.com/typst/typst/releases/download/${TYPST_TAG}/${TYPST_TAR}"; \
    mkdir -p /tmp/typst; \
    tar -xJf /tmp/typst.tar.xz -C /tmp/typst; \
    install -m 0755 "/tmp/typst/typst-${TYPST_ARCH}-unknown-linux-musl/typst" /usr/local/bin/typst; \
    rm -rf /tmp/typst /tmp/typst.tar.xz
