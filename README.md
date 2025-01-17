# waline-notification-telegram-bot

A [Waline](https://waline.js.org/) plugin that provide [**Telegram**](https://t.me/) Bot spport.

[中文文档](./README_CN.md) | English Doc

## How to install
```shell
npm install waline-notification-telegram-bot
```

## How to use
Edit your Waline File:

indes.js
```js
const Application = require('@waline/vercel');
const Telegram = require('waline-notification-telegram-bot');

module.exports = Application({
  plugins: [Telegram],
  async postSave(comment) {
    // do what ever you want after comment saved
  },
});
```

### package.json
Add `"waline-notification-telegram-bot": "latest"` into `package.json` dependencies.


## Environment Variables
- `TELEGRAM_BOT_TOKEN`: Telegram bot token, get it by creating a bot via `@BotFather`. e.g. `9435023322:DKEEOGmREFHKHwSpo-KfsgSnjwUGEHEft0A`
- `TELEGRAM_CHAT_ID`: Telegram chat id, can be a single user, channel, or group, get it via `@userinfobot`. e.g. `098765432`
- `SITE_NAME`: Your site name, used for display in notification message.
- `SITE_URL`: Your site URL, used for display in notification message.
- `TELEGRAM_TEMPLATE`: (optional) Your custom notification template, please refer [this document](https://waline.js.org/en/guide/features/notification.html#notification-template).

The default template as below:
```js
{{site.name|safe}} 有新评论啦
【昵称】：{{self.nick}}
【邮箱】：{{self.mail}}
【内容】：{{self.comment}}
【地址】：{{site.postUrl}}
```

You need **redeploy** after change environment variables.