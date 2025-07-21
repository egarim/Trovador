# Trovador API Documentation

## Overview

Trovador uses Electron's IPC (Inter-Process Communication) to handle communication between the main process and renderer process.

## Main Process APIs

### File System Operations

#### `dialog:openFolder`
Opens a folder selection dialog for importing music libraries.

**Returns:** `string[]` - Array of selected folder paths

#### `fs:readDirectory`
Reads the contents of a directory.

**Parameters:**
- `path: string` - Directory path to read

**Returns:** `FileInfo[]` - Array of file information objects

### Music File Operations

#### `music:scanFiles`
Scans directories for music files.

**Parameters:**
- `paths: string[]` - Array of directory paths to scan

**Returns:** `MusicFile[]` - Array of discovered music files

#### `music:readMetadata`
Reads metadata from a music file.

**Parameters:**
- `filepath: string` - Path to the music file

**Returns:** `Metadata` - File metadata object

#### `music:writeMetadata`
Updates metadata for a music file.

**Parameters:**
- `filepath: string` - Path to the music file
- `metadata: Metadata` - New metadata to write

**Returns:** `boolean` - Success status

### Database Operations

#### `db:query`
Executes a database query.

**Parameters:**
- `query: string` - SQL query string
- `params?: any[]` - Query parameters

**Returns:** `any[]` - Query results

## Renderer Process APIs

### Store API

The renderer process uses Redux for state management with the following slices:

- `library` - Music library management
- `player` - Audio playback control
- `ui` - User interface state

### Hooks

Custom React hooks for common operations:

- `useLibrary()` - Access and manage music library
- `usePlayer()` - Control audio playback
- `useSettings()` - Manage application settings

## Data Types

### MusicFile
```typescript
interface MusicFile {
  id: string;
  path: string;
  filename: string;
  metadata: Metadata;
  stats: FileStats;
}
```

### Metadata
```typescript
interface Metadata {
  title?: string;
  artist?: string;
  album?: string;
  year?: number;
  genre?: string;
  track?: number;
  duration?: number;
  // ...additional fields
}
```
