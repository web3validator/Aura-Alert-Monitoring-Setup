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

