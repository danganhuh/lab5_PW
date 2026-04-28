# go2web

Python CLI base for Task 0.

## Includes required capabilities

- TCP sockets (`--tcp-check HOST:PORT`)
- CLI argument parsing (`argparse`)
- HTML parsing (`html.parser` title extraction)

## Run

```sh
python go2web --help
python go2web https://example.com
python go2web --tcp-check example.com:80
```

On Unix-like systems, it can also run as:

```sh
./go2web --help
```
