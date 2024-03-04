# Configuring Your WSL

## Install WSL
 - Open `Powershell` and digits:
```
wsl --install
```
## Configuring WSL hardware Limits
 - Open `Powershell` and digits:
```
Add-Content -Path "$Env:USERPROFILE/.wslconfig" -Value "[wsl2]"
Add-Content -Path "$Env:USERPROFILE/.wslconfig" -Value "memory=<memory>GB"
Add-Content -Path "$Env:USERPROFILE/.wslconfig" -Value "processors=<processor>"
```

## Update and Upgrade WSL OS
 - Open `WSL Terminal` and digits:
```
sudo apt update && apt upgrade -y
```

## Install DevOps / Development Stack
See other tutorials on repo or tips bellow.

### Adjusting permissions to `non-root` users to docker:
 - Open `WSL Terminal` and digits:
```
sudo su
```

 - Paste config bellow:
```
{
  echo "[automount]";
  echo "options = \"metadata\"";
  echo "[boot]";
  echo "command=\"service docker start\"";
} > /etc/wsl.conf
```
 - Restart WSL Workload to apply configs: Open `Powershell` and digits:
```
wsl --shutdown
```

### Install awscli
To install the `AWS CLI`, run the following commands.
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

### Install kubectl
To install the `kubectl`, run the following commands.
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

### Install helm
To install the `helm`, run the following commands.
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

### Configuring git sources
```
{
  echo "Git host 1";
  echo "  Port 221"; # custom port
  echo "  AddKeysToAgent yes";
  echo "  IdentityFile ~/.ssh/key1";
  echo "git host 2";
  echo "  AddKeysToAgent yes";
  echo "  IdentityFile ~/.ssh/key2";
} > ~/.ssh/config
```
