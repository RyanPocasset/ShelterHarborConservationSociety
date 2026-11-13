# Shelter Harbor Conservation Lands Map (public version)

Interactive map of the Shelter Harbor Conservation Society lots and the Shelter Harbor Fire District open space around them in Westerly, Rhode Island. It covers forest type by hydrology, conifers, LiDAR tree height and density, conversion history since 1939 (open fields, stone walls, dug drainage ditches), streams, springs and wetlands, wildlife and habitat potential, geology, and Indigenous and U.S. history, including the Spears-Nardone Bridge and the Musicolony water works. Fifteen stories tie the layers to people and places. The base map is town-wide leaf-off (March 2026) and leaf-on (July 2022) imagery. The 1939, 1951–52, 1962, 1972 and 1997 aerials and 2022 LiDAR relief are clipped to the properties.

Produced by **PPLT AGIKS**, Pocasset Pokanoket Land Trust. Field observations are from the PPLT field survey of 11 November 2026.

**This public build leaves out small-mound candidates and closed depressions**, along with their counts. Boulders, erratics and boulder fields appear through the *Granite, moraine and stony till* story rather than the Map tab.

## Contents

| Path | What it holds | Files |
|---|---|---|
| `index.html` | The map page (Leaflet 1.9.4, bundled) | 1 |
| `data.js` | All map layers and per-property numbers | 1 |
| `lib/` | Leaflet JS, CSS and license | 3 |
| `base/` | Town-wide leaf-off / leaf-on base map | 26 |
| `detail/` | Sharper leaf-off imagery around the properties | 9 |
| `hist/` | 1939, 1951–52, 1962, 1972 and 1997 aerials | 10 |
| `lidar/` | 2022 LiDAR relief, canopy height, vegetation height and stream-height rasters | 4 |
| `.nojekyll` | Tells GitHub Pages to serve files as-is | 1 |

About 37 MB in total; the largest file is 2.4 MB. Everything loads by relative path. Nothing calls outside services except Google Fonts, and the page falls back to system fonts without them.

## Put it on GitHub Pages

**With git or GitHub Desktop (simplest):**

1. Copy the `shelter-harbor-map` folder's contents into the root of a new repo (for example `ShelterHarbor`), or copy the folder itself into an existing Pages repo as a subfolder.
2. Commit and push.
3. If Pages isn't on yet: Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)`.
4. Open `https://<user>.github.io/<repo>/` (root) or `https://<user>.github.io/<repo>/shelter-harbor-map/` (subfolder). The first deploy can take a few minutes.

**In the browser:** GitHub's uploader takes up to 100 files per commit, and this map is 56 files, so one commit is enough. On the new repo's page choose **Add file → Upload files**, then drag in `index.html`, `data.js`, `README.md` and the five folders (`lib`, `base`, `detail`, `hist`, `lidar`) so their folder names are kept.

`.nojekyll` only matters if this folder is the root of the Pages site. It's a hidden file, so show hidden files to drag it in, or create an empty file with that name on GitHub.

## Embed in ArcGIS StoryMaps

1. Add a block → **Embed** → paste the page URL → choose the interactive **Embed** display, not Card.
2. 650–800 px tall works well. In narrow frames the side panel starts closed, and readers open it with **Layers & info**.
3. In sidecars and guided slides, embed the same page several times with different URL parameters so each slide opens on its own view.

## URL parameters

| Parameter | Values | Effect |
|---|---|---|
| `property` | Property name or part of one, any case, or its plat/lot (e.g. `125-001`) | Zooms to it and shows its numbers |
| `base` | `leafoff`, `leafon`, `none` | Town-wide base map |
| `hist` | `1939`, `1951`, `1962`, `1972`, `1997`, `lidar`, `none` | Imagery shown on the properties |
| `layers` | Comma list of layer keys | Only these layers start on |
| `story` | Story key | Opens the story, turns on its layers and zooms to it |
| `tab` | `map`, `stories` | Which panel tab is open |
| `panel` | `0` closed, `1` open | Side panel state |

Layer keys:

- Land cover and forest: `ftype` (forest type by hydrology), `evergreen` (conifers and evergreen understory), `struct` (vegetation height class), `chm` (tree height), `grid` (20 m stand metrics), `mature` (mature canopy ≥24 m)
- Conversion history: `f39` (open fields in May 1939), `walls` (stone walls), `ditch` (dug drainage ditches), `lu88`, `lu11` (land cover 1988, 2011)
- Hydrology: `reaches` (stream bed character and flow), `springs` (springs and seep heads), `rist` (RIDEM streams and cold-water designation), `nwi` (wetlands by water regime), `rem` (height above the nearest stream bed), `ws` (watersheds)
- Wildlife: `obs` (field detections, 11 Nov 2026), `lowa` (Louisiana Waterthrush stream potential), `trout` (coldwater reaches), `wturt` (wood turtle corridor), `sturt` (spring pools), `nha` (RIDEM Natural Heritage Areas)
- Geology and soils: `bedrock`, `glacial`, `soils`, `soilpts`, and the story layers `boulders` (boulders and erratics), `bfields` (boulder fields), `tipups` (windthrow pit-and-mound)
- History: `hist` (historic places), `water` (Spears-Nardone Bridge and Musicolony water works), `cem` (historic cemeteries), `dist` (Shelter Harbor and Weekapaug districts), `roads` (roads and town line)

Story keys: `niantic`, `weekapaug`, `sosoa`, `kpw`, `park`, `quonnieneck`, `freebody`, `inn`, `nardone`, `barrier`, `shcs`, `geology`, `brook`, `waterworks`, `pools`.

Examples, appended to your page URL:

- `?story=waterworks&panel=0` opens on the Spears-Nardone Bridge, the dug reservoir and the probable water line.
- `?story=geology&panel=0` shows bedrock, glacial deposits, boulders, erratics and boulder fields.
- `?property=greenbelt&hist=lidar&layers=boulders,bfields,reaches&panel=0` shows the bouldery brook valley on LiDAR relief.
- `?property=greenbelt&hist=1939&layers=f39,walls,roads&panel=0` shows the greenbelt and its open fields in May 1939.
- `?property=Rossini&base=leafoff&layers=sturt,ditch,obs,reaches&panel=0` shows spring pools and the ditch grid in Rossini Road woods.

## Sources and credits

- Base imagery: RIGIS orthophotography, March 2026 (leaf-off) and July 2022 (leaf-on); April 2011 color-infrared.
- Historic aerials: 1939, 1951–52, 1962, 1972 and 1997 statewide photography, RI Statewide Planning / RIGIS (URI EDC).
- LiDAR: USGS 3DEP point cloud, RI_Statewide_D22 (flown 29 March 2022); RIGIS 2022 LiDAR DEM.
- Wetlands: USFWS National Wetlands Inventory (2014); RIGIS wetlands (1988).
- Soils: USDA NRCS SSURGO (2025 release) via RIGIS.
- Bedrock geology, glacial deposits, stone walls, streams, E-911 roads (2026), building footprints (2022), land cover (1988, 2011), historical cemeteries, RIDEM Natural Heritage Areas and Local Conservation Areas: RIGIS.
- Property boundaries: Town of Westerly parcels (2025).
- Species status: 2015 RI Wildlife Action Plan SGCN list; 2025 status pending — verify in the RIWAP database (dem.ri.gov/riwap-database).
- Leaflet 1.9.4, BSD-2-Clause (`lib/LEAFLET-LICENSE.txt`).

Mapped landforms, pools and habitat potential are LiDAR and photo interpretations, not field-verified. Field observations are from the PPLT field survey of 11 November 2026.
