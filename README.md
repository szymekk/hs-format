# hs-format

`hs-format` is a tool used to automate running `ormolu`, a Haskell source formatter, on files inside a git repository.
It searches for Haskell files and detects those in need of formatting.
Found files are formatted with `ormolu`.
`hs-format` respects .gitignore rules and skips ignored files.
