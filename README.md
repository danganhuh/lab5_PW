# go2web

Python CLI for the web programming tasks.

## Task 1 CLI interface

Supported commands:

- `go2web -h` show help
- `go2web -u <URL>` call URL/HTTP handler
- `go2web -s <search-term>` call search handler

Validation:

- Missing value after `-u` -> error
- Missing value after `-s` -> error
- Using `-u` and `-s` together -> error

## Run on Windows

- `python go2web -h`
- `go2web -h` (via `go2web.cmd` in this folder)

To run `go2web` from any folder, add this directory to your PATH:

```powershell
setx PATH "$env:PATH;C:\Users\user\Desktop\University\WP\lab5"
```
