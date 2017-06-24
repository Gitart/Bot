# Телеграм
## Работа с БОТОМ в Телеграм



### Послать сообщение
```bat
chcp 1251
rem chcp 65001

c:/curl/curl.exe -s -XPOST "https://api.telegram.org/bot000000000:AAAKEY-YOUID/sendMessage" -F chat_id="235188412" -F text="Отлично все работает с нашим ботом" 
pause
```

### Для получения последнего сообщения от бота необходимо указать параметр ?offset=-1
r.http("https://api.telegram.org/bot000000000:AAAKEY-YOUID/getUpdates?offset=-1")

### Получение последнего через базу данных не используя offset=-1
r.http("https://api.telegram.org/bot000000000:AAAKEY-YOUID/getUpdates")("result")("message")("reply_to_message")("chat").max()

### Получение последнего сообщения telegram
r.http("https://api.telegram.org/bot000000000:AAAKEY-YOUID/getUpdates")("result")("message").max()

### Получение всех сообщений
r.http("https://api.telegram.org/bot000000000:AAAKEY-YOUID/getUpdates")("result")("message")

### Добавление кнопочек в telegram
```bat
chcp 1251
rem chcp 65001
rem -H "Content-Type:application/json" -H "Charset:utf-8"
c:/curl/curl.exe -s -XPOST  "https://api.telegram.org/bot000000000:AAAKEY-YOUID/sendMessage" -T "clear.json" -H "Content-Type: application/json; charset=utf-8;" 
rem --trace-ascii trace.txt

pause
```

### message.json
```json
{
  "chat_id": 235188412,
  "text": "Выберите пожалуйста заказ",
  "reply_markup": {
    "keyboard": [
      [
        {"text": "Человек", "request_contact":true, "request_location":true},
        {"text": "Собака",  "request_contact":true, "request_location":true},
        {"text": "Лошадь",  "request_contact":true, "request_location":true}
      ],
      [
        {"text": "Запрос"},
        {"text": "Карточка"},
        {"text": "Список"}
      ]
    ]
  }
}

```

### Убрать кнопочки в боте
```bat
chcp 1251
rem -H "Content-Type:application/json" -H "Charset:utf-8"
c:/curl/curl.exe -s -XPOST  "https://api.telegram.org/bot000000000:AAAKEY-YOUID/sendMessage" -T "clear.json" -H "Content-Type: application/json; charset=utf-8;" 
rem --trace-ascii trace.txt

pause
```

### clear.json
```json
{
  "chat_id": 235188412,
  "text": "Clear",
  "hide_keyboard":true
}
```
