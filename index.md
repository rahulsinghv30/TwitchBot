# Twitch Bot
This project is using Python and Raspberry Pi in order to code a twitch bot which can directly read the chat and sends the messages onto the shell. The project I chose is the Twitch Bot, it is supposed to transfer the messages from the twitch website onto the shell of the bot and run commands which is part of my modifications for this project. I have some prior experience in python which is what this project is based on and I use twitch regularly so I know the features of the app and what I can do to make the bot more efficient. 

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Rahul | Dublin High School | Software Engineering | Incoming Senior |

<a href="https://ibb.co/qk4hBxH"><img src="https://i.ibb.co/6gpGYNK/screenshot.png" alt="screenshot" border="0"></a>
  
# Final Milestone
For my twitch bot, I first set up the Raspberry Pi and synced it with my VNC viewer code app so that I can access Rasberry Pi through my computer screen. Then I  wrote the basic twitch bot code from scratch where I faced some issues. I utilized my first week to debug the code and connect my Twitch bot to the shell. During the second week, I used the twitch API to code the bot in order to add more modifications to my bot. I made two modifications during that week and made my second milestone video. During the third week, I cleaned my code, worked on the Github website, and made sure to debug some parts of the code that were not working. A quick rundown of my modifications, using the twitch IO I made some commands such as; !hello the bot will spit out Hello, and the person’s name in the twitch chat. If someone types !randomNum, then the bot will spit out a random number between 1-10. I also added a routine function that is provided by api. This would display the bot controller a custom message. In my case, I have programmed it to show the message of like and subscribe after every 10 seconds.

Some challenges which I faced during this project were the Python version and some OAuth key changes. In order to run my code, I had to update the python version manually from 3.9.2 to 3.10.5. But then the code was still not working and I realized that I had to generate a new OAuth key to make the bot sync with my twitch channel. In the future, I can add more modifications to display these automated messages to the users after a fixed interval of time.

Here is the code for the Twitch Bot using Twitch IO API in Python:

```from twitchio.ext import commands, routines
import random, sched, time 

class Bot(commands.Bot):
    def __init__(self):
       # Initialise our Bot with our access token, prefix and a list of channels to join on boot...
       super().__init__(token='oauth:a47vhfexb2e2roryfpoh01c51iax0o', prefix='!', initial_channels=['hypercoolness30'])

    async def event_ready(self):
        # We are logged in and ready to chat and use commands...
        print(f'Logged in as | {self.nick}')
        print(f'User id is | {self.user_id}')

    async def event_message(self, message):
            # Messages with echo set to True are messages sent by the bot...
            # For now we just want to ignore them...
            if message.echo:
                return

            # Print the contents of our message to console...
            print(message.content)

            # Since we have commands and are overriding the default `event_message`
            # We must let the bot know we want to handle and invoke our commands...
            await self.handle_commands(message)

    @commands.command()
    async def hello(self, ctx: commands.Context):
        # Send a hello back!
        print('Hello')
        await ctx.send(f'Hello {ctx.author.name}!')
    @commands.command()
    async def randomNum(self, ctx: commands.Context):
        num = random.randint(0, 10)
        print(num)
        #send a random number between 1-10
        await ctx.send(f'random #: {num}!')
    
    @routines.routine(seconds=10.0, iterations=5)
    async def remember(arg: str):
        print(f'Remember {arg}!')
        
    remember.start('to like and subscribe!')
```

[![Milestone 3](https://res.cloudinary.com/marcomontalbano/image/upload/v1656623081/video_to_markdown/images/youtube--K2IrG8-i3lM-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=K2IrG8-i3lM "Milestone 3"){:target="_blank" rel="noopener"}

# Second Milestone
For my second milestone, I added the twitch API for my twitch bot project and I made two modifications. One of them is if you type “!hello” which is a command in the twitch chat, the bot will respond back saying “Hello and the user’s name”. I used the API to call the functions ctx which puts the code into the twitch chat so the user can see it. The second modification I made was if the user types in “!randomNum” then the bot will spit out a random number between 1-10. I am also working on a third modification where every 15 minutes the bot will say “Remember to subscribe and like”.

[![Rahul's Second Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1656105469/video_to_markdown/images/youtube--VZ5WCXRN4-s-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=VZ5WCXRN4-s "Rahul's Second Milestone"){:target="_blank" rel="noopener"}

# First Milestone
My first milestone was to make a functioning Twitch bot. I first had to set up the Raspberry Pi for my project and download Python and the default version was 3.9.2.  I had to learn the features of the Pi. In order to make the twitch bot I had to look through two different guides and did some research to get a code that was functional. While doing this I was facing many problems with my code which I had to debug. I also had to update the Python version from 3.9.2 to 3.10.5 to make the code work. I later realized that my ouath ley was not working properly and decided to apply for a new one. And once I did that the bot started working.

[![Milestone 1](https://res.cloudinary.com/marcomontalbano/image/upload/v1655844344/video_to_markdown/images/youtube--RvDTBw8fGOY-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=RvDTBw8fGOY "Milestone 1"){:target="_blank" rel="noopener"}
