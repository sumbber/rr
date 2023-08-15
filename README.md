import discord
import random
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='/', intents=intents)
items = {'Бумага':'2-5 месяцев',
         'Банановая кожура':'от 2 до 5 недель',
         'Пластиковая бутылка':'400 лет'

}
@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.command
async def help(ctx):
    await ctx.send('Этот бот создан для помози природе от отходов!')
    await ctx.send("Вы можете узнать сколько разлагается предметы спомощь команды /decomposition")
    await ctx.send('Вы можете узнать как сделать поделку например из пластиковой бутылки, туалетного рулончика и т.д.')
@bot.command
async def decomposition(ctx, item):
    if item in items:
        time_decompos = items[item]    
        await ctx.send(f'Предмет {item} разлагается {time_decompos}')
    else:
        await ctx.send('информация не найдена')
bot.run('MTEzOTg4NDc4OTE5Mzc4OTQ2MQ.GTNsC7.sC51b5AO2vigXcktgnTKVl2CxL8grQWciMRRYU')
