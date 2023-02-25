# How-to-make-a-discord-bot-on-python
I will be teaching you how to make a discord bot i n python 3.10

pip install discord in the terminal 

#make a new project in python and create 3 python files

#use pycharm community version!
#
#the 3 files are:
#main.py
#responses.py
#bot.py

#you need a bot token and invite link (DO NOT SHARE THE TOKEN TO ANYONE)
you can get those by going to dev portal


#in the main py type this code:

import bot

if __name__ == '__main__':
  bot.run_discord_bot()
  
  #now I will show you what to do in responses!:
  
  import random

def get_response(message: str) -> str:
    p_message = message.lower()

#now to get the bot to chat these are the commands:

if p_message == "Your message":
return "What the bot will say"


now I will tell you what to do with the bot section:

import discord
import responses



async def send_message(message, user_message, is_private):
    try:
        response = responses.get_response(user_message)
        await message.author.send(response) if is_private else await message.channel.send(response)

    except Exception as e:
        print(e)

def run_discord_bot():
    TOKEN = "your bot token"
    intents = discord.Intents.default()
    intents.message_content = True
    client = discord.Client(intents=intents)

    @client.event
    async def on_ready():
        print(f"{client.user} is now running!")

    @client.event
    async def on_message(message):
        if message.author == client.user:
            return

        username = str(message.author)
        user_message = str(message.content)
        channel = str(message.channel)

        print(f"{username} said: '{user_message}' ({channel})")

        if user_message[0] == "?":
            user_message = user_message[1:]
            await send_message(message, user_message, is_private=True)
        else:
            await send_message(message, user_message, is_private=False)

    client.run(TOKEN)

ENJOY






