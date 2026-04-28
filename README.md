# go2web

Python CLI for the web programming tasks.

## Task 3 TCP Socket layer

`-u <URL>` now uses raw sockets (no HTTP libraries):

- supports both `http://` and `https://`
- opens TCP socket to `host:port`
- wraps socket with TLS for `https://`
- sends manual HTTP/1.1 request:
  - `GET /path HTTP/1.1`
  - `Host: ...`
  - `Connection: close`
- receives full response with looped `recv(4096)` until socket closes
- parses headers/body and decodes chunked transfer encoding when present

## Task 4 HTTP response parser

Raw response is split into:

- status line
- headers
- body

Extracted fields:

- status code
- content-type
- location (redirect header)

## Task 5 redirect handling

- detects `301` and `302`
- extracts `Location` header
- automatically follows redirects
- limit: 5 redirects (loop protection)

## Task 6 content processing

- if `Content-Type` is `text/html`:
  - strips HTML tags
  - extracts visible text
- if `Content-Type` is JSON:
  - pretty-prints JSON

## Task 9 HTTP cache

- cache key: request URL
- cache value: final response (status, headers, body, final URL)
- storage: file-based (`.go2web_cache.json`)
- expiration: 5 minutes
- cache checked before network request for both `-u` and `-s`

## Search engine

- `-s` now uses DuckDuckGo (`https://duckduckgo.com/html/?q=...`)
- search results are normalized to direct target links (no DuckDuckGo redirect wrapper)

## Task 10 content negotiation

- request header includes:
  - `Accept: text/html, application/json`
- response handling:
  - HTML (`text/html`) -> strips tags and prints readable text
  - JSON (`application/json`) -> pretty-prints JSON

## Task 11 output formatting

- trims and normalizes whitespace
- limits long lines for readability
- keeps result links fully copyable

## Task 12 error handling

- user-friendly errors for:
  - invalid URL
  - DNS lookup failure
  - connection refused
  - timeout
  - TLS/SSL handshake problems

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
