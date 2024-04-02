# Comment PR

There are other GitHub Actions doing the same thing, yet their usage seemed so
complicated to me and I wanted something simple and consistent.

The objective of this GitHub Action is as follows:

- Have a unique identifier for the comment to avoid duplicates.
- On subsequent runs, remove the old comment and add another of the exact same
one just to get notified by email from the GitHub notification system.

## Usage

```yaml
jobs:
  build:
    permissions:
      pull-requests: write # this is necessary
    runs-on: ubuntu-latest
    steps:
# ... truncated ...
      - name: Comment PR
        uses: meysam81/comment-pr@main
        with:
          # `title` and `content` support markdown
          title: "# Custom title" # ensures idempotency through a unique identifier
          content: |
            My content goes here
          token: ${{ secrets.GITHUB_TOKEN }} # this is required
```
