---
layout: site
title: Source Control
body_class: code
---

All source is stored within the [Senwes Azure DevOps](https://senwes.visualstudio.com/){:target="_blank"}.

Our culture around source code is one of Shared (or Collective) Code Ownership, this means that we are all, as a team, collectively responsible for our code. We all own the code and in principle any one of us can make changes anywhere. See [Our Charter](charter.html).

### Working with branches

The main branch is always regarded as deployable, following a green build. If the main branch is not deployable, it should be urgently fixed.

For any changes, always create a branch. The branching model we use is based on GitHub Flow[^1]. We branch from the develop branch, implement our changes on the branch and then merge the branch back down to the develop branch. The develop branch then merges into subsequent branches (i.e. qa, staging, main) aligned to environments.

Committing often is also a good practice. Every committed revision gives you a rollback position, and makes it easier for you step back through changes locally[^2].

Before merging a branch, always raise a pull request, and make sure your changes have been reviewed by others. This must be enforced by Github branch protection.

Once your branch is merged into the destination branch, the branch will be automatically deleted via GitHub’s branch policy.

### Commit Messages

While working on a branch, commits provide rollback positions and commit messages reflect this. When merging, the commit message becomes part of the destination branch’s commit log.

The content of the commit message at that point can help with things like release tracking and linking or even automatically closing JIRA issues.

It is therefore very important that we write good commit messages[^3], following these simple guidelines:

```
Summarize changes in around 50 characters or less.

Include the issue tracker ticket number (followed by a colon) at the beginning of the summary line e.g. `123:`. Use the imperative mood, explain what applying the commit will do, not what you did. i.e. "Fix bug XYZ".

More detailed explanatory text, if necessary. Wrap it to 72
characters (this is because git log adds a padding of 4 blank spaces) when it formats messages.

In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequenses of this
change? This is the place to explain them.

Further paragraphs come after blank lines.

 * Bullet points are okay, too

 * We should use an asterisk for the bullet, preceded
   by a single space, with blank lines in between.

```

The wrapping of text at 50 characters for the Summary line and 72 characters for the body is very important, and is explained here[^4].

[^1]: [GitHub Flow](https://guides.github.com/introduction/flow/){:target="_blank"}
[^2]: [Commit Often, Perfect Later, Publish Once](https://sethrobertson.github.io/GitBestPractices/){:target="_blank"}
[^3]: [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/){:target="_blank"}
[^4]: [Whats with the 50/72 Rule](https://www.midori-global.com/blog/2018/04/02/git-50-72-rule){:target="_blank"}