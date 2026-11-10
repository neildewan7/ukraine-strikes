# Ukraine Crisis Map

A single-file interactive map of Russian strikes on Ukraine — strike density, displacement data, and a proposed humanitarian response (evacuation corridors, aid zones) overlaid on one map, built for a 24-hour humanitarian mapathon.

**🏆 3rd place + Best Design**, 2026 International Humanitarian Mapathon (Hitotsubashi University, Special Lectures: New Approaches to International Law and Relations, Prof. Sumie Nakaya).

**Live demo:** <!-- TODO(Neil): holding off on enabling GitHub Pages here until the ACLED data question below is resolved, so the visualization doesn't get more visible/discoverable in the meantime -->

**My role:** team of 4 (with Clara Wei, Yutaka Yamada, Natalie Ly). Clara and I wrote the code; I led the technical build — initial map + data pipeline, the military bases/border crossings/IDP overlay, and the routing fixes (1,408 lines added across my commits vs. 1,035 for Clara). Clara did early project framing and later UI/routing hardening (absolute-positioned sidebars, responsive layout fixes). Yutaka and Natalie contributed to data sourcing/verification. Full data provenance and the contributor list are in `citations.html` (linked from the map).

## What it does

- Renders Russian strike events (ACLED, Feb 2022–Apr 2026) as a density layer, categorized by target type (energy, residential, healthcare, education)
- Overlays IDP/returnee estimates per oblast (IOM Displacement Tracking Matrix)
- Marks military airfields and border crossings
- Proposes evacuation corridors and aid-zone placement based on where strike density overlaps IDP data gaps — a suggested intervention, not an official plan (stated explicitly in-app)

## How it was built

Single-file static HTML app using MapLibre GL JS over CARTO Dark Matter tiles, with ACLED/IOM/Natural Earth data pre-processed into GeoJSON and deployed on GitHub Pages — no backend, no build step.

## Data and limitations

Full sourcing, known data gaps (e.g. no IDP estimates for occupied oblasts; strike categorization is approximate keyword matching), and the complete contributor list are documented in `citations.html`. Read that before using any numbers from this map elsewhere.

**Note on the ACLED data in this repo:** `strikes.geojson` is a filtered/categorized derivative of ACLED's raw export, not the raw file — but it may still exceed what ACLED's terms of use permit for redistribution. This predates my README rewrite and lives in a repo with other contributors; flagging it here rather than editing data files unilaterally. <!-- TODO(Neil): confirm with Clara/team whether to restrict this file or get ACLED's sign-off before treating this as a long-term public artifact -->

## Run it locally

Open `index.html` in a browser — no build step, no server required. All dependencies load from CDN.
