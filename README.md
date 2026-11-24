# Chandigarh Drive

A leisure driving game set in a half-scale Chandigarh, built to run in the browser. There's no racing and no timer: drive, ride or walk around Northern Chandigarh (Sectors 1 to 19 and Sukhna Lake), take a pedal boat out on the lake, and collect ten postcard spots if you like.

**Play it online:** https://karanysingh.github.io/chandigarh-drive/

![Himalaya Marg](docs/himalaya-marg.jpg)

## Play

Open `index.html` in a modern desktop browser. The game is a single self-contained HTML file; the only external dependency is Three.js r128, loaded from cdnjs.

If your browser blocks local files, serve the folder:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## What's in it

- **The city:** a real Chandigarh layout at half scale, covering Sectors 1 to 19. It has V2 and V3 roads (Uttar Marg, Madhya Marg, Udyog Path, Jan Marg and Himalaya Marg), clockwise roundabouts and left-hand traffic.
- **Landmarks:**
  - the Capitol Complex: High Court, Assembly, Secretariat and the esplanade
  - the Rock Garden: walled lanes and arches, rows of small mosaic figures, and a waterfall (on foot)
  - Sector 17: the Plaza with its fountain and arcades (on foot), Bank Square, the ISBT and the parade ground
  - the Rose Garden and the cricket stadium in Sector 16
  - the Government Museum and the Leisure Valley in Sector 10
  - Panjab University in Sector 14, with Gandhi Bhawan and the Student Centre
  - PEC and PGIMER in Sector 12, Rajendra Park, the Bougainvillea Garden and the Golf Club
- **Residential sectors:** houses, inner markets, gurudwaras and mandirs, and green belts.
- **Sukhna Lake:**
  - the parking lot, the entrance gate and plaza with food kiosks, and a plaque
  - the full promenade along the dam, with food carts, benches, ducks and rowing-lane buoys
  - a boat club jetty with swan pedal boats you can take out on the water
- **Vehicles:**
  - a hatchback
  - an original supercar (Aandhi GT)
  - an original classic motorbike (Rahi 350) that leans into corners
- **On foot:** get out of any vehicle and walk or run. The promenade and jetty are on foot only.
- **World detail:**
  - AI traffic, a walking crowd, and leaf-card trees that sway in the wind
  - real 3D grass, a day/night cycle, headlights and street lamps
  - a minimap, a full map and an aerial camera

## Controls

| Key | Action |
| --- | --- |
| W A S D / arrows | Drive, ride or walk |
| Space | Handbrake (jump when on foot) |
| Shift | Run when on foot |
| F | Get out, or get into a car, the bike or a pedal boat |
| Tab | Full map (or click the minimap) |
| C | Camera: chase, far, cockpit/helmet, showroom, aerial |
| G / V | Swap vehicle / change paint |
| Q / E | Left / right indicator |
| L · H · M | Headlights · horn · sound |
| T / N | Speed up time / jump 2 hours |
| P | Photo mode (hide the overlay) |
| R | Reset |
| Esc | Pause menu (resume, restart, map, sound) |

On touch screens, on-screen buttons appear for steering, throttle, brake and F.

## Screenshots

| | |
| --- | --- |
| ![Sector 17 Plaza](docs/sector17-plaza.jpg) | ![Rock Garden](docs/rock-garden.jpg) |
| ![Rock Garden waterfall](docs/rock-garden-waterfall.jpg) | ![Promenade](docs/promenade.jpg) |
| ![Motorbike](docs/motorbike.jpg) | ![Boat jetty](docs/jetty.jpg) |
| ![Promenade at night](docs/promenade-night.jpg) | |

![Full map](docs/map.jpg)

## Tech notes

- Three.js r128, plain JavaScript, no build step.
- All textures, including the foliage atlas, grass, bark and signs, are drawn procedurally on canvas at load time.
- Static city geometry is merged per material. Trees, grass, lamps, parked cars and people are instanced.
- Parked cars and far traffic are culled by distance.
- Trees use leaf-card crowns with a distance LOD and a wind shader.
- Grass tufts are placed using a top-down mask render. A height-map render lets you walk over curbs, medians and the jetty.
- The crowd uses five low-poly variants, with the walk cycle animated in the vertex shader.
- The walking character and riders are procedural and use two-bone IK for seated poses.
