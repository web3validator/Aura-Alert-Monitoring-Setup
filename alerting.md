# Alerting system trough the Telegram in Aura test network
A short guide on how to set up a notification in telegram (ukranian language)

Отже у нас вже є створенний та працюючий моніторинг тепер ми прикрутимо туди телеграм сповіщання

#### Для цього нам необхідно створити свого бота через Botfather https://t.me/BotFather

Переходимо за посилання та натискаємо кнопку або вводимо /newbot

<img width="394" alt="image" src="https://user-images.githubusercontent.com/59205554/187072414-3bd83456-3399-4edb-850b-6c091312d939.png">

####  Далі він спитає назву бота таким чином:
Гаразд, новий бот. Як ми будемо це називати? Виберіть назву для свого бота.

Вибираємо назву наприклад AuraMonitoringAlerting_bot

(ім'я користувача для вашого бота має закінчуватися на "бот". Ось так, наприклад: TetrisBot або tetris_bot та бути унікальним)

<img width="376" alt="image" src="https://user-images.githubusercontent.com/59205554/187072530-d33c43f8-64da-4884-b81e-90346ce19f44.png">

І він видасть вам неоюхідний нам апі ключ таким чином:

Готово! Вітаємо з новим ботом. Ви знайдете його на t.me/AuraMonitoringAlerting_bot. Тепер ви можете додати опис, про розділ і зображення профілю для вашого бота, перегляньте /help для списку команд. До речі, коли ви закінчите створювати свого крутого бота, надішліть запит у службу підтримки ботів, якщо вам потрібно краще ім’я користувача для нього. Просто переконайтеся, що бот повністю працездатний, перш ніж це робити.

також вам знадобиться чат айди який ви можете отримати за допомогою цього бота https://t.me/RawDataBot

<img width="378" alt="image" src="https://user-images.githubusercontent.com/59205554/187073448-9bde2c35-25b4-48d8-bdc6-2f4f17dbedd1.png">


### Використовуй цей токен щоб отримати доступ до HTTP API:
```shell
123456789:AAG7FFSFyUsaCy-4U-Y5sXW0TYm-M7xfnA
```
Тримайте свій токен у безпеці та зберігайте його безпечно, будь-хто може використовувати його для керування вашим ботом.

Опис API бота див. на цій сторінці: https://core.telegram.org/bots/api

### Отже заходимо в конфіг та міняємо у строці # Telegram settings та   # Chain specific setting також у # Telegram settings
enabled: yes
та api_key: '5555555555:AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'

таким чином

<img width="1040" alt="image" src="https://user-images.githubusercontent.com/59205554/187072799-c7f80d5e-08f7-4585-bbe5-d6feda4ae439.png">
<img width="1107" alt="image" src="https://user-images.githubusercontent.com/59205554/187073087-bdfebe70-5c38-43eb-9d88-06dbc64bb882.png">


### Після цього перезапускаємо докер командой
```shell
docker restart tenderduty
```
<img width="491" alt="image" src="https://user-images.githubusercontent.com/59205554/187072869-c2ac14e8-9c6a-4416-9d7c-b1d3ea53755f.png">


