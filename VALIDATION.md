# Validation — City Life 3.0

## Automated checks performed

- `npm run check`: PASS for server.js, public/game.js, public/world-data.js and public/city-data.js.
- `npm test`: PASS for original gameplay regression suite (updated job total) and new city expansion suite.
- Regression coverage: catalog totals, courier earnings, duplicate purchases, movement-speed bounds, marina spawn restrictions, aircraft ownership and exit altitude, raid/escape/wanted-level flow, ferry payment, saved accounts and HTTP health.
- Expansion coverage: 20 unique city locations; all entrances on land; valid service definitions; 27 job definitions; terrain bounds and continuity at park boundary; terrain height is computed server-side; paid services enforce location, cooldown and sufficient balance; health restoration; ranger contract completion above sea level; swept city-building and traffic collision; traffic yields to nearby walkers; traffic included in world snapshots; city-data.js HTTP serving.
- Archive integrity and both compressed/uncompressed package sizes checked at packaging.

Transport is mocked. These are not full WebSocket integration, visual quality, performance, accessibility or production-security tests. No real-browser WebGL render/playthrough was performed.

## Manual browser acceptance checklist

1. Install dependencies, start server, and join from two desktop browser profiles.
2. Open Cars, Boats, Aircraft, Homes and Clothes: verify 3D snapshots, image enlargement/closing, correct names and prices, and representative-home labels. Use keyboard Enter to enlarge.
3. Check High and Balanced graphics. Compare reflective vehicles, ambient occlusion, surface detail, shadows and nighttime interior lighting. Check GPU frame rate and lower quality as needed.
4. Drive at maximum boost toward a building, new business, traffic and another player. Confirm no forward tunneling. Confirm longer cars have larger collision margins. Approach stopped traffic and ensure traffic yields to pedestrians. Collision handling is intentionally conservative; it is not realistic crash physics.
5. Enter a generic building, a named business, an owned house and an unowned viewing property with E; leave at the front opening. Confirm room-category furnishings and no loss of exterior position.
6. Inside a restaurant, move away from the entrance and press E. Purchase a meal; confirm game cash and health update. Try insufficient funds and access from a distant location.
7. Use City to locate all 20 businesses/civic buildings. Verify their signs and entrance clearance. The gas forecourt pumps and supports should be solid.
8. Walk to Summit Range north of downtown; check ascent and descent, visible terrain-aligned task rings, camera elevation, checkpoint signs and ranger payout at the third stop.
9. Finish an office shift, stock-clerk route, three lawn tasks, postal route and an island passenger flight. Land on Aurelia's apron before waiting for the pilot payout.
10. Restart the server with its data directory retained and confirm account ownership and money persist.

## Boundaries

Procedural graphics are not photorealistic assets. Preview images are local renders, not real-world photographs. Home thumbnails are representative. Interiors use portals and room templates, not seamless unique buildings with every floor accessible. Civil services are lobbies; not every location offers a purchasable product. Jobs are waypoint/timed contracts. Fuel and mechanic purchases do not implement fuel depletion or vehicle damage. World vehicles use arcade footprints, not a physics engine. Client-side collision protects the original map; server-side car collision additionally covers new businesses and live traffic but is not comprehensive anti-cheat. Anonymous profile keys are not production-grade identity. WebGL/CDN availability, real WebSocket transport and target-device frame rate require manual verification.
