# The Skin Games World — Build Guide

A 3D virtual campus for The Skin Games (TSG): players, judges, sponsors and estheticians.
Owner: Jennifer, The Skin Games (info@theskingames.com). Future home: **world.theskingames.com**.

## For the Claude helping build this
- The whole world lives in **one file: `index.html`**. Three.js r159 is inlined at the top of the file, and the world's code is in the last `<script>` block. Keep it a single self-contained file.
- Make small, focused changes. Don't rewrite or restructure the file.
- After every change, check that the world still loads, and that you can walk between all six areas without errors.
- Keep it fast on phones and older laptops: simple shapes, no huge textures, and no new libraries without asking Jen.

## TSG style rules (from The Skin Games Design System)
- Colors: ink `#0d0d0d`, paper `#ffffff`, cream `#faf7f5`. The brand accent is magenta-pink `#e63def` (dark `#cf1fd9`, light `#fce8fa`). Gold `#e8c26a` is used **only** for prize and award moments.
- Fonts: headlines in Playfair Display (or Georgia); body text and buttons in Montserrat (or Helvetica).
- Buttons are pill-shaped, with uppercase text. Cards have rounded corners (14px) and soft shadows.
- Voice: confident awards-show energy, like "Where Legends Are Made" and "The Olympics of the Skincare Industry."

## Map (world coordinates, in meters)
| Area | Center (x, z) | Code section |
|---|---|---|
| Central Plaza (stone pavers, fountain + 3D gold TSG archer logo) | 0, 0 | `ground & plaza` (logo outline is in `LOGO_SHAPES`) |
| Sponsor Expo Hall (16 booths) | 0, -44 | `EXPO HALL` (sponsors are in the `SPONSORS` array) |
| Grand Auditorium (stage + screen slides) | 46, 0 | `AUDITORIUM` (slides are in the `slides` array) |
| Skin Fam Lounge (chat circles, café, board) | -44, 0 | `LOUNGE` |
| Champions Gallery (category plaques) | -30, 40 | `CHAMPIONS GALLERY` (categories are in the `CATS` array) |
| TSG Offices (Jen's office, Boardroom, team desks) | 30, 40 | `OFFICES` |

## How things work
- `interact.push({x,z,r,label,open})` creates a spot that shows a pink "Press E" button when you walk within distance `r`.
- `openCard({eb,title,body})` opens the info popup.
- `wall()` and `box(...,{col:true})` create objects you can't walk through.
- The gold rings on the floor are voice/video zones (`voiceZones`). Live calls are not switched on yet.
- The "(demo)" avatars are fake guests, there for the preview only.
- Live presence (seeing each other walk, chat, emotes) runs through `claude.use('room')`, which only works when the page is published as a Claude artifact. Opened as a plain file, the world still loads, with just you and the demo guests.
- Jen's live world is the Claude artifact https://claude.ai/artifact/BfWfLRxx7NbvvKbSByWAvu. Changes pushed to this repo get published there by Jen's Claude.

## Roadmap
1. Visual tweaks requested by Jen and her friend.
2. Real sponsor logos, champion photos and winner case studies.
3. Voice/video in the gold zones (seeing each other and chat already work in the live artifact).
4. Quest + points + leaderboard; AI Consultation Room for practicing client consultations.
5. Host at world.theskingames.com, with preview links before anything goes live.
