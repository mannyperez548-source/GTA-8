# COASTLINE — City Life & Summit Range (3.0)

An expansion of the supplied Coastline Expanded multiplayer browser game.

## Run

Requires Node.js 20 or newer and internet access for dependency installation and the browser's Three.js CDN imports.

```sh
npm install
npm start
```

Open http://localhost:3000 in a modern desktop browser with WebGL enabled. Do not open index.html directly: the HTTP and WebSocket server must run. PORT defaults to 3000. DATA_DIR selects the saved-account directory; keep that directory on persistent storage when hosting. The included Render configuration is retained.

To update an existing installation, back up its data directory, replace the application files, and keep that saved data directory. Existing catalog IDs and anonymous browser profile keys are retained. Do not clear browser storage if you want to keep access to that profile.

## Added in this version

- Actual 3D model purchase snapshots for cars, boats, aircraft, outfits, and representative house/tower exteriors. Click or keyboard-activate an image to enlarge it. Previews render locally and are cached in browser memory, without photographic image downloads.
- Procedural surface textures and bump shading, a small prefiltered reflection environment, half-resolution screen-space ambient occlusion on High, existing soft shadows and bloom, and textured road/wood/grass/sand/concrete surfaces. Balanced disables shadows, bloom and ambient occlusion for performance.
- Public entrances on generated buildings; furnished private home tours (including before purchase), furnished generic public lobbies, and category-specific business interiors. Entering uses a separate room scene above the world: these are portal interiors, not seamless floor-by-floor replicas of the exterior. Rooms are not distinct multiplayer rooms.
- Solid arcade collisions with world buildings, traffic and other players. Player ground movement is subdivided into short steps to reduce tunneling. Car footprints conservatively expand with vehicle size. The server also checks swept movement against city businesses and traffic. Server traffic stops for nearby walkers and cars. This is not a rigid-body crash/damage simulation, and original building collisions remain client-side.
- Summit Range north of downtown, with a continuous height-field mesh, terrain-following walking, hiking trail, checkpoints, and an elevated multi-stop ranger contract. Terrain heights are shared with the server.
- 20 named city businesses and civic locations: restaurant, supermarket, gas station, cafe, bank, two office buildings, clinic, fire station, police station, library, gym, hotel, auto service, lawn care depot, school, cinema, bakery, pharmacy and post office.
- 12 additional legal jobs, for 27 total: accounting, software support, office administration, lawn care, chef, stock clerk, fuel attendant, barista, postal delivery, passenger pilot, trail ranger and hotel reception. Existing cargo pilot and helicopter jobs remain. Office and retail work uses timed contract tasks rather than a separate work minigame.
- City directory tab with entrance navigation. Businesses offer paid game-cash services where applicable. Food, coffee, groceries, first aid, rest and other listed services restore the stated health amount up to 100. Fuel and tune-up services are explicitly role-play purchases: there is no new fuel or vehicle-damage meter. Civic lobbies are exploratory, not full banking/education/emergency-service simulations.

## Controls and getting started

- WASD / arrow keys: move, drive or steer; Shift: sprint / boost; Space: brake.
- Drag mouse: orbit camera. Scroll: zoom.
- E: interact or enter. Inside, E close to the front door exits. In a public business, E away from the door opens City services.
- Tab: collection / catalog / city / jobs. H: help and graphics settings.
- M: expand map. T: chat. V: leave vehicle or open collection.
- R / C: aircraft climb / descend. Planes need forward speed to climb.
- F: non-graphic mission-NPC stun tool. Q: guard.

Start with $1,200; earn game cash at the Courier marker. Buy transport in the catalog; boat spawning requires a marina and aircraft spawning requires an airport. Use Jobs to locate dispatchers and City to find businesses. The mountain trailhead is near x=-95, z=-353, north of downtown; the ranger job guides three mountain checkpoints.

## Storage and graphics expectations

The ZIP and all uncompressed application source files are each collectively below 1,000,000 bytes at packaging. The game does not need to fill the budget to add features. This source-package limit does not include npm-installed dependencies, CDN-loaded Three.js modules, browser caches, runtime RAM, or growing saved-player data. It is not a fully offline single-file game.

Graphics are enhanced procedural low-poly / mid-detail rendering, not genuinely photorealistic scanned assets. The tiny package does not contain high-resolution real photographs, photogrammetry, or detailed architectural models. Home catalog snapshots are clearly labeled representative exteriors; vehicle snapshots use their actual in-game model generator.

## Validation

```sh
npm run check
npm test
```

Syntax checks cover server.js and every application JavaScript module. Two dependency-free mocked-transport suites exercise existing game behavior and the City Life expansion. They test jobs, ownership, saving, health/service purchases, purchase range and cooldown, terrain heights, elevated ranger payouts, traffic publication and yielding, swept city-business/traffic collision, aircraft restrictions and HTTP serving. These tests do not require installing ws because their loader substitutes a transport mock. Production requires the real ws dependency.

A real rendered-browser / GPU playthrough has not been performed in the build environment. See VALIDATION.md for manual checks and known boundaries. Test on target hardware before public deployment.
