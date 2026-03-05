# Notify Slack Action

A minimal GitHub composite action that sends a Slack notification when a CI job fails.

Uses [`slackapi/slack-github-action@`](https://github.com/slackapi/slack-github-action) under the hood with an incoming webhook.

## Setup

1. Create a Slack App at [api.slack.com/apps](https://api.slack.com/apps)
2. Enable **Incoming Webhooks** and add one for your target channel
3. Store the webhook URL as a GitHub repo secret (e.g., `SLACK_WEBHOOK_URL`)

## Usage

```yaml
- name: Notify Slack on failure
  if: failure()
  uses: deepset-ai/notify-slack-action@v1
  with:
    slack-webhook-url: ${{ secrets.SLACK_WEBHOOK_URL }}
```

### Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `slack-webhook-url` | Yes | - | Slack Incoming Webhook URL |
| `mention-here` | No | `"true"` | Whether to include `@here` in the notification |

### Message format

The notification includes:
- Repository name, workflow name, and branch
- `@here` mention (configurable)
- Link to the failed workflow run

## License

Apache 2.0
