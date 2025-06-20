import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print('{bot.user} olarak giriş yaptık')
.
@bot.command()
async def hello(ctx):
    await ctx.send("Merhaba! Ben {bot.user}, bir Discord sohbet botuyum!")

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)

@bot.command()
async def joined(ctx):
    user_id = 944306257706238044  
    member = ctx.guild.get_member(user_id)
    if member is None:
        await ctx.send("Kullanıcı bulunamadı ya da bu sunucuda değil.")
        return

    joined_time = discord.utils.format_dt(member.joined_at, style='F')
    relative_time = discord.utils.format_dt(member.joined_at, style='R')
    await ctx.send(f'{member.name} sunucuya {joined_time} tarihinde katıldı. ({relative_time})')

*

bot.run ("MTExMjMxNzgwODgyNzcxMTU5OQ.GqI3ua.yt4PNUekktYftYYFWk1v7_yUhJ4LBAq-MEwciI")
