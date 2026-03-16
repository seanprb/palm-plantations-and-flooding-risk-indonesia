# Domain Profile

## Field

**Primary:** Development Economics / Environmental Economics
**Adjacent subfields:** Environmental and Resource Economics, Agricultural Economics, Political Economy of Development, Tropical Forestry Economics

---

## Target Journals (ranked by tier)

| Tier | Journals |
|------|----------|
| Top-5 | AER, QJE, JPE, REStud, Econometrica |
| Top field | Journal of Development Economics (JDE), Journal of the Association of Environmental and Resource Economists (JAERE), American Economic Journal: Applied Economics (AEJ:Applied), American Economic Journal: Economic Policy (AEJ:Policy) |
| Strong field | Review of Economics and Statistics (RESTAT), Environment and Development Economics (EDE), World Development, Journal of Environmental Economics and Management (JEEM) |
| Specialty | Ecological Economics, Forest Policy and Economics, Global Environmental Change, Nature Sustainability |

---

## Common Data Sources

| Dataset | Type | Access | Notes |
|---------|------|--------|-------|
| MODIS flood inundation (Terra/Aqua) | Satellite raster | Public (NASA) | 500m resolution; daily; historical archive from 2000; needs cloud-clearing; complement with Landsat/Sentinel-2 for validation |
| Dartmouth Flood Observatory (DFO) | Event-level panel | Public | Georeferenced flood events 1985–present; includes extent polygons |
| Global Surface Water Explorer (JRC/Google) | Satellite raster | Public | Monthly water presence 1984–2021; permanent vs. seasonal water |
| Indonesian Village Census (PODES) | Village-level panel | Public (BPS) | Every 3 years; flood incidence self-report; 70,000+ villages |
| Ministry of Forestry / KLHK concession maps | Polygon shapefile | Public (partial) | Palm oil HGU concession boundaries; spatial join to village/grid |
| Global Forest Watch (GFW) / Hansen et al. | Raster, annual | Public | Annual forest cover loss at 30m resolution; tree cover gain |
| CHIRPS rainfall | Gridded climate | Public | Daily/monthly precipitation, 0.05° resolution, 1981–present |
| SRTM Digital Elevation Model | Raster | Public (NASA) | 30m or 90m DEM; derive slope, flow accumulation, catchment areas |
| TerraClimate | Gridded climate | Public | Monthly climate variables including soil moisture, runoff |
| Indonesian Land Use / Land Cover (KLHK) | Raster/polygon | Public (BPS/KLHK) | Biennial land use classification including plantation categories |
| BPS Agricultural Census | Village/district panel | Public | Plantation area statistics by crop type |
| GADM / BPS administrative boundaries | Polygon shapefile | Public | Indonesia admin levels 1–4 (province, district, subdistrict, village) |
| FAO/HarvChoice palm oil suitability | Raster | Public | Agro-ecological suitability index; key instrument candidate |

---

## Common Identification Strategies

