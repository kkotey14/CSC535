# Golden Echoes

Single-file virtual art gallery for `CSC 535 Project 2`.

The project is built around one required deliverable:

- `index.html`

Everything needed for the gallery lives inside that file:

- HTML structure
- custom CSS
- Tailwind CDN config
- vanilla JavaScript
- room and artwork data
- interaction logic

## Project Overview

This gallery is designed as a scroll-based 2D virtual exhibition using works from the Rijksmuseum. It includes:

- 3 themed rooms
- 12 artworks total
- room-to-room movement through scrolling and section jump buttons
- click-to-open deep-dive overlay for each artwork
- title, artist, date, description, and official Rijksmuseum link for every piece
- staged reveal animations as the user scrolls

## Files In This Repo

- `index.html`
  This is the main project file and the only file required for the assignment deliverable.

- `README.md`
  This guide for teammates.

- other `.html` files
  These appear to be older experiments or scratch files. They are not required for running the final gallery unless the team decides to reuse them.

## Requirements

You do not need any package manager or build step.

You only need:

- a web browser
- a simple local server

## How To Run Locally

Because the page loads external museum images, it is better to serve the project over a local HTTP server instead of opening the file directly.

### Option 1: Python server

From the project folder:

```bash
cd /Users/kingsleykotey/Desktop/CSC535-Project
python3 -m http.server 8000
```

Then open:

```text
http://127.0.0.1:8000/
```

### Option 2: VS Code Live Server

If you use VS Code:

1. Open the folder.
2. Install the `Live Server` extension if needed.
3. Right-click `index.html`.
4. Click `Open with Live Server`.

## How The App Works

### 1. Hero section

The page opens with a large exhibition-style hero.

Purpose:

- establish the tone of the gallery
- give the visitor context before they enter the rooms
- lead users into the rest of the page by scrolling

### 2. Rooms

There are 3 room sections in `index.html`.

Each room contains:

- a room label
- a title and theme
- a short descriptive paragraph
- room metadata
- buttons to move to another room or open the Rijksmuseum collection
- a custom art layout generated from JavaScript data

### 3. Artwork data

All room and artwork content is stored in the `rooms` array in the JavaScript section near the bottom of `index.html`.

Each artwork object contains:

- `shortTitle`
- `title`
- `artist`
- `date`
- `description`
- `image`
- `link`
- `placement`

If teammates want to swap art, this is the main place to edit.

### 4. Artwork rendering

The function `buildRooms()` reads the `rooms` array and creates each artwork card dynamically.

This means:

- teammates do not need to manually hardcode all artwork cards in the HTML
- changes to artwork content mostly happen in one place

### 5. Deep dive overlay

Clicking an artwork opens a modal-style overlay.

That overlay is filled by:

- `populateDeepDive()`
- `openDeepDive()`
- `closeDeepDive()`

### 6. Scroll reveal animations

The page uses an `IntersectionObserver` so sections and artwork cards animate in as the user scrolls down.

The shared CSS class for that system is:

- `.reveal-item`

## Suggested Team Workflow

To avoid stepping on each other’s work, each teammate should choose a clear section.

Recommended split:

- Person 1: hero section and overall visual polish
- Person 2: room text, room sequencing, and navigation buttons
- Person 3: artwork data, descriptions, museum links, and fact-checking
- Person 4: QA, responsiveness, deployment, and final cleanup

If your team only has 3 people, combine the last two responsibilities.

## Safe Editing Guide

### If you are editing the hero

Work mainly in:

- hero HTML near the top of `body`
- `.intro-*` CSS rules

### If you are editing room copy or layout

Work mainly in:

- the room section markup inside `<main class="track" id="roomTrack">`
- `.room-*`, `.gallery-cluster`, and `.art-card` CSS

### If you are editing artworks

Work mainly in:

- the `rooms` JavaScript array

### If you are editing interaction logic

Work mainly in:

- `buildRooms()`
- `scrollToRoom()`
- `openDeepDive()`
- `closeDeepDive()`
- the reveal animation observer near the bottom

## Important Notes For Teammates

- The assignment asks for all team-written code in a single `index.html` file.
- Do not move the project into multiple CSS or JS files unless the team is intentionally making a separate non-submission version.
- If you change the artwork list, keep the total at 12 minimum.
- If you replace any artwork, make sure the Rijksmuseum link still works.
- If you change the room structure, keep it obvious that each section is a room with a theme.

## How To Test Before Pushing

Before pushing changes, check:

1. The page opens at `http://127.0.0.1:8000/`.
2. The hero appears first.
3. Scrolling reveals the rest of the gallery.
4. Each room still contains 4 artworks.
5. Clicking an artwork opens the deep-dive overlay.
6. The overlay shows title, artist, date, description, and museum link.
7. The layout still works on a narrower browser width.

## How To Deploy Later To The Student Server

The final deployment target mentioned in the assignment is:

```text
https://prd-stuweb02.southernct.edu/~[username]
```

Typical deployment approach:

1. Log into the student server with SFTP.
2. Open the `public_html` folder.
3. Upload `index.html`.
4. If the team later uses any separate assets, upload them there too.
5. Visit the public URL and verify that the page loads.

For the assignment submission, the team should make sure the final public version matches the current `index.html`.

## Git Basics For Teammates

Clone:

```bash
git clone https://github.com/kkotey14/CSC535.git
cd CSC535
```

Pull latest changes:

```bash
git pull origin main
```

Create your own working branch:

```bash
git checkout -b your-name-section
```

Stage and commit:

```bash
git add index.html README.md
git commit -m "Update gallery section"
```

Push your branch:

```bash
git push origin your-name-section
```

## Suggested Team Message

Use this in the group chat if needed:

```text
I’m pushing the latest gallery code to the repo now. Based on whichever section you choose, feel free to make any changes you need. Just try to stay mostly within your section so we don’t overwrite each other’s work. I also added a detailed README with instructions on how to run the project locally, where the main parts of the code live, and what to edit depending on your section.
```
