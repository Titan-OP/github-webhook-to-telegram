## GitHub Webhook to Telegram

ʀᴇᴄᴇɪᴠᴇ ɢɪᴛʜᴜʙ ᴡᴇʙʜᴏᴏᴋ ᴇᴠᴇɴᴛꜱ ᴀɴᴅ ꜱᴇɴᴅ ᴛᴏ ᴛᴇʟᴇɢʀᴀᴍ ᴄʜᴀᴛꜱ ᴡɪᴛʜ [ᴀɪᴏʜᴛᴛᴘ](ʜᴛᴛᴘꜱ://ɢɪᴛʜᴜʙ.ᴄᴏᴍ/ᴀɪᴏ-ʟɪʙꜱ/ᴀɪᴏʜᴛᴛᴘ) ᴛʜʀᴏᴜɢʜ [ᴛᴇʟᴇɢʀᴀᴍ ʙᴏᴛ ᴀᴘɪ](ʜᴛᴛᴘꜱ://ᴄᴏʀᴇ.ᴛᴇʟᴇɢʀᴀᴍ.ᴏʀɢ/ʙᴏᴛꜱ/ᴀᴘɪ#ꜱᴇɴᴅᴍᴇꜱꜱᴀɢᴇ)  ᴡʜᴀᴛ ᴛʜɪꜱ ᴘʀᴏᴊᴇᴄᴛ ᴅᴏ ɪꜱ ᴠᴇʀʏ ꜱɪᴍᴘʟᴇ, ɪᴛ ᴅᴏᴇꜱ ɴᴏᴛ ᴜꜱᴇ ᴀɴʏ ᴛᴇʟᴇɢʀᴀᴍ ʙᴏᴛ ᴀᴘɪ ꜰʀᴀᴍᴇᴡᴏʀᴋ/ʟɪʙʀᴀʀʏ ɴᴏʀ ʀᴇᴄᴇɪᴠᴇ ᴜᴘᴅᴀᴛᴇꜱ ꜰʀᴏᴍ ᴛᴇʟᴇɢʀᴀᴍ, ʙᴜᴛ ᴄᴀʟʟɪɴɢ `ꜱᴇɴᴅᴍᴇꜱꜱᴀɢᴇ` ᴍᴇᴛʜᴏᴅ ᴏꜰ ᴛᴇʟᴇɢʀᴀᴍ ʙᴏᴛ ᴀᴘɪ ᴅɪʀᴇᴄᴛʟʏ ʙʏ ꜱᴇɴᴅɪɴɢ `ɢᴇᴛ` ʀᴇQᴜᴇꜱᴛꜱ ᴛʜʀᴏᴜɢʜ ᴀɪᴏʜᴛᴛᴘ. ɪᴛ ꜱʜᴏᴜʟᴅ ʙᴇ ᴀʙʟᴇ ᴛᴏ ʙᴇ ᴜꜱᴇᴅ ᴀʟᴏɴɢ ᴡɪᴛʜ ᴀɴʏ ᴇxɪꜱᴛɪɴɢ ᴛᴇʟᴇɢʀᴀᴍ ʙᴏᴛ ᴡɪᴛʜᴏᴜᴛ ᴄᴏɴꜰʟɪᴄᴛꜱ.  1. ʀᴇᴄᴇɪᴠᴇ ɢɪᴛʜᴜʙ ᴡᴇʙʜᴏᴏᴋꜱ (`ᴘᴏꜱᴛ` ʀᴇQᴜᴇꜱᴛ) 2. ᴠᴇʀɪꜰʏ ᴛʜᴇ ꜱʜᴀ256 ꜱɪɢɴᴀᴛᴜʀᴇ 3. ꜰᴏʀᴍᴀᴛ ᴀɴᴅ ꜱᴇɴᴅ ᴛʜᴇ ᴛᴇxᴛ ᴛᴏ ᴀ ᴛᴇʟᴇɢʀᴀᴍ ᴄʜᴀᴛ ᴛʜʀᴏᴜɢʜ "ꜱᴇɴᴅᴍᴇꜱꜱᴀɢᴇ" ᴍᴇᴛʜᴏᴅ ᴏꜰ    ᴛᴇʟᴇɢʀᴀᴍ ʙᴏᴛ ᴀᴘɪ (`ɢᴇᴛ` ʀᴇQᴜᴇꜱᴛ)

### Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Titan-OP/github-webhook-to-telegram)

### Setup

You need a Telegram bot token, create a Telegram bot with
[BotFather](https://t.me/BotFather) if you don't have one yet.

#### Configuration

1. Go to your GitHub project `Settings - Webhooks - Add webhook`, fill "Payload
   URL", "Content Type" (must be `application/json`) and "Secret". You can also
   do this after start running the project.
2. Copy `config_sample.json` to `config.json` to configure it. `chat_id` can be
   user id or group/channel id/username, make sure the bot is `/start`ed or
   member of the chat with permission to send messages
3. Configure reverse proxy for this app, corresponding configuration for Nginx
   looks like this
   ```
   location /github {
       rewrite ^/github(.*) /$1 break;
       proxy_pass http://127.0.0.1:12345;
   }
   ```

#### Run

```
virtualenv venv
venv/bin/pip install -U -r requirements.txt
venv/bin/python main.py
```

### LICENSE

AGPL-3.0-or-later

```

    github-webhook-to-telegram, receive GitHub webhooks and send to Telegram
    Copyright (C) 2021  Dash Eclipse

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.

    You should have received a copy of the GNU Affero General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.

```

 # **Credits**

 ➥ **тє¢нησ_ρяσ** 

<a href="https://github.com/Titan-OP" alt="Tᴇᴄʜɴᴏ Pʀᴏ"> <img src="https://img.shields.io/badge/-T%E1%B4%87%E1%B4%84%CA%9C%C9%B4%E1%B4%8F%20P%CA%80%E1%B4%8F-blue?logo=github" /></a>     <a href="https://telegram.me/DARK_DEVIL_OP" alt="Tᴇᴄʜɴᴏ Pʀᴏ"> <img src="https://img.shields.io/badge/-T%E1%B4%87%E1%B4%84%CA%9C%C9%B4%E1%B4%8F%20P%CA%80%E1%B4%8F-bluevoilet?logo=telegram" /></a>
