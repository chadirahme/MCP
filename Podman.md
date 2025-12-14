sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_24.04/Release.key \
 | sudo gpg --dearmor -o /etc/apt/keyrings/libcontainers.gpg



echo "deb [signed-by=/etc/apt/keyrings/libcontainers.gpg] \
https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_24.04/ /" \
| sudo tee /etc/apt/sources.list.d/libcontainers.list




export NODE_OPTIONS="--use-openssl-ca"
echo 'export NODE_OPTIONS="--use-openssl-ca"' >> ~/.bashrc
export NODE_EXTRA_CA_CERTS=/usr/local/share/ca-certificates/corp-root-ca.crt
echo 'export NODE_EXTRA_CA_CERTS=/usr/local/share/ca-certificates/corp-root-ca.crt' >> ~/.bashrc


podman run \
  -v /etc/ssl/certs:/etc/ssl/certs:ro \
  -e NODE_EXTRA_CA_CERTS=/etc/ssl/certs/ca-certificates.crt \
  your-image


sudo update-ca-certificates
podman pull registry.access.redhat.com/ubi8/nodejs-20


export NODE_TLS_REJECT_UNAUTHORIZED=0


node mcp-jira-server.js
