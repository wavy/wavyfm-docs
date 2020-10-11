Thanks for your interest in contributing to the wavy.fm docs! Here's some instructions to get started.

# Accepted Contributions

- Participate to design discussion in the GitHub issues.
- Open pull-requests to fix typos, inaccuracies, and confusing wording.
- Open pull-requests to fill gaps in our documentation.

## Design Discussions

Design discussions take place in GitHub issues.

We also have a private wavy.fm **Developer Working Group** with a Discord channel.
If you're interested in being part of the Working Group, email us at `contact@wavy.fm`
with some info about your project(s).

- Before opening a pull-request with your suggested changes to the wavy.fm API, please open an issue on GitHub
  describing your use-case.

- Open one issue per use-case. Try to be as descriptive as possible:
  - Describe what the use-case is.
  - If possible, suggest the semantics of the new endpoints, or the ones you'd like to see enhanced.
  - If applicable, give examples of this use-case in similar projects and APIs.

## Pull-Requests

- Pull-requests are open to everyone for fixing typos and making the documentation clearer.
- If there are gaps in our documentation, feel free to open a pull-request.
  However, we'd prefer you open an issue first.
- Once a use-case has been reviewed and approved in its GitHub issue, the wavy.fm staff or Developer Working Group
  will prepare a pull-request with the new API documentation. Reviewing the pull-request is open to anyone, but
  wavy.fm staff will give the final approval.

# Repository Guidelines

The documentation is composed of Markdown files ("pages") categorized in "chapters". The list of chapters and pages
are defined in the `index.json` file at the root of the repository.

All Markdown documents go through a spell-checker when you open a pull-request.
We use [`mdspell`](https://www.npmjs.com/package/markdown-spellcheck) to run the check:

```
npm install -g markdown-spellcheck
mdspell **/*.md -n --en-us
```

We use American English throughout the documentation.

Do not use `h1` tags (`#` in Markdown). This tag is reserved for the title as displayed on the wavy.fm website.
