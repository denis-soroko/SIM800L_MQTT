# Удаленное управление запуском двигателя автомобиля через интернет с использованием протокола MQTT.

[Видео на youtube](https://www.youtube.com/watch?v=HzQ7oy439Qk)

[Анатомия автозапуска 5.2](https://www.drive2.ru/c/499270089304965988/)

[Само устройство останется таким же](https://github.com/martinhol221/SIM800L_DTMF_control/blob/master/README.md) изменится только прошивка и функции управления. 

![](https://github.com/martinhol221/SIM800L_DTMF_control/raw/master/img/conecting-001.JPG)

**Останется:**

* Входящий звонок, автоподъем, распознавание DTMF команд `123`,`789`,`*` и `#`

* Исходящий звонок при срабатывании датчика вибрации только при поставленной охране

* Отключение зажигания по таймеру

**Будут убраны не нужные функции:**

* Исходящее SMS сообщение

* Входящие SMS команды

* Отправка показаний датчиков на сервер narodmon.ru

* Прием команд из приложения Народмон 2017

* Автопрогрев

* Моргалка светодиодом

* Голосовое информирование о событиях в "трубку" - под вопросм


**Добавится:**

* Онлайн связь с автомобилем по интернет соединению с получением из авто данных температуры и напряжения каждых 60 сек.

* Возможность установки таймера прогрева из приложения "накруткой"

* Возможность запуска двигателя в одно касание кнопки

* Возможность снатия/постановки на охрану нажатием одной кнопки.


**Главное окно программы MQTT Dash** 
![](https://github.com/martinhol221/SIM800L_MQTT/raw/master/other/mqtt-18.jpg)


### Регистрация на https://www.cloudmqtt.com/

* зарегистрируйтесь и залогинтесь

* нажмите  **+Create New Instanct**

* Name **любое значение**

* Plan  **Cute Cat (Free)**

* Data center **EU-West-1 (Ireland)**

* Tags **любое значение**

* Нажать по **Create New Instance**

* Перейти в созданный профиль

Server

User

Password

Port

перенести значение этих параметров в  MQTT Dash, [Скачать](https://play.google.com/store/apps/details?id=net.routix.mqttdash&hl=ru), можно использовать любой другой MQTT клиент

**Настройка приложения к серверу**

![](https://github.com/martinhol221/SIM800L_MQTT/raw/master/other/mqtt-9.jpg)

**Загрузка настроек интерфейса**

Открыть в приложении ***Импорт/экспорт*** (1)

Нажать ***Подписаться и ждать метрики*** (2) 

![](https://github.com/martinhol221/SIM800L_MQTT/blob/master/other/setupMqtt.JPG)

В вебсокете https://api.cloudmqtt.com/console/________/websocket  заполнить  и отправить настройки в телефон

![](https://github.com/martinhol221/SIM800L_MQTT/blob/master/other/setupMqtt2.JPG)

***Topic***  metrics/exchange

***Message***  
[{"mainTextSize":"LARGE","postfix":"°","prefix":"","textColor":-12517632,"topicPub":"","topic":"C5/ds0","lastPayload":"26.81","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":false,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Двигатель","id":"2e64db41-6222-4723-90ac-929a1f16b75a","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":5,"type":1},{"mainTextSize":"LARGE","postfix":"°","prefix":"","textColor":-16384,"topicPub":"","topic":"C5/ds1","lastPayload":"26.63","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":false,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Салон","id":"23395be6-0d65-44c7-a661-8e50d494fc97","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":7,"type":1},{"prefix":"","postfix":"V","minValue":0.0,"decimalPrecision":2,"displayPayloadValue":true,"progressColor":-4128769,"maxValue":15.0,"topicPub":"","topic":"C5/vbat","lastPayload":"13.50","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":false,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Напряжение","id":"2b7ab4a9-4bfa-435e-b384-da2bf322ed75","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":11,"type":3},{"prefix":"","postfix":"мин","minValue":0.0,"decimalPrecision":0,"displayPayloadValue":true,"progressColor":-192,"maxValue":30.0,"topicPub":"C5/settimer","topic":"C5/timer","lastPayload":"0","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":true,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Таймер прогрева","id":"03bd3e53-d473-4ab6-987f-269a25f2cce5","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":12,"type":3},{"iconOff":"ic_lock_opened_outline","iconOn":"ic_lock_closed_outline","payloadOn":"lock1","payloadOff":"lock0","onColor":-65472,"offColor":-12517632,"topicPub":"C5/comand","topic":"C5/security","lastPayload":"lock0","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":true,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Охрана","id":"6a98ecb5-c75a-47ad-bb8c-e3a83d071bdf","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":15,"type":2},{"iconOff":"ic_car","iconOn":"ic_propeller_on","payloadOn":"start","payloadOff":"stop","onColor":-32513,"offColor":-128,"topicPub":"C5/comand","topic":"C5/engine","lastPayload":"stop","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":true,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Двигатель","id":"d0b38071-570d-4712-9dbf-4c0dbb51459d","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":13,"type":2},{"mainTextSize":"LARGE","postfix":"ч.","prefix":"","textColor":-64,"topicPub":"","topic":"C5/uptime","lastPayload":"3","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":false,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Время работы","id":"7700ae13-aef6-4f14-9c60-57fc1da44422","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172151,"longId":8,"type":1},{"iconOff":"ic_autorenew","iconOn":"ic_autorenew","payloadOn":"Refresh","payloadOff":"Refresh","onColor":-1,"offColor":-1,"topicPub":"","topic":"C5/comand","lastPayload":"Refresh","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":true,"enableIntermediateState":false,"updateLastPayloadOnPub":false,"name":"Обновить данные","id":"f7bfd0fc-f0c1-43c9-9b5c-9621ea4e6f13","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172335,"longId":10,"type":2},{"mainTextSize":"LARGE","postfix":"","prefix":"","textColor":-1,"topicPub":"","topic":"C5/comand","lastPayload":"Refresh","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":true,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Команды в машину","id":"700dbe98-03b8-42db-86e1-3211559400f8","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523172335,"longId":14,"type":1},{"mainTextSize":"SMALL","postfix":"","prefix":"","textColor":-1,"topicPub":"","topic":"C5/status","lastPayload":"Подключено","jsOnReceive":"","jsonPath":"","intermediateStateTimeout":0,"enteredIntermediateStateAt":0,"qos":0,"retained":false,"enablePub":true,"enableIntermediateState":true,"updateLastPayloadOnPub":true,"name":"Последнее событие","id":"433a3000-a8aa-4061-a1b7-4e9e5de167ff","jsBlinkExpression":"","jsOnDisplay":"","jsOnTap":"","lastActivity":1523171127,"longId":1,"type":1}]

