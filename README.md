# Assessing the Global Military Carbon Bootprint: A Comparative Analysis of Military and Conflict GHG Emissions Against Nation-States

Where would the world's militaries rank if treated as a single country by annual greenhouse-gas emissions, and how do specific conflicts' attributable emissions compare to national emitters? This is a contextual comparison, not a counterfactual.

## Group Members
* **Reva Bhardwaj** (Working Solo)

## Question & Hypothesis
If the world's militaries were aggregated and treated as a single country, where would they rank in annual greenhouse-gas (GHG) emissions compared to recognized national emitters? Furthermore, how do the attributable emissions of specific, acute conflicts compare to the static annual baseline emissions of mid-sized nation-states?

## Summary of Analysis
This project aggregates estimated global military greenhouse gas emissions data and injects this collective entity into standard international country-level emission rankings to contextualize the true scale of global military footprints. Using Python and Pandas, I analyze the structural relationship between national military expenditures and carbon output across top global spenders to see if spending scales linearly with carbon intensity. Finally, the analysis maps out localized case studies of recent conflicts, contrasting their intense, compressed emissions spikes against the standard annual national budgets of peaceful states.

## The Notebook

Everything lives in **[`military_carbon_bootprint.ipynb`](military_carbon_bootprint.ipynb)** — a self-contained, narrative notebook with four figures:

1. **If militaries were a country** — the global military footprint (5.5 % of world emissions, SGR/CEOBS 2022) injected into the latest OWID national GHG ranking → it lands **4th–5th, ahead of Russia**.
2. **Spending vs emissions** — log–log regression of SIPRI military expenditure against national GHG across ~150 countries → strongly correlated (r ≈ 0.78) but clearly **sublinear** (slope ≈ 0.6), so spending does *not* scale one-for-one with carbon output.
3. **Whose bootprint?** — two independent allocation methods (spending share of the global estimate vs a US-DOD-derived emissions intensity) for the top-10 spenders → they disagree by ~10×, which *is* the finding: the military emissions gap.
4. **Wars as temporary emitter-countries** — annualized emissions of Russia's war in Ukraine (IGGAW) and the US post-9/11 wars (Costs of War) against the annual inventories of mid-sized countries → three years of the Ukraine war out-emits Austria's annual total; a routine Pentagon year out-emits Sweden.

## How to run

Open the repo on the Leap Pangeo hub (or any Jupyter environment with `pandas`, `numpy`, `scipy`, `matplotlib`) and run the notebook top to bottom — *Kernel → Restart & Run All*. No manual data steps: the OWID emissions dataset (~14 MB) is downloaded and cached automatically on first run; everything else is committed under [`data/`](data/) with provenance notes in [`data/README.md`](data/README.md).

## Datasets Used
* **Our World in Data — CO₂ and Greenhouse Gas Emissions** (compiled from the Global Carbon Project and Jones et al.; the same data family behind Climate Watch country rankings): [github.com/owid/co2-data](https://github.com/owid/co2-data) — country-level baseline GHG rankings, downloaded by the notebook.
* **SIPRI Military Expenditure Database:** [sipri.org/databases/milex](https://www.sipri.org/databases/milex) — national military spending (constant 2021 US$), committed at `data/sipri-milex-constant-2021-usd.csv`.
* **SGR / Conflict and Environment Observatory (CEOBS):** [Estimating the military's global greenhouse gas emissions (2022)](https://ceobs.org/estimating-the-militarys-global-greenhouse-gas-emissions/) — the global military footprint estimate (≈ 2,750 Mt CO₂e, 5.5 % of global emissions).
* **IGGAW / Ecoaction:** [Climate damage caused by Russia's war in Ukraine, 2022–2025](https://en.ecoaction.org.ua/climate-damage-3-years-numbers.html) — conflict-attributable emissions (230 Mt CO₂e over three years).
* **Brown University Costs of War Project:** [Pentagon Fuel Use, Climate Change, and the Costs of War (Crawford 2019)](https://costsofwar.watson.brown.edu/paper/pentagon-fuel-use-climate-change-and-costs-war) — US DOD fuel-use emissions and operational emission scaling factors.
