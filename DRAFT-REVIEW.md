# Indian Head Road — first-draft review

Prepared September 8, 2026. Local editorial record; not a client report page.

## Draft scope

Updated project metadata and narrative configuration; rewrote the summary, energy-model, envelope, windows, and mechanical narrative; added a Connecticut code/scope section; replaced five townhouse assembly cards with eight project-specific cards; corrected case-sensitive references for all four ventilation plans. Existing model data, source workbooks, diagrams, publication settings, and workflow pins were preserved. No commit, push, or deployment was performed.

## Review priorities

1. **Revised recommendation (owner direction):** `project.yaml` now overrides the generated manifest with `enerphit_by_component`. Target EnerPHit component performance for feasible renovation work; do not pursue actual certification because of retained fireplaces and the inaccessible cellar/crawlspace floor. The current component model still assigns R-10 to the remaining cellar floor; revise the correct area to retained uninsulated construction and re-scrape. Current comparison: 42.138 kWh/m²·yr heat demand, 24,636 kWh/year site energy, 1.0 ACH50, U-0.1585065 IP windows. Numeric results are explicitly provisional for the revised construction scope.
2. **Climate naming/elevation:** Verification K10 and Climate D25/D77 identify Greenwich CT (Passipedia); Climate D12 and sheet header strings still say Bridgeport. Active monthly values match the Greenwich table. Climate D17/D18 use 92.6 m elevation. Confirm dataset identity, acceptance, and project elevation before final model issue. No workbook changes made.
3. **CO₂ factor is inherited NYC:** Data P20 is `NYC eGrid (2020)`; PER Y21 / Data F36 = 0.28785456 kg CO₂e/kWh. Replace/verify in PHPP for the appropriate Connecticut region and year, then re-scrape. Merely changing the YAML region name would not correct the charts. The draft labels the current factor honestly. Also inspect auxiliary CO₂: the export implies roughly twice the per-kWh factor used for heating. Do not issue the carbon total as verified until reconciled.
4. **Occupancy:** Verification F30 = 3.5119951888220493. Stored as model occupancy, not an assertion about household members. Confirm intended household/guest capacity for ventilation and whether to retain the illustrative 1 ton/person carbon benchmark. No household research included in the client report.
5. **Existing export errors:** `r_values.assembly_*` rows contain `#DIV/0!`; `peak_loads.peak_latent_cooling_load` contains `#VALUE!` for all five variants. Annual latent demand is zero. Prose does not infer zero dehumidification need. The explicit envelope table uses valid `envelope.*` variant rows and the project PDFs. Correct the workbook/export fields and re-scrape before final issue.
6. **Appliance energy:** Cooking and dedicated lighting entries are zero in all variants. Confirm whether counted elsewhere or omitted before presenting site-energy totals as a complete household budget. No existing-condition baseline or PV credit is present.
7. **Assembly drawings versus targets:** Component variant retains the supplied as-drawn roofs, insulated walls, cellar walls, garage ceiling and insulated cellar floor. Other above-grade wall increases from R-12.8 to R-18. Remaining floor changes from R-1.4 to R-10 in the model, but that upgrade is not feasible and is excluded from the recommended work. Confirm area assignment and update the model. Reconcile the small metal-roof U/R annotation discrepancy and garage R-31.6 drawing versus R-31.7 input.
8. **Window specification:** Drawing schedule uses Marvin Ultimate/Magnum nomenclature and U-0.29 / SHGC-0.27, while current As-Drawn PHPP uses U-0.220 / SHGC-0.40. Do not describe the current As-Drawn model as an exact transcription of the original schedule. Recommended component window average is U-0.1585065 IP. Final unit sizes, frame/glass data, and installation psi-values still need schedule reconciliation.
9. **Window comfort:** Climate W49 = -12.5°C and W50 = 0.936 W/m²K, approximately U-0.165 IP / R-6.07. These are PHPP-derived comfort values, not ASHRAE design weather. ASHRAE fields remain null rather than borrowing an unrelated temperature.
10. **Ventilation:** Addl vent N13 is `test_ventilator`; no actual ERV selected. The active workbook demand case has ERV effective recovery V13 = 80.6989% and whole-system V24 = 76.4589%. The recommended component variant instead has 72.6222% whole-system recovery and 25 mm cold-duct insulation; do not carry the active demand-case unit efficiency into component selection. Schedule unit 1 is 300/275 cfm high and 231/211.75 cfm medium; imbalance is 8.33% of supply. Low speed is zero throughout. Sunroom, cellar rooms, and `218-GUES BATH` have no assigned flow. Verify intended transfer zones and room occupancy. Hood ON is a separate unit-2 allowance of 623.892 cfm supply/extract, not continuous ERV flow. Plans are zoning/airflow graphics, not duct plans.
11. **Radiation graphics:** Reviewed winter and summer images visually. Legends say kWh but omit period and area normalization. Draft discusses relative exposure and uses the PHPP solar balance for annual numbers. Confirm GH analysis period/units before adding quantitative image captions. The new Resilience page uses separate EnergyPlus results, not these solar graphics.
12. **Code:** Working basis is 2022 CT SBC / 2021 IECC as amended, CZ 5A. Confirm actual permit application date and compliance route. CT R502.3.1 explicitly exempts addition envelope assemblies from R402.4.1.2 testing. Do not impose the whole-house code comparison as the legal scope of alteration work. Window U-0.30 is the base prescriptive reference subject to table exceptions, not the modeled average U-0.271.

