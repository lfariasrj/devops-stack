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

## Adjusting permissions to `non-root` users:
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
## Update and Upgrade WSL OS
 - Open `WSL Terminal` and digits:
```
sudo apt update && apt upgrade -y
```

## Install DevOps / Development Stack
See other tutorials on repo
