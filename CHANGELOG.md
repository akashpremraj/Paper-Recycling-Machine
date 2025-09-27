# Changelog
All notable changes to this project will be documented in this file.

The format is based on **Keep a Changelog** and this project aims to follow **Semantic Versioning**.

## [Unreleased]
### Added
- (placeholder) Auto slurry feed prototype
- (placeholder) Closed-loop dryer control (PID)
- (placeholder) Wider-web frame investigation

---

## [1.1.0] - 2025-09-28
### Added
- Overhauled `README.md` (Project Overview, Process Flow with Mermaid, Drive/Speed calcs, Press calcs, Timeline, Results & Reflection, Mini Testing Log, Advantages, Limitations, Scope, Author’s Note, References)
- `docs/safety-and-risks.md` (hazard table, daily checklist, emergency actions, maintenance cadence)
- `docs/sop_operations.md` (pre-start, start-up, operation, shutdown, cleaning, faults)
- `docs/press-calcs.md` (cylinder → line load, nip pressure)
- `docs/testing_log.csv` (template) and **Mini Testing Log** section in README
- `docs/bom_costs_2020_INR.csv` (itemised prototype costs; fixed CSV quoting)
- `CODE_OF_CONDUCT.md`, `.github/ISSUE_TEMPLATE.md`
- `CITATION.cff` (repository citation metadata)
- `images/process-flow.png` fallback and enlarged Mermaid diagram

### Changed
- README sections polished; consistent engineering language and UK/NHS-friendly impact bullet
- BOM filename from `bom_costs.csv` → `bom_costs_2020_INR.csv` and references updated

### Fixed
- CSV preview warnings due to commas in fields (quoted offenders; corrected totals rows)
- Minor arithmetic for nip pressure (now ~3.3 MPa with given inputs)

## [1.0.0] - 2020-07-08
### Added
- Initial BE project repository: basic README, early images, and report link

