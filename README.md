# Compound-Hazard Feasibility Gap (CHFG)

Resources for **“Compound-Hazard Feasibility Gaps in Climate Adaptation Planning”** by Srimonti Dutta and Akshata Kishore Moharir.

A response plan can pass its single-hazard feasibility checks and still lose executability when several hazards occur together. CHFG measures the weighted share of constituent-valid compound scenarios in which the **default combined response** becomes infeasible because required capabilities are unavailable, shared capacity is exceeded, or both.

## At a glance

| Illustrative case | Result |
|---|---:|
| Goal-activating single-stressor baselines | 3 / 3 feasible |
| Eligible two- and three-stressor scenarios | 19 |
| Default compositions losing feasibility | 10 |
| **CHFG** | **10 / 19 ≈ 0.53** |
| Scenarios with at least one feasible permitted response | 15 |
| **Contingency coverage** | **15 / 19 ≈ 0.79** |

The case uses uniform scenario weights. The six public action records come from the **2024 New York City Hazard Mitigation Plan Mitigation Actions Database**; the dependency model, normalized capacities and demands, stress effects, and response roles form the paper's controlled analytical experiment.

## How CHFG works

<p align="center">
  <img src="chfg-workflow.png" alt="CHFG workflow" width="760">
</p>

## Where to start

### Apply CHFG to a plan

Start with [`APPLYING_CHFG.md`](APPLYING_CHFG.md). It gives the audit sequence from action extraction and dependency mapping through constituent checks, compound feasibility, failure diagnosis, and contingency coverage.

Reusable records are available in [`templates/`](templates/):

- [`action_record.csv`](templates/action_record.csv) for plan actions, goals, capabilities, resources, and source references;
- [`scenario_record.csv`](templates/scenario_record.csv) for compound states, weights, feasibility outcomes, and failure witnesses;
- [`audit_record.md`](templates/audit_record.md) for reporting the resulting audit.

### Read the formal definition

[`SPECIFICATION.md`](SPECIFICATION.md) gives the planning objects, eligibility rule, CHFG definition, contingency coverage, failure indicators, reporting requirements, and terminology used across the repository.

CHFG is evaluated over compound scenarios whose response-triggering constituents pass their corresponding single-hazard checks. The specification also records the failure witness associated with each infeasible default composition so that capability loss and shared-resource contention can be traced to specific plan dependencies.

### Inspect the worked case

[`examples/nyc_worked_example.md`](examples/nyc_worked_example.md) walks through the New York City mitigation-action fragment used in the paper.

The supporting records in [`data/`](data/) include:

- the six source action records;
- the illustrative response model;
- scenario assumptions;
- scenario-level results;
- severity sensitivity.

## New York City source records

The public mitigation-action records provide the action identities and documented purposes used to construct the case. The controlled experiment then assigns protection goals, default and alternative roles, capability dependencies, normalized resource demands, scenario-conditioned capacities, and stress effects.

The repository keeps the source records and analytical assumptions separate so that the worked example can be inspected directly.

The public action records are drawn from the [New York City Hazard Mitigation Plan Mitigation Actions Database](https://nychazardmitigation.com/documentation/mitigation/actions/).

## Reusing CHFG

A new CHFG application needs four ingredients:

1. a response plan;
2. a compound-scenario family;
3. an explicit model of required capabilities and shared resources;
4. a declared rule for combining constituent responses.

Scenario weights may represent a uniform stress-test design or, when defensible joint probabilities are available, a specified planning distribution or climate horizon.

A CHFG audit reports constituent coverage, CHFG, contingency coverage, and the capability or resource witnesses associated with failed default compositions. These outputs show where separately workable responses cease to compose and which permitted alternatives preserve coverage.
