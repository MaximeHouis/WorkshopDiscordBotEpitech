# :mailbox: Epitech Discord Bot Workshop - Part 02
## :+1: Some useful links

 What | Link
------|------
**Discord Developer Portal**|https://discordapp.com/developers
**discord.py Github**|https://github.com/Rapptz/discord.py
**discord.py Documentation**|https://discordpy.readthedocs.io/en/latest/index.html
**discord.py Cogs**|https://discordpy.readthedocs.io/en/latest/ext/commands/cogs.html
**discord.py Extensions**|https://discordpy.readthedocs.io/en/latest/ext/commands/extensions.html

## :pushpin: Important

* You should take a look at [**Part 01**](Part01_Beginning.md) if you weren't there last time.
* For our examples, our command prefix is `db!`, but you can change it by one of your choice.

---

## :mortar_board: More things about commands
### Some options that can be cool to use
> In part 1, we saw the basics of a discord bot. Here, we will see more tools that you can use to improve your commands
 
 1) Let's try to create a command `db!countdown` that prints a message every seconds *x* times in a specific channel (x is passed as parameter of the command)
 1) Now, let's try to add some aliases to already existing commands. With aliases you are able to call the same command but using a different name. `db!stop`, `db!sleep` and `db!exit` must do the same thing.
 1) You may not know, but a help command is automatically created with your bot. You can see all your existing commands, pretty useful right? But with only the name of the command, it can be hard to understand what it does sometimes. Add descriptions to your commands.

## :gear: Cogs
### What are *Cogs*?

From the official documentation:
> There comes a point in your bot’s development when you want to organize a collection of commands, listeners, and some state into one class. Cogs allow you to do just that.

Let us introduce you to Cogs! You will see, it's very cool. To add some context, we are going to make a Cog where some admins commands will be stored.

 1) Let's start by creating a Cog named Admin
 1) Add the following commands to it:
    * `db!kick` => kicks the user passed by parameters
    * `db!ban`  => bans the user passed by parameters
    * `db!mute` => prevents the user passed by parameters to send any messages
    
:exclamation: *All of these commands **must be only visible by admins** when `db!help` is used*

## :euro: XP and Money
### Add some activities to your bot
> To make your bot more attractive, let's add an xp and a money feature to it. These are popular features that already exist in a lot of bots.

 1) Let's create three new Cogs:
    * System (All the mathematical and other actions will be there)
    * XP (All the commands based on xp are there)
    * Currency (All the commands based on currency are there)
    
:exclamation: *The System Cog have to be invisible for everyone with `db!help` but not the two other Cogs*
 1) Let's create the system that will allow users to level up. When a user posts a message, he gains xp.
    * When a user levels up, mention him with a nice message :)
 1) Users can gain xp now, nice! Let's give them the possibility to gain money now. Add a `db!daily` command that give money to the user (must have a cooldown)
 1) Great! Now, why don't we reward our fellow users with special access at a certain level and enough money ? Add a `db!buy` command that give access to new channels

## :rocket: Extras
### To finish
To finish this part, let's see few more things that can be good to know.
 1) Did you see that the help wasn't in any category on the help message? Fix it, assign it to a category!
 1) Did you hear about Extensions (there's a link on top)? Why not trying to make some of our Cogs to load dynamically when we need them?

---

*By Maxime Houis and Benjamin Praud*
