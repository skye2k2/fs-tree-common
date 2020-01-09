# fs-tree-common/travis

Common configuration snippets for use with Travis CI builds. This allows us to manage 70+ Travis CI .yml files without making direct modifications to each repository every time.

# Usage

In your repository, add the following to your `.travis.yml`:

```
version: ~> 1.0

# This Travis CI configuration makes use of imports (https://docs.travis-ci.com/user/build-config-imports/) to commonize and simplify build configuration. Utilizes shallow merge, allowing overwrites for most root level sections, and deep merge for notifications.
import:
  - source: skye2k2/fs-tree-common:travis/base.yml
    mode: merge
  - source: skye2k2/fs-tree-common:travis/sauce.yml
    mode: merge
  - source: skye2k2/fs-tree-common:travis/notifications.yml
    mode: merge
  - source: skye2k2/fs-tree-common:travis/before.yml
    mode: merge
  - source: skye2k2/fs-tree-common:travis/install_with_bower.yml
    mode: merge
  - source: skye2k2/fs-tree-common:travis/scripts.yml
    mode: merge
```

And then put anything additional you wish to have happen before running tests in an `install` section.

If you need specific build script steps, simply add an entry for it, and it will override the default.
