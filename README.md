Telegram bot that uses ChatGPT to perform different types of tasks

## Screenshots
![image](https://user-images.githubusercontent.com/93794796/229308106-190d99df-9a55-4f34-b5af-fbbfaf4ae8c3.png)
![image](https://user-images.githubusercontent.com/93794796/229308138-cbd58299-db6c-4179-aa7a-4f26beb163da.png)



### Configuration
Customize the configuration by copying `.env.example` and renaming it to `.env`, then editing the required parameters as desired:

| Parameter                   | Description                                                                                                                                                                                                                   |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OPENAI_API_KEY`            | Your OpenAI API key, you can get it from [here](https://platform.openai.com/account/api-keys)                                                                                                                                 |
| `TELEGRAM_BOT_TOKEN`        | Your Telegram bot's token, obtained using [BotFather](http://t.me/botfather) (see [tutorial](https://core.telegram.org/bots/tutorial#obtain-your-bot-token))                                                                  |
| `ADMIN_USER_IDS`            | Telegram user IDs of admins. These users have access to special admin commands, information and no budget restrictions. Admin IDs don't have to be added to `ALLOWED_TELEGRAM_USER_IDS`. **Note**: by default, no admin ('-') |
| `ALLOWED_TELEGRAM_USER_IDS` | A comma-separated list of Telegram user IDs that are allowed to interact with the bot (use [getidsbot](https://t.me/getidsbot) to find your user ID). **Note**: by default, *everyone* is allowed (`*`)                       |

### Optional configuration
| Parameter                          | Description                                                                                                                                                                                                                      | Default value                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|
| `ENABLE_IMAGE_GENERATION`          | Whether to enable image generation via the `/image` command                                                                                                                                                                      | true                           |
| `ENABLE_TRANSCRIPTION`             | Whether to enable transcriptions of audio and video messages                                                                                                                                                                     | true                           |
| `MONTHLY_USER_BUDGETS`             | A comma-separated list of $-amounts per user from list `ALLOWED_TELEGRAM_USER_IDS` to set custom usage limit of OpenAI API costs for each.  **Note**: by default, *no limits* for anyone (`*`)                                   | `*`                            |
| `MONTHLY_GUEST_BUDGET`             | $-amount as usage limit for all guest users. Guest users are users in group chats that are not in the `ALLOWED_TELEGRAM_USER_IDS` list. Value is ignored if no usage limits are set in user budgets (`MONTHLY_USER_BUDGETS`="*") | `100.0`                        |
| `PROXY`                            | Proxy to be used for OpenAI and Telegram bot (e.g. `http://localhost:8080`)                                                                                                                                                      | -                              |
| `OPENAI_MODEL`                     | The OpenAI model to use for generating responses                                                                                                                                                                                 | `gpt-3.5-turbo`                |
| `ASSISTANT_PROMPT`                 | A system message that sets the tone and controls the behavior of the assistant                                                                                                                                                   | `You are a helpful assistant.` |
| `SHOW_USAGE`                       | Whether to show OpenAI token usage information after each response                                                                                                                                                               | false                          |
| `STREAM`                           | Whether to stream responses. **Note**: incompatible, if enabled, with `N_CHOICES` higher than 1                                                                                                                                  | true                           |
| `MAX_TOKENS`                       | Upper bound on how many tokens the ChatGPT API will return                                                                                                                                                                       | 1200                           |
| `MAX_HISTORY_SIZE`                 | Max number of messages to keep in memory, after which the conversation will be summarised to avoid excessive token usage                                                                                                         | 15                             |
| `MAX_CONVERSATION_AGE_MINUTES`     | Maximum number of minutes a conversation should live since the last message, after which the conversation will be reset                                                                                                          | 180                            |
| `VOICE_REPLY_WITH_TRANSCRIPT_ONLY` | Whether to answer to voice messages with the transcript only or with a ChatGPT response of the transcript                                                                                                                        | true                           |
| `N_CHOICES`                        | Number of answers to generate for each input message. **Note**: setting this to a number higher than 1 will not work properly if `STREAM` is enabled                                                                             | 1                              |
| `TEMPERATURE`                      | Number between 0 and 2. Higher values will make the output more random                                                                                                                                                           | 1.0                            |
| `PRESENCE_PENALTY`                 | Number between -2.0 and 2.0. Positive values penalize new tokens based on whether they appear in the text so far                                                                                                                 | 0                              |
| `FREQUENCY_PENALTY`                | Number between -2.0 and 2.0. Positive values penalize new tokens based on their existing frequency in the text so far                                                                                                            | 0                              |
| `IMAGE_SIZE`                       | The DALL·E generated image size. Allowed values: "256x256", "512x512" or "1024x1024"                                                                                                                                             | "512x512"                      |
| `GROUP_TRIGGER_KEYWORD`            | If set, the bot in group chats will only respond to messages that start with this keyword                                                                                                                                        | ""                             |
| `IGNORE_GROUP_TRANSCRIPTIONS`      | If set to true, the bot will not process transcriptions in group chats                                                                                                                                                           | true                           |
| `TOKEN_PRICE`                      | $-price per 1000 tokens used to compute cost information in usage statistics (https://openai.com/pricing)                                                                                                                        | 0.002                          |
| `IMAGE_PRICES`                     | A comma-separated list with 3 elements of prices for the different image sizes: "256x256", "512x512" and "1024x1024"                                                                                                             | "0.016,0.018,0.02"             |
| `TRANSCRIPTION_PRICE`              | USD-price for one minute of audio transcription                                                                                                                                                                                  | 0.002                          |

Check out the [official API reference](https://platform.openai.com/docs/api-reference/chat) for more details.

### Installing
Clone the repository and navigate to the project directory:

```shell
git clone https://github.com/Carcajo/GPT_bot.git
cd chatgpt-telegram-bot
```

#### From Source
1. Create a virtual environment:
```shell
python -m venv venv
```

2. Activate the virtual environment:
```shell
# For Linux or macOS:
source venv/bin/activate

# For Windows:
venv\Scripts\activate
```

3. Install the dependencies using `requirements.txt` file:
```shell
pip install -r requirements.txt
```

4. Use the following command to start the bot:
```
python bot/main.py
```

## Credits
- [ChatGPT](https://chat.openai.com/chat) from [OpenAI](https://openai.com)
- [python-telegram-bot](https://python-telegram-bot.org)
- [jiaaro/pydub](https://github.com/jiaaro/pydub)

