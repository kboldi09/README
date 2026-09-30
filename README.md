# Town gravity map

`town-gravity-map.html` is a single-file tool. Open it in a browser, paste or load a CSV of addresses, and it will:

- geocode every address and plot it on a map
- work out the **centre of gravity per town**: the mean of that town's coordinates, weighted by an optional `weight` column. It draws a black star at each centre, with thin lines out to the town's points
- **colour points by any column** (e.g. `type`) and **highlight** points matching a rule (e.g. `type equals cafe`, `revenue > 1000`) with a bigger, yellow-ringed marker
- export the centres as CSV, and everything as KML for import into **Google My Maps** or Google Earth

## CSV format

Minimum: an `address` column and a `town` column. You can pick the columns in the UI.
If you already have coordinates, add `lat` and `lng` columns and those rows skip geocoding.

```csv
address,town,type,weight
Dam 1,Amsterdam,shop,3
Neude 11,Utrecht,museum,1
```

## Google Maps vs OpenStreetMap

- **With a Google Maps API key** (Maps JavaScript API + Geocoding API enabled): renders on Google Maps and geocodes with Google.
- **Without a key:** renders on OpenStreetMap and geocodes with Nominatim, which is free but slow (1 address/second).

Geocoding results are cached in your browser, so re-plots are instant.
