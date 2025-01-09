# Пояснение
В скрипте [install_warp_proxy.sh](https://github.com/hamid-gh98/x-ui-scripts/blob/main/install_warp_proxy.sh) из main репозитоирия изменена одна строка.  
было
```
function step_create_command() {
  {
    mkdir -p /etc/wireguard
    wget -N -P /etc/wireguard https://gitlab.com/fscarmen/warp/-/raw/main/menu.sh
    chmod +x /etc/wireguard/menu.sh
    ln -sf /etc/wireguard/menu.sh /usr/bin/warp
  }
  [[ $? -ne 0 ]] && STEP_STATUS=0
}
```
стало
```
function step_create_command() {
  {
    mkdir -p /etc/wireguard
    wget -N -P /etc/wireguard https://raw.githubusercontent.com/Dandellion007/warp/refs/heads/main/menu.sh
    chmod +x /etc/wireguard/menu.sh
    ln -sf /etc/wireguard/menu.sh /usr/bin/warp
  }
  [[ $? -ne 0 ]] && STEP_STATUS=0
}
```
Это сделано, т.к. по каким-то причинам wget запросы к gitlab.com с vps получают ответ 302.  
Сделал форк от устаревшего репозитория Warp и добавил туда файл [install_warp_proxy.sh](https://github.com/Dandellion007/x-ui-scripts/blob/main/install_warp_proxy.sh) из актуального репозитоия.

# Install Warp (on socks5 proxy) for 3x-ui
```
bash <(curl -sSL https://raw.githubusercontent.com/Dandellion007/x-ui-scripts/refs/heads/main/install_warp_proxy.sh)
```
