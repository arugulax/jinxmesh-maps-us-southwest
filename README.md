# JinxMesh maps

Vector maps for the JinxMesh keyboard view on the Elecrow ThinkNode M9: contour lines, water, roads and
trails, rails, borders and names, drawn on the device. One state or province at a time, cut into files of
at most 48 MB.

## One repository per region

The maps of a continent are too much for one repository, so they are in several, each named
`jinxmesh-maps-<region>`:

| Region | States and provinces |
|---|---|
| `us-northeast` | CT, DC, DE, MA, MD, ME, NH, NJ, NY, PA, RI, VT |
| `us-southeast` | AL, AR, FL, GA, KY, LA, MS, NC, SC, TN, VA, WV, Puerto Rico, US Virgin Islands |
| `us-midwest` | IA, IL, IN, KS, MI, MN, MO, ND, NE, OH, SD, WI |
| `us-southwest` | AZ, NM, OK, TX |
| `us-mountain` | CO, ID, MT, NV, UT, WY |
| `us-pacific` | CA, HI, OR, WA |
| `us-alaska` | AK |
| `ca-east` | New Brunswick, Newfoundland and Labrador, Nova Scotia, Prince Edward Island, Quebec |
| `ca-central` | Manitoba, Ontario, Saskatchewan |
| `ca-west` | Alberta, British Columbia |
| `ca-north-west` | Northwest Territories, Yukon |
| `ca-north-east` | Nunavut |

A repository is made when the first map of its region is built; this one holds what is listed in `state/`
and `province/`.

## Layout

- `state/` for the United States, `province/` for Canada, as the folders are named on the card.
- `<name>-1.jmv`, `<name>-2.jmv`, ...: the pieces of a state, numbered from the north-west. A small one is a
  single `<name>.jmv`.
- `<name>.json`: the pieces of that state with their corners (south, west, north, east in degrees), sizes
  and SHA-256.

## On the card

Copy the pieces of the land you need to `/maps/state/` or `/maps/province/` on the SD card. The device shows
all of them side by side; pieces and states meet at their edges. A card does not need all pieces of a state,
only those of the land it is used in (the `.json` says which piece lies where). The `.json` files are not
needed on the card.

Pieces need a JinxMesh build that knows them (device-ui `6797d75` or later). Older builds draw them too,
with bolder lines along the cuts at zooms 7 to 10. Do not put a whole-state file and the pieces of the same
state on one card.

## Format and tools

"JMVM" version 4, described in `include/util/VectorMap.h` of the device-ui branch. Built by
`maps/vector/build.py`, cut by `maps/vector/split.py`, queued by `maps/vector/build-all.py` of the JinxMesh
scripts repository.

To build a map again, or one of other land or from your own data: `maps/vector/make-map.py` of that
repository does it in one command, and `docs/MAPS.md` there describes every step and source.

## Where the data is from

- Roads, water, borders, names: (c) OpenStreetMap contributors, under the Open Database License (ODbL),
  https://www.openstreetmap.org/copyright. Taken from the extracts of https://download.geofabrik.de.
- Contour lines: made from the Terrain Tiles open data set on AWS (https://registry.opendata.aws/terrain-tiles/),
  which in the United States comes from the USGS 3D Elevation Program, and elsewhere from the sources named
  at https://github.com/tilezen/joerd/blob/master/docs/attribution.md.

The maps here are a database made from OpenStreetMap and stay under the ODbL.
