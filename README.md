# Overview

5 years ago I have worked with a startup product that aim to create a platform for IoT devices, and they have one challenge is indoor mapping.
We did not have a really good solution on the market at that moment, so we had to use the architectural blueprint of the building on top of Leaflet.
For each room and floor, we use BIM data together with our IoT devices to create a 3D map. It works.

So, I'm not going to go in to details about how to build Leaflet because it's another story.

I would assume that we already have:

- Map tiles: This one is a huge task, and the UI should sit on top of the tile layer, not tightly coupled with it.
- Coordinate system and related data: This one also another story, and the UI should not related to this.

So if the first candidate I would choose to develop with:

- Mapbox (or Google Maps we are heavily interested in Google Cloud products): the pricing is acceptable and it provides a good collection of SDK to develop with.
- Leaftlet and OpenStreetMap: if we are looking for open source alternative libraries.

The overall code structure for a map component could contain:

- One or more UI components like general search input, sidebar for more complex filtering and tasks.
- The main interactive map component. Most of the time this one come from existing instance like Mapbox SDK or Leaftlet.
- The abstraction wrapper around above components so they can share the states and functions between.

Notes when developing with map:

- The map component is usually really heavy, so it should re-render as least as possible.
- The accessibility of components should respect the current state of the map applications: e.g. drag to move, pinch (or scroll) to zoom, etc. Re-inventing them could lead to really low user experience.
