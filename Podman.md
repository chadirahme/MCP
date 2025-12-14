sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_24.04/Release.key \
 | sudo gpg --dearmor -o /etc/apt/keyrings/libcontainers.gpg



echo "deb [signed-by=/etc/apt/keyrings/libcontainers.gpg] \
https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_24.04/ /" \
| sudo tee /etc/apt/sources.list.d/libcontainers.list


