How to Add a New Command to Your Bot

This bot is structured so that each command lives in its own file inside the commands folder as a function that registers a handler to the bot.

To add a new command, follow these steps:

1. Create a new Python file for your command inside the commands folder.
For example, create commands/newcommand.py

2. Define a function
   register_newcommand(bot) inside that file, which registers a message handler for your command.

For example 

def register_newcommand(bot):
    @bot.message_handler(commands=['newcommand'])
    def handle_newcommand(message):
        bot.send_message(message.chat.id, "This is a response from newcommand!")
        
3. Import and register your command in the main bot file (main.py)
   Add these lines:
   
from commands.newcommand import register_newcommand

register_newcommand(bot)

4. Restart your bot so the new command is loaded.

   Example summary of your current main.py
   
import telebot
import json
from commands.shoti import register_shoti_command
from commands.sim import register_sim_command
from commands.ai import register_ai_command

with open("token.json", "r") as f:
    data = json.load(f)
token = data["token"]

bot = telebot.TeleBot(token)

"""Register commands here"""
register_newcommand_command(bot)

bot_info = bot.get_me()
print(f"Success login! Bot name: @{bot_info.username}")

bot.polling()

Summary:
Each command is a function that takes the bot instance and adds handlers.
Import that function in your main file and call it with the bot instance.
Keep your commands modular and organized in the commands folder.
Restart the bot after adding new commands.
