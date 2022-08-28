# Aura network Monitoring and alerting setup guide (ukranian language)
Guide how to setup and configure monitoring and alerting systems for Aura test network 
## Для моніторингу ми будемо викорстовувати комплексний інструмент моніторингу мереж Tendermint - Tenderduty
Детальніше можна ознайомитись на офіційному гітхабі https://github.com/lesnikutsa/tenderduty

Даний моніторинг TenderDuty v2 дозволяє здійснювати контроль за нодами та, зокрема, бачити висоту мережі, статус валідатора, аптайм, підписані та пропущені блоки. Також можливе підключення оповіщень у телеграм та дискорд але наша команда зробили свій телеграм бот без будь яких встановлень взагалі.

Установка можлива різними способами, але я використовуватиму установку через Docker, хоча немає принципової різниці

Нам знадобиться окремий сервер або сервер із уже встановленою нодою (нодами). Також потрібно буде знайти відкриті RPC проекта або відкрити свою на основній (не бажано).

Отже почнемо

### оновлюємо репозиторії
```shell
sudo apt update && sudo apt upgrade -y
```
### встановлюємо необхідні утиліти
```shell
sudo apt install curl build-essential git wget jq make gcc tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev -y
```

<img width="1360" alt="image" src="https://user-images.githubusercontent.com/59205554/187070112-ed9d89f5-f1ac-442f-be29-0a7f798c42ef.png">

### встановлення docker
```shell
apt install apt-transport-https ca-certificates curl software-properties-common -y && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && \
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && \
apt update && \
apt-cache policy docker-ce && \
sudo apt install docker-ce -y && \
docker --version
```
<img width="487" alt="image" src="https://user-images.githubusercontent.com/59205554/187070183-6096f046-7c3a-48a1-8132-09b12cbc84bf.png">

### встановлюєм tenderduty

відкриваємо нову сесію в скрін 
```shell
screen -S tenderduty
```
```shell
mkdir tenderduty && cd tenderduty
docker run --rm ghcr.io/blockpane/tenderduty:latest -example-config >config.yml
```
<img width="1178" alt="image" src="https://user-images.githubusercontent.com/59205554/187070286-b2232c32-00d0-42f2-bce8-6b979a93fb8a.png">

### У нас створився конфіг який можно подивитись командою
```shell
nano $HOME/tenderduty/config.yml
```
або переглянути на цьому ж репозиторії -> https://github.com/cybernekit/Aura-Alert-Monitoring-Setup/blob/main/config.yaml

### Для налаштування моніторингу нам достатньо змінити у конфігу:

1) ім'я мережі - aura
2) chain-id - euphoria-1
3) valoper_address auravaloper1clwszjl2m0zjpu94lyzx8lpmzdv8vgv39xctwk (ви можете його знайти в експлорері натиснувши на свого валідатора за посиланням -> https://testnet.owlstake.com/Aura-Network/staking/)
4) url https://snapshot-1.euphoria.aura.network:443 - це є RPC проекту також можуть бути

Public Endpoints:

RPC: https://rpc-euphoria.aura.palamar.io
RPC: https://snapshot-1.euphoria.aura.network
RPC: https://snapshot-2.euphoria.aura.network
RPC: https://rpc-t.aura.nodestake.top

відкриваємо конфіг та змінюємо ці параметри

```shell
nano $HOME/tenderduty/config.yml
```
<img width="857" alt="image" src="https://user-images.githubusercontent.com/59205554/187070874-8d5449bf-3ba5-4800-967f-4caeef4dc0dc.png">
<img width="636" alt="image" src="https://user-images.githubusercontent.com/59205554/187070883-88a7800f-3ac5-4489-bc5f-8a875e98881d.png">


nano $HOME/tenderduty/config.yml
