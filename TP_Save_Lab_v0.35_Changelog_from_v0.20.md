# TP Save Lab v0.35: changes since v0.20

v0.35 covers everything from the v0.20 stable release through the v0.35 working build and all the MergedTabs work up to 2026-10-07. It is still one self-contained HTML file. Your save is processed locally and never uploaded.

---

## General

- **New name.** TP Save Viewer / TP Save Editor is now **TP Save Lab**.
- **Loading.** The drop zone is larger, and you can drop a `.json` save anywhere on the start screen. Once a save is loaded, dropping is turned off so it doesn't interfere with the editors.
- **Tabs.** The 15 tabs are now 10:
  - PERFORMANCE · PROJECTS · WAREHOUSE · FITTED PARTS · HEADQUARTERS · ELECTRONICS · DRIVERS · STAFF · SUPPLIERS · CHAMPIONSHIP
  - Merged tabs have a second row of views:
    - Performance: Trend / Table
    - Drivers: Database / Contracts / Juniors
    - Suppliers: Contracts / Performance
    - Championship: Standings / Results
  - The tab bar starts pinned open.
- Overall typography improvements
- Contract seasons are shown as years: "2000–2002 · 3 years".
- **Rebranded teams.** A team shows its current name everywhere (for example Stewart → Jaguar, British American Racing → BAR). Past race results keep the name the team had at the time.
- Every search box matches word by word, so "toyota main" and "pay driver" work.
- Part types, project categories, supplier categories, team names, abbreviations and junior series all come from the loaded save, so mods with different parts or teams display correctly.
- Long notes and footers moved into each tab's "?" help, which uses 12px text. Editor "?" tooltips use the app's own popup.

## Save safety

- Every edit is tracked, can be undone, appears in the Editor's Log, and is reviewed before download.
- An edit is rolled back only if it adds a new error. Download stays blocked while any error remains.
- **New download blockers.** 
  - a team with no current-season supplier in a category;
  - a supplier slot with two contracts for the same season;
  - a driver with two contracts for the same season;
  - more than 2 main drivers or more than 1 reserve at a team;
  - a race car with no main driver after a release.

## Performance

- Gains are capped at the chassis potential for each stat. Capped cells say so.
- Hovering a Current stat shows the baseline, each gain in order, and the total.
- **Overall** = (100 + the eight car stats) ÷ 9, minus 1 point per 27 kg above minimum weight. Hover the header for the formula.
- **Trend and Table now agree on every stat.** Before, 484 of 1,716 checks differed.
- **Spec B/C/D chassis** count as a new base car from the week they finish, as in the game's Car Ratings screen.
- Several graph errors were fixed: mass counted twice, empty aero history entries, and history from other seasons.
- The Trend and Table update straight after any edit; before, they needed a reload.
- **Car baseline editor** (new): an EDIT button next to each team opens it.
  - It edits the Baseline (week 0) and the Cap (potential), and shows "Developed now" live as you type.
  - It writes what the game's own baseline edit writes.
  - A fitted Spec chassis is never changed by it.

## Projects

- New column order. Gains are labelled **PERFORMANCE GAINS** and include an Overall gain.
- Sorting: Completed → Development → Design → Prototype → Concept, with higher progress first within each stage.
- **Project editor:**
  - It edits completed and in-design chassis and aero projects. Concept-stage projects stay read-only.
  - Each value has − and + buttons in steps of .10 / .50.
  - Limits: no negative gains, aero up to +10, chassis up to +20, ratings 0–100, mass ±20 kg.
  - In-design projects show a progress bar.
  - Chassis projects show their stats in two columns.
  - Undo and Apply sit side by side.
- Force Complete Next Week is available for aero upgrades, chassis development packages, and next year's chassis in Design. The game finishes the project at the next week advance, at full return. Spec B/C/D are excluded.
- Next year's chassis can be edited with Start and Cap columns, whether finished or still in design.
- **Engine editor** (new):
  - This year and next year side by side, with steps of 0.5.
  - This year's edit updates the supplier, every team's contract and every built engine. Each team's contract penalty is applied, read from the save.
  - Next year's edit updates the target that the season change copies.

## Warehouse and Fitted Parts

- Replaced dropdown selection with seletion buttons, for parts and teams.
- Fitted Parts now displayed correctly, for each car.

## Headquarters

- Revamp layou
- Each facility shows only the effect stored in the save, at its current level:
  - Wind tunnel: "Concept ×1.075"
  - CFD centre: "Baseline +5.0%"
  - Engine plant: "Gains ×1.036 · Weight ×0.97"
  - Test track: "Testing $500/lap"
  - Facilities with no stored effect show none.
- Upkeep and degradation are shown on each card, if available for that building.

## Electronics

- The all-teams grid has one box per team with Driver aids and ERS rows. It fits without side scrolling down to a window about 1,100px wide.
- The level in development is outlined in gold.
- Cards show Work done and Staff assigned (+N/week).
- No research requirement is assumed. The fixed 3000/2000/1000 targets are gone.

## Drivers, Staff and Juniors

- **Overall rating** is shown on selectors and seat bubbles:
  - Drivers: the five driving skills.
  - Staff: the average of their skills.
  - Juniors: Overall, with Talent in brackets.
- Juniors show AGE and TALENT in the side panel.
- Contract bubbles share one style across Drivers, Juniors, Staff and Suppliers: 14px names, a team colour stripe, and a fixed rating column.
- **Negotiations** (Drivers and Staff):
  - Filters: All / Ongoing / Complete. Rows can be searched and sorted.
  - Each row shows Status, Term, Interest and the decision week.
  - Only negotiations for future seasons are listed.
  - A completed signing reads **SIGNED** and has a CANCEL CONTRACT button.
  - END NEGOTIATION removes only that one driver↔team or staff↔team negotiation.
- **Signing by drag and drop:**
  - Drop a driver or staff member onto an empty seat or position, for this season or next.
  - A "Sign <name>" window opens with Status, Term, Salary and bonuses. The salary is pre-filled from an open offer or from similar contracts.
  - Nothing is written until you press Sign.
- **Mid-season moves:**
  - Sign a reserve driver or a staff member, starting this week.
  - "Release driver now" frees a contract.
  - A freed main seat can be filled, and the new driver takes over the car and its fitted parts.
- **Contracts end at a season end.** Choose "End of <year>". Contracts that the data pack stores with a mid-season end keep it.

## Suppliers

- Opens on **Contracts**.
- **Contracts:**
  - Same page layout as Drivers and Staff.
  - Drag a supplier onto a slot of its own part type to start a contract; nothing is written until you confirm.
  - The edit panel uses the same steppers.
  - The term shows years and length on two lines.
- **Negotiations:** team colours, text that folds onto a second line, and terms shown as years.
- **New future engine contracts** hold only the fields the game writes. This fixes the "circular reference" error and stops other teams' settings being copied in.
- **Engine supplier list** shows supplier names only. Acquired suppliers count as inactive.
- **Performance:**
  - Categories come from the save.
  - Text sizes match the Performance Table; supplier names are in capitals and team names are 12px.
  - The type selector wraps onto more rows instead of scrolling.
  - Inactive suppliers are greyed and marked "(INACTIVE)".


