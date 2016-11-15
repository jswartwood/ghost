...currently this project is just a clone of Showoff, but will eventually incorporate additional features, tweak some assumptions for existing functionality, etc.

# Showoff (aka Gunsmith Bot)

Showoff is a slack bot based on the [hubot](https://hubot.github.com/) framework, designed to make it easy for users to show off their Destiny weapons in slack. The goal is to enable users to share weapon information with as few inputs as possible.  
This project was based heavily off of [slack-destiny-bot](https://github.com/cprater/slack-destiny-bot) which served as an outstanding basis for me to implement my own functionality.

### Usage

Showoff only requires at most 3 inputs, directed at the bot (order does matter):  
* XBL/PSN gamertag
* console network ("xbox" or "playstation")
* weapon slot ("primary", "special", "heavy").  

The standard usage looks like this:  
>@bot-name MyGamertag xbox primary  

with a response looking like (active nodes in bold):  
![image](https://cloud.githubusercontent.com/assets/11082871/14224924/604e45aa-f87c-11e5-9dbd-0c81fe46938c.png)  
Showoff automatically looks at **your most recently played character** when grabbing the weapon data.

### Advanced Options
If your slack profile's **first name** (not username) matches your gamertag, you can omit this entirely.  
>@bot-name xbox special  

If you don't include a console network, showoff will automatically search both.
>@bot-name MyGamertag heavy

Note that if the gamertag exists on both networks, this will not work.  

Combining these options, the bot will pull your slack first name, and search both networks for the specified weapon with a single input.
>@bot-name primary

### Testing it out
If you want to test out the bot before using it in a public channel, try sending it a direct message. You do not need "@bot-name" when you are messaging the bot directly, just the inputs.

### Caveats
* Xbox users must use an underscore ( _ ) for any spaces in their gamertag when inputting it directly. This is not necessary in the first name field of your slack profile; spaces will work fine.
* As stated above, Showoff automatically looks at your most recently played character. This was ultimately an intentional decision to limit the number of inputs needed and simplify using the bot.

### Setting up the bot in your own slack
First clone the repo locally:
> git clone git@github.com:phillipspc/showoff.git

To deploy to heroku, cd into the newly created folder then follow the steps [here](https://github.com/slackhq/hubot-slack) under "Deploying to Heroku" (minus the part about creating a local hubot).  
You'll also need to add your [Bungie Api Key](https://www.bungie.net/en-US/User/API) to the config variables:
> heroku config:set BUNGIE_API_KEY=your-key-here
