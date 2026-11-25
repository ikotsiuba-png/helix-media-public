# Helix media library

Pictures, videos and logos for the `helix-event-deck` skill. Before each build the skill pulls this repo and picks files for the event.

## Structure
```
_common/<kind>/     fits any event (stories, portraits, cities…)
<direction>/<kind>/ medical, books, agro, beauty, tech, food, mobility…
logos/<Company>.svg|png   file name = company name, exactly as in event.json
```
Kinds: `hero` (header video .mp4 + a .jpg still with the same name, or a photo; the skill picks the video whose name matches the event's first photo query, else the alphabetically first one — prefix the default with `00-`), `stories`, `sessions`, `products`, `experiences`, `banners`, `perks`.

## File names are the keywords
`robotic-surgery-surgeons-operating.jpg` matches the query "robotic surgery". Use English, lowercase, words separated by `-`.

## Formats
- Photos: JPG/WebP, landscape, at least 1200 px wide (the MEDITEX set is smaller and still works).
- Logos: SVG or PNG with transparency.
- Video: MP4 (H.264), 10–20 s, 1080p, no audio, under ~15 MB. Put a `.jpg` still with the same name next to it.

## Lookup order in the skill
The event's own `media/` folder → this repo (the event's direction, then `_common`) → Unsplash/Pexels → gradients.

## Sources
`medical/`, `_common/` pictures and `logos/` come from the MEDITEX 2027 demo in the Helix promo kit (fictional companies). All header videos (`*/hero/*.mp4`) are the kit's 10-second 1080p cuts of the Pexels clips in Tanya's Drive folder "App 2 0 video background" (drive.google.com/drive/folders/1oUn-ydOLaplChdNGwzY3sWsPwCV6i34M; originals there are 4K, up to 240 MB — too big for GitHub). Pexels licence: pexels.com/license.

Directions with videos: medical, tech, agro, food, energy, manufacturing; `_common/hero` (expo halls, crowds, cities) is the fallback for any other direction.

Photos taken from Pexels are listed with their source pages in `credits.json` (Pexels License: free to use, no attribution required).

`logos/` also holds 90 fictional company wordmarks (SVG) from the EP Design System v7 (Figma file TjUdoBdv3IlZ5rXc92SHcU, component set "Company logo", node 7531:71186; Style=Default, light). `logos/ep-marks/` holds the same 90 as square marks (48×48, name cut off): the build gives them to companies that have no logo of their own and to partner perks (wordmark), instead of generating logos.

`<direction>/logos/` (e.g. `beauty/logos/`): logos made for that direction; fictional companies of such an event get these first, then EP Design System marks.
