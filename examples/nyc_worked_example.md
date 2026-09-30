# Worked example: NYC mitigation-action fragment

The paper constructs a small compound-feasibility stress test from six public actions in the 2024 New York City Hazard Mitigation Plan. The public records provide the action identities and documented purposes. The response roles, dependency mappings, normalized demands and capacities, stress effects, and scenario weights are analytical choices made for the experiment.

## Action library

The case uses four protection goals:

- **shelter continuity** — default mobile generator deployment (MA.00180), with a fixed school quick-connect alternative (MA.00177);
- **dewatering** — diesel pump toolkit (MA.00181);
- **critical power** — default portable generator deployment (MA.00712), with a fixed critical-site generator alternative (MA.00685);
- **emergency mobility** — contingency bus fleet (MA.00680).

The complete normalized demands and required capabilities are in [`../data/illustrative_action_model.csv`](../data/illustrative_action_model.csv).

## Scenario layer

Coastal storm, flooding, and power outage activate protection goals. Transport disruption and fuel disruption modify the operational state without introducing an additional protection goal. The base illustration uses three renewable service-capacity classes, each with 13 normalized units, together with road access, usable facilities, and communications as binary capabilities.

The stress effects are listed in [`../data/scenario_assumptions.csv`](../data/scenario_assumptions.csv). Transport disruption sets road access unavailable; the other binary capabilities remain available in the base illustration.

The default merge places the activated default responses in a common response window, so their resource demands are concurrent and the default-feasibility test does not introduce additional rescheduling. The contingency test evaluates the permitted response choices for the active goals against the same scenario state.

## Base-case results

All three goal-activating single-stressor baselines are feasible. The compound suite contains nine two-stressor scenarios and ten three-stressor scenarios. All 19 are eligible for CHFG under the base assumptions.

- Six of nine two-stressor scenarios retain default feasibility; eight retain a feasible permitted response.
- Three of ten three-stressor scenarios retain default feasibility; seven retain a feasible permitted response.
- Ten of the 19 eligible compound scenarios therefore lose default feasibility, giving \(\mathrm{CHFG}=10/19\approx0.53\).
- Fifteen of the 19 retain at least one feasible permitted response, giving contingency coverage \(15/19\approx0.79\).

[`../data/scenario_results.csv`](../data/scenario_results.csv) contains every one-, two-, and three-stressor scenario used in the case and exposes the default capacities, demands, capability state, failure mechanism, and first feasible permitted response when one exists.

## Reading the failure traces

The representative traces illustrate how the same scalar CHFG can arise from different operational mechanisms. A coastal storm combined with transport disruption disables the mobile shelter-power response through road-access loss, but the fixed school quick-connect remains feasible. Flooding combined with transport disruption leaves no listed response combination that restores all active goals. In the flooding, power-outage, and fuel-disruption scenario, the default combination exceeds shared capacity, while the fixed critical-site power option lowers demand enough to restore feasibility. A coastal storm, flooding, and transport disruption can produce capability loss and resource contention together.

These traces are collected in [`representative_traces.csv`](representative_traces.csv).

## Severity sensitivity

The sensitivity analysis multiplies every listed capacity decrement by a common factor from 0.5 to 2.0 while retaining baseline capacities and binary capability states. The eligible denominator remains 19 throughout this range. At multipliers 0.5, 1.0, and 2.0, the reported CHFG values are approximately 0.47, 0.53, and 0.84; contingency coverage is approximately 0.79, 0.79, and 0.37.

The full sequence is available in [`../data/sensitivity_results.csv`](../data/sensitivity_results.csv).
