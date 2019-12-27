# fs-tree-common

[![Build Status](https://travis-ci.com/skye2k2/fs-tree-common.svg?branch=master)](https://travis-ci.com/skye2k2/fs-tree-common)

Common configuration snippets for use with Travis CI builds. This allows us to manage 70+ Travis CI .yml files without making direct modifications to each repository every time.

> Living in Clif's world, for now, since the org has disallowed creation of open-source repositories.

# Usage

In your repository, add the following to your `.travis.yml`:

```
version: ~> 1.0

# This Travis CI configuration makes use of imports to commonize and simplify build configuration. Utilizes shallow merge, allowing overwrites for all root level sections. See fs-webdev/fs-tree-common for more detail.
import:
  - source: fs-webdev/fs-tree-common:base.yml
    mode: merge
  - source: fs-webdev/fs-tree-common:sauce.yml
    mode: merge
  - source: fs-webdev/fs-tree-common:notifications.yml
    mode: merge
  - source: fs-webdev/fs-tree-common:before.yml
    mode: merge
  - source: fs-webdev/fs-tree-common:install_with_bower.yml
    mode: merge
  - source: fs-webdev/fs-tree-common:scripts.yml
    mode: merge
```

Add which team's channel to notify about builds (note the deep merge). Example:

```
  - source: fs-webdev/fs-tree-common:notifications_tw-gold.yml
    mode: deep_merge
```


And then put anything additional you wish to have happen before running tests in an `install` section.

If you need specific build script steps, simply add an entry for it, and it will override the default.

### Updating

If you need to update a Slack notification channel, run the following:

```
travis encrypt SLACK_ACCOUNT:SLACK_TOKEN#CHANNEL --add notifications.slack.rooms
```

and then move the resulting string that was placed in the root `.travis.yml` to its proper desitnation.
