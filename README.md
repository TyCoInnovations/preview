# Preview

[![ShellCheck](https://github.com/TyCoInnovations/preview/actions/workflows/shellcheck.yml/badge.svg)](https://github.com/TyCoInnovations/preview/actions/workflows/shellcheck.yml)

A small script to spin up a local static file server (via [http-server](https://www.npmjs.com/package/http-server)) for quick previews.

## Usage

```sh
./preview.sh                             # interactive prompt for port
./preview.sh 3000                        # serve on port 3000, no prompt
./preview.sh 3000 -d ./dist -o           # serve ./dist on port 3000 and open a browser
./preview.sh --https --cert c.pem --key k.pem
./preview.sh -h                          # show help
```

## Options

| Flag              | Description                                              |
| ----------------- | ---------------------------------------------------------- |
| `port`            | Port to serve on (1-65535). Prompted for if omitted.       |
| `-d, --dir DIR`   | Directory to serve. Defaults to the current directory, or the last one used. |
| `-o, --open`      | Open the preview in a browser automatically.                |
| `-q, --quiet`     | Skip the banner.                                            |
| `--no-auto-port`  | Fail instead of trying the next port when the chosen one is busy. |
| `--https`         | Serve over HTTPS. Requires `--cert` and `--key`.             |
| `--cert PATH`     | Path to a TLS certificate (used with `--https`).             |
| `--key PATH`      | Path to a TLS private key (used with `--https`).             |
| `-h, --help`      | Show help and exit.                                          |
| `-v, --version`   | Show version and exit.                                       |
| `-- ...`           | Anything after `--` is passed through to `http-server`.      |

You can also set the `PREVIEW_PORT` environment variable to choose a default port without being prompted.

Port and directory choices are remembered in `~/.previewrc` and offered as defaults next time.

Requires Node.js (for `npx`).
