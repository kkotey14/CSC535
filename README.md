# Golden Echoes

`Golden Echoes` is a single-file virtual art gallery for `CSC 535 Project 2`.

The main deliverable is:

- `index.html`

That file contains the full project:

- HTML
- CSS
- Tailwind CDN setup
- JavaScript
- room and artwork data
- interaction logic

## Project Snapshot

This version of the gallery is built as a top-down 2D route using Rijksmuseum works.

It includes:

- 3 themed rooms
- 12 artworks total
- a moving guide bot inside each room plan
- room switching with buttons and arrow keys
- artwork deep-dive overlay with title, artist, date, description, and Rijksmuseum link
- scroll-based reveal animation

## Files

- `index.html`
  The full gallery experience and the required assignment file.

- `README.md`
  A short guide for teammates.

- other `.html` files
  Older experiments or scratch files. They are not part of the main submission unless the team chooses to reuse them.

## Running The Project

There is no build step and no package manager.

A simple local server is enough. `Live Server` in VS Code is fine, or any other localhost setup your teammate already uses.

The main thing is to open the project through localhost instead of double-clicking the file, since the page loads external museum images.

## How The Gallery Works

### Hero

The page opens with an exhibition-style intro section, then moves into the gallery as the user scrolls.

### Rooms

There are 3 rooms, and only one room is active at a time.

Each room has:

- a title and theme
- short room text
- room navigation buttons
- a top-down 2D floor plan
- 4 artworks placed around the room

### Guide Bot

The small moving avatar in the floor plan is the guide bot.

It shows where the visitor is in the room route:

- `Left` and `Right` arrow keys switch rooms
- `Up` and `Down` move between artwork stops
- the guide bot moves along the room route instead of staying still

### Artwork Data

All room content lives in the `rooms` array near the bottom of `index.html`.

If someone wants to update a work, title, description, or link, that is the first place to check.

### Deep Dive Overlay

Clicking a framed artwork opens a larger detail view.

That overlay is handled by:

- `populateDeepDive()`
- `openDeepDive()`
- `closeDeepDive()`

## Main Parts To Edit

### Visual design

Look at:

- the hero markup near the top of `body`
- the `.intro-*` CSS rules
- the `.room-*` and `.art-card` CSS rules

### Room text or structure

Look at:

- the room sections inside `<main class="track" id="roomTrack">`

### Artwork content

Look at:

- the `rooms` array in the script

### Interaction logic

Look at:

- `buildRooms()`
- `activateRoom()`
- `focusArtwork()`
- `animateVisitorToken()`
- `openDeepDive()`

## Quick Testing

Before pushing changes, a teammate should quickly check:

1. The intro loads first.
2. Room tabs switch between all 3 rooms.
3. Each room still has 4 artworks.
4. The guide bot moves when the artwork focus changes.
5. Clicking an artwork opens the detail overlay.
6. The Rijksmuseum link still opens.
7. The page still looks okay on a smaller screen.

## Important Notes

- Keep team-written code in `index.html` for the final assignment submission.
- Keep at least 12 artworks total.
- Make sure every artwork still has a working Rijksmuseum link.
- Keep the room themes clear so the gallery still reads as separate spaces.

## Deployment Reminder

The assignment says the final file should be published to:

```text
https://prd-stuweb02.southernct.edu/~[username]
```

When the team is ready, upload the final `index.html` to `public_html` on the student server and test the public URL.
