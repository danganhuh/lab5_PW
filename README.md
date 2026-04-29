# go2web

CLI utility for **HTTP over raw TCP sockets** (Lab 5).

## CLI

```bash
go2web -u <URL>         # make HTTP/HTTPS request and print readable response
go2web -s <search-term> # search term and print top 10 results
go2web -h               # show help
```

## Demo GIF

Add your gif file later (example: `docs/demo.gif`):

```md
![go2web demo](docs/demo.gif)
```

## Features Implemented

- Raw socket HTTP/HTTPS requests (no HTTP client libraries)
- URL parsing (`scheme`, `host`, `port`, `path`)
- HTTP response parsing (`status line`, `headers`, `body`)
- Redirect handling (`301`/`302`, up to 5 redirects)
- Content negotiation header:
  - `Accept: text/html, application/json`
- Content processing:
  - HTML -> strip tags, extract visible text
  - JSON -> pretty-print
- Search via DuckDuckGo HTML endpoint
- Search links normalized to direct destination URLs
- HTTP cache (file-based, 5-minute TTL)
- User-friendly error handling (invalid URL, DNS, timeout, refused connection, TLS issues)

## Output Formatting

- Clean readable text output
- Whitespace normalization
- Long-line limiting for readability
- Search links kept copy-friendly

## Run

From current folder:

```powershell
python go2web -h
python go2web -u "https://example.com"
python go2web -s "socket programming"
```

If you want plain `go2web` command in PowerShell, use `go2web.cmd` and add this folder to PATH:

```powershell
setx PATH "$env:PATH;C:\Users\user\Desktop\University\WP\lab5"
```

Then open a new terminal and run:

```powershell
go2web -h
```
