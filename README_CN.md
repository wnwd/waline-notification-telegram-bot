# waline-notification-telegram-bot

中文文档 | [English Doc](./README.md)

一个[Waline](https://waline.js.org/)插件，提供 [**Telegram**](https://t.me/) Bot 通知功能。

## 如何安装
```shell
npm waline-notification-telegram-bot
```

## 如何使用
编辑你的服务端 Waline 文件：

waline.js
```js
const Application = require('@waline/vercel');
const Bark = require('waline-notification-telegram-bot');

module.exports = Application({
  plugins: [Bark],
  async postSave(comment) {
    // do what ever you want after comment saved
  },
});
```

### package.json
把 `"waline-notification-telegram-bot": "latest"` 添加到 `package.json` 文件的依赖项中。


## 环境变量

- `TELEGRAM_BOT_TOKEN`：Telegram bot token，通过 `@BotFather` 创建机器人获取，例如`9435023322:DKEEOGmREFHKHwSpo-KfsgSnjwUGEHEft0A`。
- `TELEGRAM_CHAT_ID`：Telegram chat id，可以是单一用户、频道、群组，通过 `@userinfobot` 获取，例如`098765432`。
- `SITE_NAME`：你的站点名字，用来显示在通知消息中。
- `SITE_URL`：你的站点名字，用来显示在通知消息中。
- `TELEGRAM_TEMPLATE`：（可选）你可以自定义通知模板，请参考官方文档 [this document](https://waline.js.org/guide/features/notification.html#%E9%80%9A%E7%9F%A5%E6%A8%A1%E6%9D%BF)。

默认模板如下：
```js
{{site.name|safe}} 有新评论啦
【昵称】：{{self.nick}}
【邮箱】：{{self.mail}}
【内容】：{{self.comment}}
【地址】：{{site.postUrl}}
```

在修改环境变量后，你需要 **重新部署** Waline服务端。