# Georgetown Pulse Topology — 3D Bulb Visualizer

Interactive 3D viewer for the Georgetown hanging-bulb layout. Each bulb hangs from a ceiling mount grid at its own depth, forming a topographic surface. Loads the CSV directly in the browser — no export step needed.

## Run Locally

Serve this folder with any static server, then open `index.html`:

```bash
python3 -m http.server
```

Then open http://localhost:8000/ (or use Cursor / VS Code Live Server).

## Data Input

- Default source: `001-june30.csv`
- Override with a query string: `index.html?csv=other-layout.csv`

Expected CSV columns:

`index, position_x, position_y, position_z, pitchx, pitchy, cablelength(M), BulbCables, BulbZ, lineid, ID, Universe`

| Field            | Meaning                                          |
|------------------|--------------------------------------------------|
| `position_x/y/z` | Ceiling mount point (z = ceiling height)         |
| `BulbCables`     | Length the bulb hangs below the ceiling mount    |
| `BulbZ`          | Vertical offset of the bulb (negative, = -drop)  |
| `cablelength(M)` | Total cable length for wiring                    |
| `lineid`         | Line / row group                                 |
| `Universe`       | DMX universe                                     |

Bulb world height = `position_z + BulbZ`.

## Controls

- **Color by**: bulb height (topology), drop length, total cable length, universe, or line
- **Point size**: rendered bulb size
- **Drop line opacity**: opacity of the ceiling→bulb drop lines
- **Mouse**: drag to orbit, scroll to zoom, right-drag to pan, hover a bulb for ID / line / universe / drop / height / cable

## Notes

- Built with [Three.js](https://threejs.org/) via CDN; nothing to install.
- Adapted from the 2025 Boston Pulse Topology cable visualizer for this show's bulb-grid data model.
