# Comment PR

<!-- START doctoc -->
<!-- END doctoc -->

Tired of complex PR comment actions?

Comment PR provides a straightforward solution for adding and updating
comments on Pull Requests.

## Features

- [x] ✨ **Unique Identifiers**: Automatically prevents duplicate comments
- [x] 🔄 **Smart Updates**: Removes old comments and adds new ones to trigger notifications
- [x] 📝 **Markdown Support**: Full markdown capabilities for both title and content
- [x] 🎯 **Minimal Configuration**: Simple YAML setup with just three required fields

## Why Choose Comment PR?

- [x] **Simplicity First**: Designed for developers who want a no-nonsense solution
- [x] **Consistent Behavior**: Predictable outcomes across all your workflows
- [x] **Notification Friendly**: Updates trigger GitHub notifications to keep your team informed

Perfect for CI/CD pipelines, automated reviews, and status updates on your Pull Requests.

## Yet Another GH Action?

There are other GitHub Actions doing the same thing, yet their usage seemed so
complicated to me and I wanted something simple and consistent.

The objective of this GitHub Action is as follows:

- Have a unique identifier for the comment to avoid duplicates.
- On subsequent runs, remove the old comment and add another of the exact same
one just to get notified by email from the GitHub notification system.

## Usage

```yaml
jobs:
  comment-pr:
    permissions:
      pull-requests: write # this is necessary
    runs-on: ubuntu-latest
    steps:
      - name: Comment PR
        uses: meysam81/comment-pr@v1
        with:
          # `title` and `content` support markdown
          title: "# Custom title" # ensures idempotency through a unique identifier
          content: |
            My content goes here
          token: ${{ secrets.GITHUB_TOKEN }} # this is required
```
