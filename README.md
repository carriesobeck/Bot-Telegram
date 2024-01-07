<p>To create a simple telegram bot in Python, you can use the python-telegram-bot library. First of all, install it by running the command:</p>
pip install python-telegram-bot
<p>Then here is some sample code for a simple echo bot that sends back the text you send to it</p>
from telegram import Update
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters, CallbackContext

# Вставьте ваш токен бота здесь
TOKEN = "YOUR_BOT_TOKEN"

# Обработчик команды /start
def start(update: Update, context: CallbackContext) -> None:
    update.message.reply_text('Привет! Я эхо-бот. Отправьте мне что-нибудь, и я повторю.')

# Обработчик текстовых сообщений
def echo(update: Update, context: CallbackContext) -> None:
    update.message.reply_text(update.message.text)

def main() -> None:
    # Создаем объект Updater и передаем ему токен бота
    updater = Updater(TOKEN)

    # Получаем диспетчер для регистрации обработчиков
    dispatcher = updater.dispatcher

    # Регистрируем обработчики команд и сообщений
    dispatcher.add_handler(CommandHandler("start", start))
    dispatcher.add_handler(MessageHandler(Filters.text & ~Filters.command, echo))

    # Запускаем бота
    updater.start_polling()

    # Запускаем бота и ожидаем завершения
    updater.idle()

if __name__ == '__main__':
    main()

<p>Replace "YOUR_BOT_TOKEN" with the token of your telegram bot. Ensure that the token remains confidential.</p>
<p>This bot responds to the /start command by sending a welcome message. It also repeats any text you send it. This is just an example and you can customize the bot according to your needs.</p>
