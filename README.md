# plexampnp

A Perl script to display currently playing music from Plexamp in your terminal.

## Features

- Display currently playing track information
- Support for multiple Plexamp clients
- Album cover art display (requires chafa or viu)
- Plugin system for extending functionality
- Scrobbles plugin to show play history from a MySQL database
- Colorized output
- XDG config directory support

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/plexampnp.git
cd plexampnp

# Install dependencies
cpanm --installdeps .

# Install the script
perl Makefile.PL
make
make install
```

## Configuration

The script uses XDG config directory (`~/.config/plexampnp/config` by default). A default configuration file will be created on first run.

### Example Configuration

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

[filters]
music_only = 1
user = 

[cover]
width = 90
height = 45

[db]
host = 192.168.1.7
port = 3306
dbname = music
user = admin
pass = password

[plugins]
enabled = Scrobbles
```

## Usage

```bash
# Show currently playing track
plexampnp

# Show specific information
plexampnp --artist
plexampnp --title
plexampnp --album
plexampnp --year
plexampnp --file

# Show album cover art
plexampnp --cover

# Show scrobble information
plexampnp --scrobbles

# List all playing clients
plexampnp --list-clients

# Show help
plexampnp --help
```

## Plugins

### Scrobbles Plugin

The Scrobbles plugin displays play history information from a MySQL database. It shows:
- Number of times a track has been played
- First play date
- Last play date

To enable the plugin, add it to the `enabled` list in your config file:

```ini
[plugins]
enabled = Scrobbles
```

## Requirements

- Perl 5.10 or later
- XML::Simple
- LWP::Simple
- Term::ExtendedColor
- JSON
- Config::Tiny
- File::HomeDir
- Time::Piece
- File::Temp
- IPC::Run
- File::Path
- File::Spec
- DBI (for Scrobbles plugin)
- DBD::mysql (for Scrobbles plugin)

## License

MIT License

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
