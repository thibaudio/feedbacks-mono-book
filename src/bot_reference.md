# Bot Reference

## Owner commands
Commands that can only be run by the discord server admin.  

### /init
Initialize BugBee and **Backend Channel** on your server, in the channel where the command was issued.  
This channel will be the channel where users reports will be forwarded.

### /add_game <game_name>
game_name: The name of the game you want to create a **Frontend Channel** for.

Create a **Frontend Channel** for a specific game, in the channel where the command was issued.  
This channel will be the channel where users will be able to create reports for the specific game.

### /add_endpoint_integration <shared_code>
shared_code: A shared_code required in the API calls  
returns: The `game_id`, required in the API calls

Create an endpoint integration for the specifig **Frontend Channel** where the command was issued.  
It enable users to submit reports via the API. More details in [API Reference](api_reference.md).

### /remove_endpoint_integration
Remove the endpoint integration for the specifig **Frontend Channel** where the command was issued.  
Users will not be able to submit reports via the API anymore. 

### /unregister_game_channel
Remove the **Frontend Channel** from the channel where the command was issued.  
Users will not be able to submit report from this channel anymore.

### /remove_bugbee
Un-initialize BugBee, clearing the database of all your data.

## Users commands
### /bee <report_type> <description> <attachement>
report_type: The type of report, can be Bug or Feedback
description: The content of the report
attachment (Optional): An optional attachment, like a screenshot

Create a report with an optional attachment

### /bug <description> <attachment>
description: The content of the report
attachment (Optional): An optional attachment, like a screenshot

Create a Bug report with an optional attachment

### /feedback <description> <attachment>
description: The content of the report
attachment (Optional): An optional attachment, like a screenshot

Create a Feedback report with an optional attachment
