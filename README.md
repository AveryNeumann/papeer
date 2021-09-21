```
❯ papeer get --format epub --recursive --delay 500 --limit 10 https://news.ycombinator.com/
   6s [===============================================>--------------------]  70% Status: 7 out of 10 chapters
   0s [====================================================================] 100% 1. Three ex-US intelligence officers admit hacking for UAE
   0s [====================================================================] 100% 2. Show HN: Time Travel Debugger
   0s [====================================================================] 100% 3. How much faster is Java 17?
   0s [====================================================================] 100% 4. The First Webcam Was Invented to Keep an Eye on a Coffee Pot
   0s [====================================================================] 100% 5. Nikon's 2021 Photomicrography Competition Winners
   0s [====================================================================] 100% 6. HTTP Status 418 – I'm a teapot
   0s [====================================================================] 100% 7. H3: Hexagonal hierarchical geospatial indexing system
  --- [--------------------------------------------------------------------]   0% 8. Automatic cipher suite ordering in Go’s crypto/tls
  --- [--------------------------------------------------------------------]   0% 9. Find engineering roles at over 800 YC-funded startups
  --- [--------------------------------------------------------------------]   0% 10. Futarchy: Robin Hanson on prediction markets
Ebook saved to "Hacker_News.epub"
```

# Installation

## From source

```sh
go get -u github.com/lapwat/papeer
```

## From binary

### On Linux / MacOS

```sh
platform=linux
# platform=darwin for MacOS
curl -L https://github.com/lapwat/papeer/releases/download/v0.1.0/papeer-v0.1.0-$platform-amd64 > papeer
chmod +x papeer
sudo mv papeer /usr/local/bin
```

### On Windows

Download [latest release](https://github.com/lapwat/papeer/releases/download/v0.1.0/papeer-v0.1.0-windows-amd64.exe).

## Install kindlegen to export websites to MOBI (optional)

```sh
TMPDIR=$(mktemp -d -t papeer-XXXXX)
curl -L https://github.com/lapwat/papeer/releases/download/kindlegen/kindlegen_linux_2.6_i386_v2_9.tar.gz > $TMPDIR/kindlegen.tar.gz
tar xzvf $TMPDIR/kindlegen.tar.gz -C $TMPDIR
chmod +x $TMPDIR/kindlegen
sudo mv $TMPDIR/kindlegen /usr/local/bin
rm -rf $TMPDIR
```

# Usage

```
Browse the web in the eink era

Usage:
  papeer [flags]
  papeer [command]

Available Commands:
  completion  generate the autocompletion script for the specified shell
  get         Scrape URL content
  help        Help about any command
  ls          Print table of content
  version     Print the version number of papeer

Flags:
  -d, --delay int         time to wait before downloading next chapter, in milliseconds (default -1)
  -f, --format string     file format [md, epub, mobi] (default "md")
  -h, --help              help for papeer
  -i, --include           include URL as first chapter, in resursive mode
  -l, --limit int         limit number of chapters, in recursive mode (default -1)
  -o, --output string     output file
  -q, --quiet             do not show logs
  -r, --recursive         create one chapter per natigation item
  -s, --selector string   table of content CSS selector
      --stdout            print to standard output

Use "papeer [command] --help" for more information about a command.
```

# Autocompletion

Execute this command in your current shell, or add it to your `.bashrc`.

```sh
. <(papeer completion bash)
```

Type `papeer completion bash -h` for more information.

You can replace `bash` by your own shell (zsh, fish or powershell).

# Dependencies

- `cobra` command line interface
- `go-readability` extract content from HTML
- `html-to-markdown` convert HTML to Markdown
- `go-epub` convert HTML to EPUB
- `colly` query HTML trees
- `uiprogress` display progress bars
