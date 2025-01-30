# Getting Started

## Add BugBee to your server
1. Click on the following link to add {{name}} to your game or company discord:  
[Invite BugBee to your server](https://discord.com/oauth2/authorize?client_id=1150747928885989376)
2. Create a private channel, we'll call it the **Backend Channel**, and give access to people reviewing user reports as well as {{name}}
3. Initialize {{name}} by typing `/init` in the **Backend Channel**

## Add a Frontend Channel for a game
To register a channel where users can report feedback and bugs, create a dedicated **Frontend Channel**, and register it by typing: `/add_game <your game name>`

## Add an Endpoint integration
To enable in-game reporting, you need to add an endpoint integration.
Go to the dedicated **Frontend Channel** for your game, then type `/add_endpoint_integration <shared_code>`, where the `shared_code` is a string of your choosing.
The bot will reply with your game's id. Note down your `shared_code` and your `game_id` for later.

You can now send report from you game to Bugbee's api. Please refer to the [API Reference](api_reference.md) for more details.

## How can I get some support
Join us on {{discord}} to get support, leave a feedback, report a bug, or ask for a new feature!
