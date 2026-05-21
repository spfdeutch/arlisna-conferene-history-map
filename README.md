# ARLIS/NA Conference Map

An interactive animated map tracing 55 years of [Art Libraries Society of North America (ARLIS/NA)](https://www.arlisna.org) annual conferences, from the founding meeting in Chicago in 1972 through Montréal in 2026, with Portland, Oregon (2027) marked as upcoming.

**[→ arlis-conference-map.html](arlis-conference-map.html)**

---

## What it shows

Each conference appears as a dot on an Albers USA projection extended to show Canada and Mexico. Dot size scales with attendance. A dashed trail connects locations in chronological order, building as you step through the years.

Dot colors encode conference type:

- **Orange** (`#D85A30`) — in-person conference
- **Blue** (`#6FA5CB`, ARLIS/NA brand blue) — virtual conference (2021, 2025)
- **Dashed outline** — upcoming (Portland 2027)

For each year the tooltip displays:

- City and conference dates
- Attendance
- Membership
- Attendance rate (% of members who attended)

Portland 2027 appears as a dashed outline marker with no data yet — see [Updating after Portland 2027](#updating-after-portland-2027) below.

## Controls

| Control | Action |
|---------|--------|
| **Play / Pause** | Animate through all 56 entries automatically |
| **← / →** arrows | Step backward or forward one year |
| **Scrubber** | Drag to jump to any year |

## Data

56 entries spanning 1972–2027. Conference locations, dates, attendance, and membership compiled from ARLIS/NA Executive Board reports and official conference records.

| Note | Detail |
|------|--------|
| Averaged figures | Attendance for 1976–1978, 1981, 1999–2001, and 2004–2005 is averaged from EB reports (no exact count recorded) |
| 2020 | Cancelled (COVID-19); a virtual event was held July 29–31 but is not mapped as a conference location |
| 2021, 2025 | Fully virtual — pinned to Boxborough, MA (ARLIS/NA management company location) |
| 2027 | Dates confirmed (Apr 2–8); attendance and membership TBD post-conference |

### Conference highlights

| | |
|---|---|
| First conference | Chicago, 1972 — 10 attendees |
| Peak attendance | New York City, 2018 — 908 attendees |
| Peak membership | San Francisco, 1993 — 1,391 members |
| Only cancellation | St. Louis, 2020 (COVID-19) |
| International locations | Toronto (1979, 2012), Montréal (1995, 2026), Vancouver (1999), Banff (2006), Mexico City (2023) |

## Usage

The file is fully self-contained HTML — no build step, no local server, no installation. Open it directly in any modern browser:

```bash
open arlis-conference-map.html
```

An internet connection is needed at load time to fetch the map tiles and D3 library from CDN. Once loaded, the map runs entirely in the browser.

It also renders correctly on GitHub Pages — just push the file and open it at its Pages URL.

## Updating after Portland 2027

Once final numbers are available, open `arlis-conference-map.html` and find the Portland entry near the bottom of the `conferences` array (around line 155):

```js
{year:2027, city:'Portland', lat:45.523, lon:-122.676,
 attendance:0, members:0, estAtt:false,
 dates:'Portland, Apr 2–8, 2027', upcoming:true},
```

Make two changes:

1. Replace `attendance:0` and `members:0` with the real figures.
2. Change `upcoming:true` to `upcoming:false`.

The dot will automatically switch from the dashed outline style to a solid filled marker sized by attendance, and the tooltip will display the real numbers.

## Dependencies

All loaded from CDN at runtime — nothing to install locally.

| Library | Version | Purpose |
|---------|---------|---------|
| [D3](https://d3js.org) | 7.8.5 | Map projection, rendering, and interaction |
| [TopoJSON](https://github.com/topojson/topojson) | 3.0.2 | Geographic topology decoding |
| [us-atlas](https://github.com/topojson/us-atlas) | 3 | US state boundaries |
| [world-atlas](https://github.com/topojson/world-atlas) | 2 | Country boundaries (Canada, Mexico) |
| [Tabler Icons](https://tabler.io/icons) | latest | Play/pause and arrow controls |

## About ARLIS/NA

The Art Libraries Society of North America is a dynamic organization of information professionals, artists, educators, and others committed to the advancement of art libraries and visual resources. Founded in 1972, ARLIS/NA serves over 800 members across the United States, Canada, and Mexico.

[arlisna.org](https://www.arlisna.org)
