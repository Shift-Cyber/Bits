# Bits
Humanoid Discord bot with too much power and a bit of an attitude...
![SCYCA Logo](.rsrc/git-banner.png)

## Overview
This is the main development repository for the Bits discord bot. Bits is the main bot in production for Shift Cyber's Hack-a-Bit Capture the Flag (CTF) competition. Please submit pulls to add additional features if you have cool ideas. We are always accepting new volunteers to help with open-source maintenance. If you have found a vulnerability, please consider responsible disclosure via our main contact contact@shiftcyber.com. If you would like to implement our public key in a third party service please reach out and request that--we will be happy to provide it upon request. **Do not submit pull requests related to like vulnerabilities in the software suite.** We will credit you on the repository if you have a hand in development or security. Thanks for checking out the Bot, hope to see you participating in a competition in the future or volunteering to help us inspire the next generation of security experts.

## Requirements
Bits is implemented via Discord's developer API which you can find via Google search, or at the following URL: https://discord.com/developers/docs/intro and permissions checks for commands are implemented via Python decorators which wrap Discord API calls. As this tool implements decorators and some modern format strings declerations, you will require a somewhat modern version of Python3. Bits was tested with against Python 3.9.10. This tool also requires specific libraries which are listed in the requirements file: [requirements.txt](requirements.txt).

## Repository Breakout
```
├── scripts     - Setup, purge and all maintenance scripts live here
└── src         - Main location for all bot source, including run.py
    └── stubs   - Code snippets for short repetative tasks
```

## Install Guide
At a primative level the bot can be run by executing [src/run.py](src/run.py) with context arguements for configuration and logging. In a more stable long-term environment, the bot can be managed with system control. The setup script in [scripts/setup.sh](scripts/setup.sh) will build a service account and setup the daemon to run with the appoperiate permissions. It will also set the proper permissions on /opt and /etc locations so that if the bot is compromised, the impact of the exploit is mitigated to a (hopefully) sufficient degree.

Installation steps (Verified stable on Kali 2021.4)
1. Execute scripts/setup.sh to build the bot into your local Linux environment
2. Setup a discord developer account to obtain a bot token. The following is a good guide for doing this: https://www.youtube.com/watch?v=ibtXXoMxaho
3. Start the bot if not already started. It will crash due to not having a token but will populate the empty config file.
4. Set the bot token in /etc/config/bits/config.yaml
5. Restart the bot using sytemctl, if the configuration was taken and the bot was restarted succesfully, you should see a log of success in /var/log/bits/bits.log as well as a number of Discord API calls.

### Scripts
```
bash scripts/setup.sh
bash scripts/purge.sh
```

### Service Control
```
sudo systemctl status bits
sudo systemctl start bits
sudo systemctl stop bits
sudo systemctl restart bits
sudo systemctl enable bits
sudo systemctl disable bits
```


## Contributors and Contact
### [Nate Singer](discord://discordapp.com/users/523958300396748810)
Nate Singer is the founding director and president of Shift Cyber and is the primary point of contact for this bot. He is resposible for most of the staging code and the framework for the bot. Therefor if there are questions related to environment or complxities in that arean, he should be the primary point of contact.


### [Darian Arnold](discord://discordapp.com/users/277500700496363521)
Darian Arnold is a lead developer and the infrastructure management supervisor during Hack a Bit Competition. He has had a major hand in development of the bot and can take any questions related to bot setup, execution and development. Specifically he has done substnatial work on bot commands and therefor is the primary contact for that aspect of the bot.

## Configuration options
```
bot_settings:
  discord_token:        - Discord bot token obtained during step two of setup
log_level:              - Log verbosity, https://docs.python.org/3/howto/logging.html
```
