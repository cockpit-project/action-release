# GitHub release action


This composite action creates a GitHub release from a tag. The release artifact
tar is provided as an input, the release description is taken from the tag
commit message.

## How to use it

In your release workflow, build a release tar, then call this action:


```yaml
steps:
  - name: Build release
    run: make dist

  - name: Publish GitHub release
    # you can also use @SHA to guard against changing API
    uses: cockpit-project/action-release@main
    with:
      filename: "myproject-${{ github.ref_name }}.tar.xz"
```

Then push a tag like this:

```
123.4

- this new feature
- fix bug #123
```
