# go2web

Python CLI for the web programming tasks.

## Task 3 TCP Socket layer

`-u <URL>` now uses raw TCP sockets (no HTTP libraries):

- opens TCP socket to `host:port`
- sends manual HTTP/1.1 request:
  - `GET /path HTTP/1.1`
  - `Host: ...`
  - `Connection: close`
- receives full response with looped `recv(4096)` until socket closes
- parses headers/body and decodes chunked transfer encoding when present

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
