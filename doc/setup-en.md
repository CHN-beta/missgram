# 3-Minute Quick Start

## 1. Create a Bot

If you do not have a bot, create one first.

Find [@BotFather](https://t.me/botfather) on Telegram and send `/newbot`. Follow the instructions to set a name and username. Save the API Token provided at the end. An API Token consists of digits, a colon, and other characters, for example:

```
1234567890:ABCDEFG-EFIGH_ijks
```

## 2. Add Bot to Channel and Grant Permissions

Add your bot as an Administrator of your Telegram Channel and ensure the "Post Messages" permission is enabled.

## 3. Get Channel ID

Send a message in your channel using any account, then forward that message to [@JsonDumpBot](https://t.me/jsondumpbot). You will receive a JSON response:

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

In this example, `-1003896695973` is your Channel ID. Record it for the next step.

## 4. Set up Misskey Webhook

Open your Misskey instance, go to Settings > Service integration, and click Create Webhook. Fill in the following details:

* Name: Anything (e.g., missgram)
* URL: `https://missgram.chn.moe`
* Secret: Combine your Channel ID and Bot Token, separated by a colon. Example: `-1003896695973:1234567890:ABCDEFG-EFIGH_ijks`
* Trigger: Enable at least "When posting a note" and "When renoted".

Save your settings, and you are all set!

> [!NOTE]  
> To properly map Misskey quotes and replies to Telegram replies, the following data is stored in our database:
>
> * The Misskey instance domain and the note ID.
> * The Telegram channel ID, the forwarded message ID, and their mapping to the original Misskey post.
>
> Your Bot Token is never logged or forwarded. If you still have privacy concerns, please consider self-hosting this service.
