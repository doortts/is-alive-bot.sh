# is-alive-bot.sh
Server status check and Telegram message notification sending shell

[English](#is-alive-bot)

크게 두 단계로 작업이 진행됩니다.

- 텔레그램 봇 생성해서 api 키 받기
- is-alive-bot.sh 을 실행해서 지시대로 따라하기


텔레그램 봇 생성
----

1. BotFather 추가

https://telegram.me/botfather

2. 새로운 bot 생성
/newbot

3. 이름 정하기
```
Alright, a new bot. How are we going to call it? Please choose a name for your bot.
```
라고 물어보면 공백 상관없이 편하게 이름 짓는다
예) is Yona Alive

4. bot username 정하기. Bot으로 끝나는 이름이어야 함
```
Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bo
```
예) isYonaAlive


5. API 토큰 받기
```
...
Use this token to access the HTTP API:
346694123:AAFhL69MxM8kOqjtUtIeRAguasgVYw7H3zF4
...
```

이후 부터는 is-alive-bot.sh를 실행시키면 안내를 해줍니다.



is-alive-bot.sh 실행하면서 지시대로 따라하기
---

sh is-alive-bot.sh 을 실행해보면 아래처럼 메시지가 나옵니다.

```                                                       
Telegram Bot api token is reqruied!

ex>
sh is-alive-bot.sh 328394984:AAFhL69afasfqjtUtIeRSzIagVYw7H3zF4

See: https://core.telegram.org/bots#3-how-do-i-create-a-bot
```

앞에서 받은 토큰을 이용해서 다시 실행해 봅니다.


sh is-alive-bot.sh 328394984:AAFhL69afasfqjtUtIeRSzIagVYw7H3zF4                    

```

---------------------------------------------------
Find chat id of user or group with your own eyes..

..chat":{ "id": 621884 ...  <= user or group id!
---------------------------------------------------

{"ok":true,"result":[]}
---------------------------------------------------

and then retry...
sh is-alive-bot.sh API_TOKEN USER_CHAT_ID

ex>
sh is-alive-bot.sh 328394984:AAFhL69afasfqjtUtIeRSzIagVYw7H3zF4 2156789
```

해당 id 값을 찾아서 인자로 넣어서 실행합니다.

예)
```
nohup sh is-alive-bot.sh 328394984:AAFhL69afasfqjtUtIeRSzIagVYw7H3zF4 2156789 &
```

파일로 설정 저장하기
---
is-alive-bot.sh 을 에디터로 열어보면...

```
#
# Check Yona server status and send me/group a message with telegram
#

# Configurations start..
# ~~~~~~~~~~~~~~~~~~~~~~

# API_TOKEN=123456789:AbCdEfgijk1LmPQRSTu234v5Wx-yZA67BCD
API_TOKEN=""

# USER_CHAT_ID=123456789
USER_CHAT_ID=""

# TARGET_SERVER="http://my-yona-server.com"
TARGET_SERVER="http://127.0.0.1:9000"

CHECK_URL="$TARGET_SERVER/-_-api/v1/hello"

EXPECTED_STATUS_CODE=200

# Polling Time (sec)
POLLING_TIME=60

# Messages
messageOnDown="Yona is unavaliable!"
messageOnRevive="Yona comeback!"

# Configurations end here...
...
```

해당 부분을 설정하면 굳이 파라미터를 이용해서 실행하지 않아도 됩니다.

#is-alive-bot

[한국어](#is-alive-botsh)

There are two big steps.

- Create a telegram bot and get an api key
- Run is-alive-bot.sh and follow the instructions

Create a telegram bot
----

1. Add BotFather

Https://telegram.me/botfather

2. Create a new bot
/ Newbot

3. Determine your name
`` `
Alright, a new bot. How are we going to call it? Please choose a name for your bot.
`` `
If you ask, you can easily name it regardless of the space.
Ex) is Yona Alive

4. Setting the bot username. Must end with Bot
`` `
Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bo
`` `
Ex) isYonaAlive


5. Get an API token
`` `
...
Use this to access the HTTP API:
346694123: AAFhL69MxM8kOqjtUtIeRAguasgVYw7H3zF4
...
`` `

From now on, run is-alive-bot.sh and it will guide you.


Running is-alive-bot.sh and following instructions
---

If you run sh is-alive-bot.sh, you will see a message like this:

"Ok": true, "result": []}
-------------------------------------------------- -

And then retry ...
Sh is-alive-bot.sh API_TOKEN USER_CHAT_ID

Ex>
Sh is-alive-bot.sh 328394984: AAFhL69afasfqjtUtIeRSzIagVYw7H3zF4 2156789
`` `

Find the id value and run it with arguments.

Yes)
`` `
Nohup sh is-alive-bot.sh 328394984: AAFhL69afasfqjtUtIeRSzIagVYw7H3zF4 2156789 &
`` `

Setting
---
Opening is-alive-bot.sh in the editor ...

`` `
#
# Check Yona server status and send me / group a message with telegram
#

# Configurations start ..
# ~~~~~~~~~~~~~~~~~~~~~~

# API_TOKEN = 123456789: AbCdEfgijk1LmPQRSTu234v5Wx-yZA67BCD
API_TOKEN = ""

# USER_CHAT_ID = 123456789
USER_CHAT_ID = ""

# TARGET_SERVER = "http://my-yona-server.com"
TARGET_SERVER = "http://127.0.0.1:9000"

CHECK_URL = "$ TARGET_SERVER / -_- api / v1 / hello"

EXPECTED_STATUS_CODE = 200

# Polling Time (sec)
POLLING_TIME = 60

# Messages
MessageOnDown = "Yona is unavaliable!"
MessageOnRevive = "Yona comeback!"

# Configurations end here ...
...
`` `
