# slack_redmine_unfurl_bolt
unfurl private redmine link for slack using bolt python

#slack #redmine #slackeventsapi #unfurl #html2text #bolt

## Installation

### Create Slack App

https://api.slack.com/apps/

#### Initial Parameters
```
{
    "display_information": {
        "name": "Redmine unfurler"
    },
    "settings": {
        "org_deploy_enabled": false,
        "socket_mode_enabled": true,
        "is_hosted": false,
        "token_rotation_enabled": false
    }
}
```

#### OAuth & Permissions

In `Bot Token Scopes` Add

- chat:write
- links:read
- links:write
- users:read.email

#### Event Subscriptions

Check `Enable Events` On

In `Subscribe to bot events`, Add link_shared

### Docker setup

- clone from https://github.com/floyd68/slack_redmine_unfurl_bolt_docker.git
- build with docker
 ```
 docer build -t slack_unfurler:v1 .
 ```
- run image with params
 ```
 docker run -d --name slack_redmine_unfurler \
     -e REDMINE_URL=http://your_redmine_url \
     -e REDMINE_API_KEY=readmine api key from http://redmine_url/my/account \
     -e SLACK_BOT_TOKEN=xoxb-xxxxxx... \
     -e SLACK_APP_TOKEN=xapp-1-xxxxx... \
     slack_unfurler:v1
 ```