## Source map

- `../07_PHPP/2619-Indian-Head-Rd-260908.xlsx`, PHPP 10.6; read-only cached values and focused formula inspection.
- `data/manifest.json`: export timestamp 2026-09-08T17:01:31.105652Z, source SHA-256 8cabb0bf55b3cfee0b29323e0eb8257a7552f254daf1359d40b6c00c6f72a2cb.
- `data/variants.csv`: envelope rows 328–336; ACH50 344; certification result/limit field IDs; report_inputs total_site_energy; peak_loads; co2e. Use source labels, not positional legacy field names (`envelope.floor_bg` actually labels New Metal Roof here).
- `data/building-metrics.csv`: TFA 6587.461 ft²; envelope area 18334.919 ft²; test volume 60224.653 ft³.
- `data/room-airflows.csv`: room allocations and unit totals.
- `public/assets/envelope/assemblies/*.pdf`: eight project Flixo studies dated September 8, 2026.
- `public/assets/mechanical/plans/Level_00` through `Level_03`: four supplied floor graphics/PDFs.
- `../01_Reference/260818 Drawing Set/indexed/40 Indian Head Road 260817/index.md` and sheet reading files: Granoff permit issue June 16, 2026. `../01_Reference/260901 CAD files`: dated CAD intake, not independently verified delivery timestamp.
- `../02_Admin/Contract/PROJECT-BRIEF.md`: project/team context only; older indicative envelope conclusions superseded by the current model. Personal/financial background excluded from report.

## External references checked September 8, 2026

