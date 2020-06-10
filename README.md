# hs-format

`hs-format` is a tool used to automate running `ormolu`, a Haskell source formatter, on files inside a git repository.
It searches for Haskell files and detects those in need of formatting.
Found files are formatted with `ormolu`.
`hs-format` respects .gitignore rules and skips ignored files.

## Usage

Call `hs-format` inside a git repo to format all unformatted Haskell source files in the current directory which are not ignored by git.

```console
$ hs-format
```

You can specify the path to an `ormolu` executable using the `--with-ormolu` flag.

```console
$ hs-format --with-ormolu /path/to/ormolu
```

Use the `--check` option to detect unformatted files.

```console
$ hs-format --check
needs formatting: 'bad.hs'
needs formatting: 'dir/bad_2.hs'
$ hs-format
$ hs-format --check
```

Add the `--print-modified` switch to display all formatted files.

```console
$ hs-format --check
needs formatting: 'bad.hs'
needs formatting: 'dir/bad_2.hs'
$ hs-format --print-modified
applying formatting: 'bad.hs'
applying formatting: 'dir/bad_2.hs'
$ hs-format --check
```

Use `--force` to format all files without detecting those in need of formatting.

```console
$ hs-format --check
needs formatting: 'bad.hs'
needs formatting: 'dir/bad_2.hs'
$ hs-format --force --print-modified
applying formatting: 'bad.hs
applying formatting: 'dir/bad_2.hs'
applying formatting: 'good.hs'
applying formatting: 'dir/good_2.hs'
$ hs-format --check
```
