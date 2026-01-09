# HydroPulse

Hydroclimate anomaly detection through spatio-temporal data. In HydroPulse, I combine multiple hydroclimate datasets into one reproducible pipeline and build baselines for each location. Then I flag anomalies beyond simple drought cutoffs, trying to tell apart one-off events from longer-term shifts, and to account for how long conditions persist.
---

## What problem this answers

Typical drought metrics often collapse complex dynamics into a single threshold. HydroPulse is designed to:
- build location-aware baselines,
- detect deviations relative to historical variability,
- distinguish transient shocks (e.g., atmospheric river disruptions) from persistent regime shifts.

---

## Data sources (pipeline design)

The workflow is structured to integrate, at minimum:
- PRISM (gridded climate normals / precipitation-temperature)
- GHCND (station observations)
- ERA5 (reanalysis fields)
- SMAP (soil moisture)
- SNOTEL (snow + mountain hydroclimate signals)

Each source has different spatiotemporal resolution and uncertainty; the pipeline explicitly logs alignment and aggregation decisions.

---

## Method sketch 

- **Multi-scale temporal aggregation:** anomalies at multiple windows (days → weeks → seasons)
- **Persistence-weighted precipitation deficits:** anomalies penalized by duration, not just magnitude
- **Lagged temperature–moisture coupling:** captures compounding effects (hot + dry persistence)
- **Null hypotheses / regime deviation scores:** benchmark observed conditions against historical variability instead of fixed cutoffs

---

## Repository layout

- `hydropulse.ipynb` — end-to-end research notebook
- `LICENSE` — MIT
- `README.md` — project overview

---

## Quickstart

1) Create a Python environment (3.10+ recommended).  
2) Install dependencies (pin versions once stabilized).  
3) Run `hydropulse.ipynb` top-to-bottom.

---

## Outputs you should expect

- Gridded baseline fields
- Time series anomaly scores for selected locations
- Regime deviation summaries (maps + ranked regions)

---

## Status

Active, methods-development stage. Expect significant changes as tests and sensitivity analyses are added.

---

## Contact

Blue Leaf Labs — https://www.blueleaflabs.org
