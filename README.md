## Sample Screenshot

<img width="580" alt="スクリーンショット 2022-12-12 15 13 07" src="https://user-images.githubusercontent.com/27538852/206983861-ef5ceab5-7563-49b2-96c1-a703fbeddc2e.png">

Slack icon and app name depends on your slack bot.  
This action does not have any slack bot settings by default.

## Usage

### Basic

Just create file and copy & paste in your repository!

```yml
name: GitHub Discussions Notifier

on:
  discussion:
    types: [created]
  discussion_comment:
    types: [created]
    
jobs:
  notify-github-discussions:
    runs-on: ubuntu-latest
    steps:
      - uses: ry023/github-discussions-webhook-notifier@main
        with:
          SLACK_INCOMMING_WEBHOOK_URL: <your slack incomming webhook url>
```

### Optional

```yml
name: GitHub Discussions Notifier

on:
  discussion:
    types: [created]
  discussion_comment:
    types: [created]
    
jobs:
  notify-github-discussions:
    runs-on: ubuntu-latest
    steps:
      - uses: ry023/github-discussions-webhook-notifier@main
        with:
          SLACK_INCOMMING_WEBHOOK_URL: <your slack incomming webhook url>
          send-discussion-create: true
          send-discussion-comment: false
```

## Inputs

See [action.yml](action.yml)

| Name | Description | Default | Required |
| - | - | - | - |
| `SLACK_INCOMMING_WEBHOOK_URL` | your slack incomming webhook url | - | yes |
| `send-discussion-create` | send discussion create notification? | true | no |
| `send-discussion-comment` | send discussion comment notification? | true | no |
| `unfurl-links` | Pass true to enable unfurling of primarily text-based content | false | no |
| `unfurl-media` | Pass false to disable unfurling of media content | false | no |

## Supported

### Events

- `discussion: types: [created]`
- `discussion_comment: types: [created]`

## Dependencies

- [actions/cache](https://github.com/actions/cache) >= 3.0.0
- [GitHub CLI](https://cli.github.com/) >= 2.6.0