| Strategy | Typical Application | Key Assumption to Defend |
|----------|-------------------|------------------------|
| Difference-in-Differences (DiD) | Compare flood risk before/after plantation expansion in treated vs. control villages/grids | Parallel trends: treated and control areas would have followed same flood trend absent expansion; no anticipatory effects |
| Staggered DiD (Callaway-Sant'Anna, Sun-Abraham) | Plantation expansion happens in different areas at different times | No anticipation; parallel trends conditional on covariates; heterogeneous treatment timing correction required |
| Instrumental Variables | Instrument palm oil expansion with: (1) world palm oil price × land suitability; (2) deforestation moratorium (2011) policy shocks; (3) distance to existing mills × price | Exclusion restriction: instrument affects flooding only through plantation expansion; suitability IV may fail if suitability correlated with natural hydrology |
| Regression Discontinuity (RDD) | Exploit sharp concession boundaries — compare pixels/villages just inside vs. just outside granted concession | No sorting around boundary; boundary as-good-as-randomly assigned within bandwidth |
| Shift-Share (Bartik) | National palm oil price shocks × local historical suitability | Relevance: price shocks shift expansion; exogeneity: historical suitability uncorrelated with time-varying shocks |
| Event Study | Trace dynamic effects of plantation approval/clearing on flood outcomes | No pre-trends; effects stabilize at new steady state |

---

## Field Conventions

- **Unit of observation:** Prefer 0.05°×0.05° grid cells (matching CHIRPS resolution) or village level (matching PODES); report robustness to both
- **Outcome variables:** Binary flood indicator (satellite), flood area (ha), flood duration (days), flood intensity index — be explicit about which measure; validate against DFO events
- **Treatment variable:** Log(plantation area) or share of grid cell covered by palm oil concession; distinguish granted vs. developed concessions
- **Controls to always include:** Log(rainfall), elevation, slope, distance to river, pre-period forest cover, district FE, year FE
- **Clustering:** At district level (kabupaten) or concession level; discuss choice; use two-way clustering if identification is within district × year
- **Heterogeneity:** By elevation/slope (flood-prone vs. not), peat soil (drainage implications), moratorium period, proximity to rivers, firm size, plantation age
- **Placebo tests:** Check effects on non-flood outcomes (droughts, heat) or on areas with unsuitable soils
- **Deforestation mechanism:** Decompose — is the effect driven by forest loss or by changes in ground cover post-clearing?
- **Welfare analysis:** Back-of-envelope cost of flooding per household; compare to palm oil income gains
- **Software:** R with `sf`, `terra`, `fixest`, `did`; or Stata with `reghdfe`, `ivreg2`, `rdrobust`, `csdid`

---

## Notation Conventions

| Symbol | Meaning | Anti-pattern |
|--------|---------|-------------|
| $Y_{igdt}$ | Outcome (flood) for grid cell $i$ in district $d$ at time $t$ | Don't use $Y_i$ without specifying all panel dimensions |
| $P_{igdt}$ | Palm oil plantation area share (or log area) | Don't conflate concession grant with realized deforestation |
| $\mathbf{X}_{igdt}$ | Controls vector (rainfall, elevation, slope, distance to river) | Don't include time-varying controls that may be post-treatment |
| $\alpha_d$, $\alpha_t$ | District FE, year FE | Always report which FE are included in each column |
| $\delta_{dt}$ | District × year FE | Absorbs district-specific trends — mention explicitly when used |

---

## Seminal References

| Paper | Why It Matters |
|-------|---------------|
| Burgess et al. (2012, QJE) — *The Political Economy of Deforestation in the Tropics* | Benchmark for deforestation + political economy in Indonesia using satellite + administrative data |
| Jayachandran (2009, AER) — *Air Quality and Early-Life Mortality* | Method for linking satellite environmental data to economic outcomes in developing country context |
| Carlson et al. (2012, PNAS) | Establishes palm oil as primary driver of deforestation in Borneo/Sumatra |
| Dell et al. (2014, JEL) — *What Do We Learn from the Weather?* | Review of climate-economy identification strategies; defines best practice |
| Abman & Carney (2020, JDE) | Palm oil moratorium and deforestation — close parallel to this paper's setting |
| Edwards et al. (2019, Nature Sustainability) | Palm oil and biodiversity co-location; spatial analysis approach |
| Engström et al. (2020, Global Environmental Change) | Flood-palm oil linkage in Southeast Asia; closest existing evidence |
| Margono et al. (2014, Nature Climate Change) | Indonesian primary forest loss 2000–2012; benchmark for forest data |
| Callaway & Sant'Anna (2021, JoE) | Staggered DiD estimator — required for heterogeneous timing |
| Sun & Abraham (2021, JoE) | Interaction-weighted DiD — required for heterogeneous timing |

---

## Field-Specific Referee Concerns

- **"Selection into plantation siting"** — firms choose where to expand; areas may differ systematically in topography, governance, flood history. Address with IV or geographic controls and falsification tests.
- **"Is this deforestation or plantations per se?"** — Palm oil plantations replace forests; separate the hydrological effect of forest loss from plantation-specific land management.
- **"Confounding by geography"** — Coastal/riverine areas prone to flooding may be preferred or avoided by plantation firms. DEM controls are essential; consider catchment-level analysis.
- **"Measurement error in flood outcomes"** — PODES flood reports are self-reported; satellite detection misses cloud-covered or shallow floods. Validate across data sources.
- **"Peat soils"** — Peatland drainage for plantations has distinct hydrology from mineral soils. Heterogeneous effects by soil type are expected and must be tested.
- **"Spatial spillovers"** — Upstream plantation affects downstream villages. Test whether control villages are actually unaffected using spatial Moran's I and buffer exclusions.
- **"External validity"** — Indonesian context is specific (weak governance, fire, peat). Discuss generalizability to other tropical contexts explicitly.
- **"What is the counterfactual?"** — Absent plantation, what would the land be? Intact forest vs. degraded scrub matters enormously for the hydrological comparison. Use Hansen data to characterize pre-treatment land cover.

---

## Quality Tolerance Thresholds

| Quantity | Tolerance | Rationale |
|----------|-----------|-----------|
| Point estimates | 1e-6 | Numerical precision in fixed-effects estimation |
| Standard errors | 1e-4 | Cluster-robust SE variability |
| Spatial join accuracy | ± 1 pixel | Raster-vector alignment in 30m/500m products |
