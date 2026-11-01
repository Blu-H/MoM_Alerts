# Final_Alert attributes
Below is description of the columns produced in the `Final_Attributes_<timestamp>*.csv` product.

## Alert
Categorical severity label — `Information` / `Advisory` / `Watch` / `Warning` — assigned from `Severity` and `Hazard_Score` via the threshold rules.

## Status
Compares this run's `Alert` to the same watershed's `Alert` from the earlier run: `New` (no prior record), `Continued` (same level), `Upgraded` (more severe), `Downgraded` (less severe).

## hazard_score (→ Hazard_Score)
A unitless composite score, calculated via `max(Hazard_Score, source_score)` — first against GFMS & GloFAS score and HWRF score, then DFO score, then VIIRS score. The final value is whichever of the four sources currently shows the worst flood signal for that watershed. Thresholds are: >=80 highest, 60–80, 35–60, 0–35 lowest.

## Severity
A 0–1 probability-like value: how extreme the current hazard signal is relative to what the watershed's baseline flood-risk profile would "expect." Used alongside the raw `Hazard_Score` thresholds to assign `Alert`.

## pfaf_id
The Pfafstetter watershed code — the primary key every data source is aggregated to. Comes from the watershed shapefile.
