# TheFuck

> A script to tell you what your latest error message means.

You know when you're hacking away, having a great time, and then you run into an error you don't recognize? With this tool you can simply run `thefuck` right after the error message, and an LLM with process your query, your previous command, and the files in the current directory to give you some guidence on how to fix the error!

> [!WARNING]
> This tool is very new, very unstable, and likely to break. I've taken steps to ensure the LLM can't access anything it should, but there's a solid chance that I'm missed something. Use with caution.

## Install

With `curl`:

```shell
curl https://github.com/johnnymatthews/thefuck/blob/latest-stable/install.sh | sh -
```

Or `wget`, if you're a heathen:

```shell
wget -qO- https://github.com/johnnymatthews/thefuck/blob/latest-stable/install.sh | sh -
```

## Configuration

### Limit history

You can limit the amount of history that `thefuck` can use with the `limit-history` tag or configuration option. The value represents X number of previous commands that `thefuck` can access.

**Config file**:

```yaml
---
limit-history: 30
```

**Runtime option**:

```shell
thefuck --limit-history=30
```

### Include local files

You can tell `thefuck` to take the files within the current directory into account when handing data over to the LLM. `thefuck` only takes files from the current directory into account.

> [!TIP]
> I intend to allow `thefuck` to search through the current directory _and down_, giving the LLM access to the files and folders further down the directory listing. This, however, comes with some security implications that need to be worked around.


**Config file**:

```yaml
---
include-local-files: true
```

**Runtime option**:

```shell
thefuck --include-local-files
```