- [CT adopted code editions](https://portal.ct.gov/en/das/office-of-state-building-inspector/connecticut-state-building-code/regulations).
- [CT amendments](https://portal.ct.gov/-/media/DAS/Office-of-State-Building-Inspector/2022-State-Codes/2022-CSBC-Final.pdf): PDF pages 103–105, residential energy amendments, especially R402.4.1.3 and R502.3.1.
- [ICC base fenestration table](https://codes.iccsafe.org/s/IRC2021P3/part-iv-energy-conservation/IRC2021P3-Pt04-Ch11-SecN1102.1.2): CZ5 U-0.30 and exceptions.
- [PHI criteria](https://passiv.de/downloads/03_building_criteria_ip_en.pdf): retrofit framework. Final criteria edition and certification scope remain for project confirmation.

## Intentionally unfilled configuration

Unused Phius limits, component-route U-value limits, ASHRAE temperatures, a specific weather-station URL, and ERV manufacturer/model/link remain null. The client narrative does not render these as placeholder claims. PER 101 is the current component-path workbook limit, not a universal EnerPHit allowance. The demand heating-limit YAML value is now null because it is not the recommended route. The climate name, window comfort values, and carbon factor are separately qualified in prose.

## Verification

Revised project schema/content validation, static build, and 68-page PDF build passed. Browser review confirmed EnerPHit By Component on the Summary and all four Recommended badges on Energy Model, the restored Mechanical sections/images, and the Resilience route/navigation/plots. No browser errors observed. Checked all 64 unique root-relative links in the built report; none missing. Visually inspected PDF pages 65 and 67: summer/winter plots and captions render legibly without clipping. Existing latent-load export errors remain disclosed. No model files or scrape-owned data were edited.

## Revision: Mechanical and Resilience

Mechanical detail restored using the current Doppelt example as an editorial reference: supply/transfer/extract rationale, independent distribution, Q600/equivalent selection study, filtration, detailed commissioning, makeup-air diagram and supplier links, retained fireplace pressure coordination, and environmental/circuit monitoring with supplied images. No equipment is represented as selected.

Resilience registered as a custom page with three sections and project-specific vector plots plus exact downloadable CSVs. All 216 hourly values in each of five zones, summer and winter, verified against the respective current EnergyPlus SQL (tolerance 1e-6). Provenance and hashes: `public/downloads/resilience/source-notes.json`. Plots show full nine-day sequences, shading rows 24:192 as the intended outage. CSV helper year 2016 differs from SQL years; charts use elapsed days. Winter source HTML has different SET values and was deliberately not used.

Winter outage minimum SET is 13.8608°C (56.95°F), zero degree-hours below 54°F; HVAC energy meters are zero during Jan20–26. Summer upper-zone peak Heat Index is 42.9885°C (109.38°F); each upper zone has 12 hourly values in the 39.4–51.7°C Danger band. **Summer district heating and cooling meters are nonzero during Jul27–Aug2**. Review residual HVAC/humidity control before claiming passive survivability. Ground temperatures/enclosure/thermal mass and mapping to the revised PHPP component variant remain unresolved. Do not treat the warm cellar as a verified refuge or infer full REVIVE compliance.

Plots generated with matplotlib from unchanged verified CSVs; no comfort calculation was reimplemented. First reference is [Phius REVIVE 2024 standard v24.1.1](https://www.phius.org/phius-revive-2024-standard-document).

## Whole-building prose units

Converted specific annual demand and certification-limit prose to whole-building kWh/year using the exact variant TFA (611.995188822 m²) and unrounded model results, rounded to the nearest 100 kWh for presentation. Peak loads use Btu/h. PER remains explicitly distinguished from purchased electricity. Geometry prose uses US customary units; window U-values retain their US performance units. Corrected the summer narrative from the previous demand-case 2,549 kWh/year to the recommended component-case 1,948 kWh/year sensible cooling demand. Generated model data and chart/table unit controls remain unchanged.

## Doppelt Resilience presentation match

Reviewed the current `2617 Doppelt Home/04_Web/content/custom/resilience` and matched its assessment/criteria table, seasonal result callouts, explanatory subsections, design recommendations, three interactive plots per season, and supporting-detail links. Indian Head Road conclusions remain independent. Main plots now use Fahrenheit for Heat Index/SET/air temperature and percent for RH. All six plots are refreshed directly from current hourly SQL values, including outdoor air temperature/RH; exact plot JSON and provenance are retained in `public/downloads/resilience`. Original diagnostic detail exports are linked with an explicit snapshot qualification.

Web plots use Doppelt's responsive enhancement and Plotly convention. PrintableEmbed supplies deterministic vector versions for all six plots. PDF build passed (74 pages). Summer deadly days remain unassessed; winter SET checks pass in the supplied series but no full compliance finding is made.

## Revision: five variants, As-Drawn recommended (September 10, 2026)

The PHPP was reworked to five variants (Code Minimum, As-Drawn, EnerPHit By Component, PHI Low Energy Building, EnerPHit By Demand) and re-scraped from `2619-Indian-Head-Rd-260910.xlsx`. The separate "Recommended" variant is gone; As-Drawn now carries 1.0 ACH50, LePage windows at U-0.20, a 20% thermal-bridge allowance, R-12.8 at the walls without exterior insulation, the crawlspace floor at R-1.4, and 72.6% whole-system heat recovery. `project.yaml` sets `recommended_variant_id: as_drawn`; the R-18 wall upgrade and the 15% allowance moved from the recommendation to the EnerPHit By Component comparison. All prose figures were rewritten from the new scrape: heat demand 58,150 / 41,290 / 25,790 / 17,810 / 15,160 kWh/yr; site energy 47,060 / 33,770 / 25,010 / 20,430 / 18,340 kWh/yr; As-Drawn PER 42,260 against 85,070; peak heat 59,530 Btu/h, sensible cooling 17,070, latent 9,690 (the latent export error is gone; `r_values.assembly_*` still exports `#DIV/0!`). Operating CO₂e excluding the 3.51 t reference line: 11.6 / 8.3 / 6.2 / 5.0 / 4.5 t.

Items to check before issue: (1) The thermal-bridge line falls from 15,420 to 5,442 kWh/yr between As-Drawn and EnerPHit By Component. A 20% to 15% allowance change on the transmission losses accounts for roughly 3,000 kWh/yr of that; As-Drawn and Code Minimum carry about 100 W/K of thermal-bridge loss beyond their percentage allowance, the other three variants about 5 to 11 W/K. The prose attributes the full 10,000 kWh/yr step to EnerPHit-level junction detailing; confirm what else changes in the variant's thermal-bridge inputs. (2) The certifications section says As-Drawn is "at or near" the cool-temperate component targets; strictly, the R-34.5 wall is U-0.165 W/m²K against a 0.15 limit and the 72.6% heat recovery is below the 75% criterion, and the EnerPHit By Component variant carries the same wall and unit.
