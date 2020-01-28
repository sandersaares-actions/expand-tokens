Replaces `__tokens__` with values from environment variables.

# Example workflow

```yaml
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - uses: sandersaares-actions/expand-tokens@master
      env:
        versionstring: 1.2.3.4
        best_day_of_week: friday
        secret_ingredient: ${{ secrets.secret_ingredient }}
      with:
        path: src
        recursive: true
```

Example file to perform replacement in:

```
In version __versionstring__ the best day of the week was __best_day_of_week__. The secret ingredient is __secret_ingredient__.
```

# Mandatory parameters

`path` is path to the file or directory to process.

# Optional parameters

`filenames` specifies a filename filter to limit files to process (e.g. `*.txt;*.cs;*.c`).

`recursive` enables recursive processing of the directory specified in `path`. Has no effect if the path points to a file.