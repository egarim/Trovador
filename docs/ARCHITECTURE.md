# Trovador Architecture

## Overview

Trovador is built using Electron with React, following a modern desktop application architecture that separates concerns between the main process (backend) and renderer process (frontend).

## Technology Stack

- **Electron**: Desktop application framework
- **React**: UI library for the renderer process
- **TypeScript**: Type safety across the application
- **Redux Toolkit**: State management
- **Vite**: Build tool and development server
- **SQLite**: Local database for music library
- **music-metadata**: Audio file metadata parsing

## Architecture Layers

### 1. Main Process (Backend)

The main process handles:
- File system operations
- Database management
- Native OS integrations
- IPC communication with renderer

Key components:
- **IPC Handlers**: Process requests from renderer
- **Database Service**: SQLite database operations
- **File Scanner**: Music file discovery and indexing
- **Metadata Service**: Read/write audio file tags

### 2. Renderer Process (Frontend)

The renderer process contains:
- React application
- UI components
- State management
- User interactions

Key components:
- **Components**: Reusable UI elements
- **Pages**: Main application views
- **Store**: Redux state management
- **Services**: API communication with main process

### 3. Shared Layer

Shared between both processes:
- **Types**: TypeScript type definitions
- **Constants**: Shared configuration values
- **Utils**: Common utility functions

## Data Flow

1. User initiates action in UI (renderer)
2. Action dispatched to Redux store
3. Side effect triggers IPC call to main process
4. Main process performs operation
5. Result sent back to renderer via IPC
6. Redux store updated with new data
7. UI re-renders with updated state

## Security Model

- Context isolation enabled
- Node integration disabled in renderer
- Preload script exposes limited API
- Input validation on all IPC channels
- File system access restricted to user-selected paths

## Performance Considerations

- Lazy loading of music library data
- Virtual scrolling for large lists
- Debounced search and filter operations
- Background indexing of music files
- Cached metadata to reduce file reads
