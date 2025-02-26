---
id: svn
title: Svn
sidebar_label: Svn
---

## What

Display svn information when in a svn repository. Also works for subfolders. For maximum compatibility,
make sure your `svn` executable is up-to-date (when branch or status information is incorrect for example).

Local changes can also be displayed which uses the following syntax:

- `+` added
- `!` conflicted
- `-` deleted
- `~` modified
- `>` moved
- `?` untracked

## Sample Configuration

```json
{
  "type": "svn",
  "style": "powerline",
  "powerline_symbol": "\uE0B0",
  "foreground": "#193549",
  "background": "#ffeb3b",
  "properties": {
    "fetch_status": true,
    "fetch_stash_count": true,
    "fetch_upstream_icon": true,
    "template": " \ue0a0{{ .Branch }} r{{ .BaseRev }} {{ .Working.String }} "
  }
}
```

## Properties

### Fetching information

As doing multiple svn calls can slow down the prompt experience, we do not fetch information by default.
You can set the following properties to `true` to enable fetching additional information (and populate the template).

- fetch_status: `boolean` - fetch the local changes - defaults to `false`

## Template ([info][templates])

:::note default template

``` template
 \ue0a0{{.Branch}} r{{.BaseRev}} {{.Working.String}}
```

:::

### Properties

- `.Working`: `SvnStatus` - changes in the worktree (see below)
- `.Branch`: `string` - current branch (releative URL reported by `svn info`)
- `.BaseRev`: `int` - the currently checked out revision number

### SvnStatus

- `.Untracked`: `int` - number of untracked files
- `.Deleted`: `int` - number of deleted files
- `.Added`: `int` - number of added files
- `.Tracked`: `int` - number of changed tracked files
- `.Conflicted`: `int` - number of changed tracked files with conflicts
- `.Changed`: `boolean` - if the status contains changes or not
- `.HasConflicts`: `boolean` - if the status contains conflicts or not
- `.String`: `string` - a string representation of the changes above

[templates]: /docs/config-templates
[hyperlinks]: /docs/config-templates#helper-functions
