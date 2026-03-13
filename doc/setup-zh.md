# 三分钟快速开始

## 1. 创建 Bot

如果您没有机器人，请先创建一个机器人。

在 Telegram 中联系 [@BotFather](https://t.me/botfather) 并发送 `/newbot`。按照指示设置机器人的名称和用户名。保存最后获取到的 API Token。API Token包含一组数字、一个冒号、一些其它的内容，例如：

```
1234567890:ABCDEFG-EFIGH_ijks
```

## 2. 将 Bot 添加到频道并授予权限

你的机器人添加为 Telegram 频道的管理员，并至少开启发布消息的权限。

## 3. 获取频道 ID

使用任意账号在频道中发送一条消息，并将消息转发给 [@JsonDumpBot](https://t.me/jsondumpbot)，你将会得到：

```json
{
  "message": {
    "forward_origin": {
      "type": "channel",
      "chat": {
        "id": -1003896695973,
        "title": "test channel",
        "type": "channel"
      }
    }
  }
}
```

这里 `-1003896695973` 即为频道 ID，将其记录下来。

## 4. 设置 Misskey Webhook

打开您的 Misskey 站点，在设置-连接服务中，点击创建 Webhook，填写以下内容：

* 名称：随意，例如 missgram
* URL：`https://missgram.chn.moe`
* 密钥：将频道 ID 与 Bot Token 组合到一起，以冒号分隔。例如：`-1003896695973:1234567890:ABCDEFG-EFIGH_ijks`
* 触发器: 至少打开“发布贴文时”和“被转发时”。

保存，完成！

> [!NOTE]  
> 为了将 Misskey 中的引用/回复正确翻译为 Telegram 平台的回复，我们会将以下内容记录到数据库:
>
> * Misskey 帖子所在的站点域名，以及帖子的 ID；
> * Telegram 频道 ID 和转发的消息 ID，以及与帖子的对应。
> 
> 您的 Bot Token 永远不会被记录或转发。若您对隐私仍有顾虑，可以考虑自建转发服务。
