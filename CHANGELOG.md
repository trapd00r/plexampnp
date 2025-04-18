# Changelog

All notable changes to the `plexampnp` script will be documented in this file.

## [1.3.1] - 2024-04-18
### Changed
- Simplified scrobble format to use "x" and ".." instead of emojis
- Improved readability of scrobble output

## [1.3.0] - 2024-04-18
### Changed
- Removed progress bar functionality
- Improved UTF-8 handling for scrobble information
- Updated plugin system to properly handle plugin instances
- Separated scrobble output options into `-s` (count only) and `--scrobbles` (full info)

### Added
- Scrobbles plugin support with scrobble count and date range display
- Plugin system for extending functionality
- Database configuration support
- Simple scrobble count output (`-s`) for status bar integration

## [1.2.0] - 2024-04-17

### Added
- Album cover art display in terminal (`-c, --cover` option)
- Support for `chafa` and `viu` terminal image viewers
- Configuration options for cover art size
- Temporary file handling for cover art

### Dependencies
Added new dependencies:
- File::Temp
- IPC::Run

## [1.1.0] - 2024-03-21

### Added
- Configuration file support (`~/.plexampnp.conf`)
- Progress information display (time elapsed/remaining)
- User filtering with `--user` option
- Media type filtering with `--all-media` option
- Improved client listing with user information
- Better error handling with descriptive messages
- Time formatting utilities
- New `--progress` option to show track progress

### Changed
- Restructured code into logical subroutines
- Improved code readability and maintainability
- Enhanced default output format to include progress information
- Better session filtering logic
- More consistent color usage
- Improved help text formatting
- Configuration moved to structured hash

### Configuration
The script now supports a configuration file at `~/.plexampnp.conf` with the following format:
```ini
[plex]
host = 192.168.1.34
port = 32400

[plexamp]
host = 192.168.1.12

[filters]
music_only = 1
user = your_username

[cover]
width = 30
height = 15
```

### New Command Line Options
- `--user USER` - Filter by specific user
- `--all-media` - Show all media types (not just music)
- `-p, --progress` - Show progress information
- `-c, --cover` - Display album cover art

### Default Output Format
The default output now includes progress information:
```
Artist - Title on Album [Year] 1:23 / 3:45
```

### Dependencies
Added new dependencies:
- Config::Tiny
- File::HomeDir
- Time::Piece
- Time::Seconds

## [1.0.0] - Initial Release
- Basic Plexamp now playing functionality
- Support for various output formats (artist, title, album, year, file)
- Colorized output
- Client listing capability 
