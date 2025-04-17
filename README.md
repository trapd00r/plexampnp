# plexampnp

A Perl script to display now playing information from Plexamp in your terminal.

## Features

- Display now playing information from Plexamp
- Show album cover art in terminal
- Colorized output
- Progress information (time elapsed/remaining)
- Filter by user and media type
- List all active Plexamp clients
- XDG_CONFIG_HOME compliant configuration

## Installation

### Manual Installation

```bash
git clone https://github.com/trapd00r/plexampnp.git
cd plexampnp
perl Makefile.PL
make
make install
```

## Dependencies

- Getopt::Long
- XML::Simple
- LWP::Simple
- Data::Dumper
- Term::ExtendedColor
- JSON
- Config::Tiny
- File::HomeDir
- Time::Piece
- Time::Seconds
- File::Temp
- IPC::Run

For cover art display (optional):
- chafa (preferred)
- viu (alternative)

## Configuration

The configuration file is located at `$XDG_CONFIG_HOME/plexampnp/config` (defaults to `~/.config/plexampnp/config`).

Example configuration:
```ini
[plex]
host = 192.168.1.34
port = 32400
session_path = /status/sessions

[plexamp]
host = 192.168.1.12

[colors]
artist = 148
title = 142
album = 107
year = 111
file = 255
time = 33

[filters]
music_only = 1
user =

[cover]
width = 30
height = 15
```

## Usage

```bash
# Show full now playing information
plexampnp

# Show specific fields
plexampnp -a  # artist
plexampnp -t  # title
plexampnp -A  # album
plexampnp -y  # year
plexampnp -f  # file path
plexampnp -p  # progress

# Show album cover art
plexampnp -c

# List all active Plexamp clients
plexampnp --list-clients

# Show all media types (not just music)
plexampnp --all-media

# Filter by specific user
plexampnp --user username

# Show help
plexampnp --help
```

## Examples

Default output:
```
Artist - Title on Album [Year] 1:23 / 3:45
```

Cover art display:
```
[Album cover art displayed here]
```

## License

This software is released under the Perl License.

## Author

Magnus Woldrich <m@japh.se>

## See Also

- [Plexamp](https://plexamp.com/)
- [Plex Media Server](https://www.plex.tv/media-server-downloads/)

```
Usage: plexampnp [options]

  -a, --artist          Print the artist
  -t, --title           Print the title
  -A, --album           Print the album
  -f, --file            Print the full path to the file
  -y, --year            Print the year
      --np              Print the full now playing string (default behaviour)
      --list-clients    List all plexamp clients playing music

      --host            Plex server host (default: 192.168.1.34)
      --port            Plex server port (default: 32400)
      --address         Plexamp client address (default: 192.168.1.12)

  -h, --help        Display this help and exit

```
