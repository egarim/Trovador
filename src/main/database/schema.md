# Trovador Database Schema

## Overview

Trovador uses SQLite for local data storage. The database stores music library information, playlists, and user preferences.

## Tables

### tracks

Stores information about music files in the library.

| Column | Type | Description |
|--------|------|-------------|
| id | INTEGER PRIMARY KEY | Unique identifier |
| file_path | TEXT UNIQUE NOT NULL | Full path to the music file |
| filename | TEXT NOT NULL | File name |
| title | TEXT | Track title |
| artist | TEXT | Artist name |
| album | TEXT | Album name |
| album_artist | TEXT | Album artist |
| year | INTEGER | Release year |
| genre | TEXT | Music genre |
| track_number | INTEGER | Track number |
| disc_number | INTEGER | Disc number |
| duration | REAL | Duration in seconds |
| bitrate | INTEGER | Audio bitrate |
| sample_rate | INTEGER | Sample rate in Hz |
| file_size | INTEGER | File size in bytes |
| date_added | TEXT | ISO date when added to library |
| date_modified | TEXT | ISO date of last modification |
| play_count | INTEGER DEFAULT 0 | Number of times played |
| rating | INTEGER | User rating (1-5) |
| last_played | TEXT | ISO date of last play |

### playlists

Stores user-created playlists.

| Column | Type | Description |
|--------|------|-------------|
| id | INTEGER PRIMARY KEY | Unique identifier |
| name | TEXT UNIQUE NOT NULL | Playlist name |
| description | TEXT | Playlist description |
| created_date | TEXT | ISO date created |
| modified_date | TEXT | ISO date modified |

### playlist_tracks

Junction table for playlist track relationships.

| Column | Type | Description |
|--------|------|-------------|
| playlist_id | INTEGER | Foreign key to playlists |
| track_id | INTEGER | Foreign key to tracks |
| position | INTEGER | Track position in playlist |
| PRIMARY KEY | (playlist_id, track_id) | Composite primary key |

### folders

Monitored folder locations.

| Column | Type | Description |
|--------|------|-------------|
| id | INTEGER PRIMARY KEY | Unique identifier |
| path | TEXT UNIQUE NOT NULL | Folder path |
| enabled | INTEGER DEFAULT 1 | Whether folder is actively monitored |
| last_scan | TEXT | ISO date of last scan |

### settings

Application settings and preferences.

| Column | Type | Description |
|--------|------|-------------|
| key | TEXT PRIMARY KEY | Setting key |
| value | TEXT | Setting value (JSON) |

## Indexes

- `idx_tracks_artist` on tracks(artist)
- `idx_tracks_album` on tracks(album)
- `idx_tracks_title` on tracks(title)
- `idx_tracks_file_path` on tracks(file_path)
- `idx_playlist_tracks` on playlist_tracks(playlist_id, position)

## Migrations

Database migrations are handled automatically on application startup. Migration files are stored in `src/main/database/migrations/`.
