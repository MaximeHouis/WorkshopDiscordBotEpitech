# :mailbox: Epitech Discord Bot Workshop - Part 03
## :+1: Some useful links

 What | Link
------|------
**Discord Developer Portal**|https://discordapp.com/developers
**discord.py Github**|https://github.com/Rapptz/discord.py
**discord.py Documentation**|https://discordpy.readthedocs.io/en/latest/index.html
**discord.py Voice**|https://discordpy.readthedocs.io/en/latest/api.html#voice
**Youtube DL**|https://github.com/ytdl-org/youtube-dl
**Youtube DL Options**|https://github.com/ytdl-org/youtube-dl/blob/master/youtube_dl/YoutubeDL.py#L140

## :warning: Warning
Make sure you've installed the `youtube_dl` and `discord.py[voice]` pip packages for this part.  
Please refer to [**Part 00**](Part00_InstallAndSetup.md) for the installation process.

---

## :musical_note: Let's play some music

So now that you know how to handle events, create commands and have a very good bot structure (cogs),
let's do something *actually* useful. Let's create a **music bot**!

This part is going to be a little more challenging than Part 01 and Part 02, but it's going to be the most interesting one!

### Youtube DL

> **Unlike the name suggests, Youtube DL currently supports more than a thousand websites to fetch audio/video from. You can find the full list of supported services [here](https://github.com/ytdl-org/youtube-dl/tree/master/youtube_dl/extractor).**

#### Example
Downloading a youtube video is pretty straightforward:
```py
from youtube_dl import YoutubeDL

# Default options
ytdl = YoutubeDL()

# Custom options
options = {
    'key': value,
    # ...
}
ytdl = YoutubeDL(options)

# Download from link
ytdl.extract_info("https://www.youtube.com/watch?v=dQw4w9WgXcQ")

# Download from query
ytdl.extract_info("ytsearch:blinding lights audio")
```
Just like that. It's easy.  
Try and play around with this.

Now let's do some actual stuff.

#### Actual stuff

* Write a `download.py` script that downloads the video passed as parameters, **whether the argument is a link or a query**.

```
$> python3 download.py "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
$> python3 download.py "Tetris 99 main theme"
```
=> **Hint**: checking if the argument starts with `http` or `https` is a valid way of doing it. But there is a **much** cleaner and sexier way of doing it. We suggest that you take a look at [**Youtube DL Options**](https://github.com/ytdl-org/youtube-dl/blob/master/youtube_dl/YoutubeDL.py#L140).

* Modify your script to **only** download the audio of the request.

> `ytdl.extract_info(...)` actually returns a dictionary of some data. You can store this dictionary in a variable and print it to see what's inside.  
Some very useful data is in there, but it's hard to read.

* Improve your script to display the returned data in a more readable way.
 ```
 $> python3 download.py "Tetris 99 main theme"
 # Some output here...
 ================ id ================
 63hoSNvS6Z4
 ================ uploader ================
 UnitedBeats
 ================ uploader_id ================
 UCJQ2mQ_WpSGzfkZ475OU98Q
  ================ ... ================
 # etc...
 ```

### Discord voice

Let's put Youtube DL aside for a bit. Let's work with Discord voice stuff now.

* Add a `join` command that joins the user voice channel.
    * You must let the user know if any errors occurred!
* Add a `leave` command that leaves the bot's voice channel.
* Add a `mute` command that toggles bot's audio on/off.

### Let's merge these two

We're almost there! Now let's merge Youtube DL and discord.py!

#### Playing audio from a file

* Add a `play` command that plays the requested url or query and a `stop` command that stops the music.

...

...

...

Okay, okay. Let's do it step by step...  
First of all, here are some functions that *might* be useful:
```py
# Get the downloaded file name from extracted data
ytdl.prepare_filename(ytdata)

# Create a Discord audio source
discord.PCMVolumeTransformer(discord.FFmpegPCMAudio(file))

# Play the audio source, where `ctx.voice_client` is the guild's... voice client.
ctx.voice_client.play(audio_source)

## Read the documentation of each functions for more details
```

* Add a `play` command that:
    * Make the bot join the caller's voice channel (if not in voice chat already).
    * Download the audio with `youtube_dl`.
    * Play the downloaded file.
* Add a `stop` command that disconnects the bot from the voice channel. *Thus stops the music.*

#### Streaming

Downloading takes a lot of time and space. So streaming is a better option for playing music.  
For this last task, we're going to only give you hints. If you've arrived this far, we're sure you will be able to figure out how to do it from hints!

Here they are:
* `youtube_dl.extract_info(...)` has a `download` parameter.
* `youtube_dl.extract_info(...)` returns a dictionary that contains the direct link to the audio file.
* `discord.PCMVolumeTransformer(discord.FFmpegPCMAudio(...))` not only accept file paths, but URLs too. :eyes:

    **:warning: If you want to stream YouTube videos, the link will expire a few minutes after the ytdl call. That's a YouTube restriction that does not apply to most of other services.**  
    You can always find a way around it, but it implies more code and reflection.

---

Once you've done this, congratulations!  
The journey has been amazing, and we hope you liked it!  
You're now ready to develop amazing bots :)

If you want to continue your music bot, here are some cool stuff you could do:
* Volume command
* Queue system (skip to next, display queue, ...)
* Playlist support
* Seek command to go to a certain timestamp
* Loop playlist/song
* *And so on*

Thank you again, have a wonderful day/night!

---

*By Maxime Houis and Benjamin Praud*
