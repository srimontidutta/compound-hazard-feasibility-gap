# Worked-case records

These files expose the New York City case reported in the paper in a form that can be inspected, adapted, or used as a reference when constructing another CHFG audit.

## `nyc_actions.csv`

Six public mitigation actions from the 2024 New York City Hazard Mitigation Plan Mitigation Actions Database. The file preserves the action identifiers and the documented purposes used in the paper. The `illustrative_case_role` field records the analytical role assigned by the controlled experiment.

## `illustrative_action_model.csv`

The response library used by the experiment: protection goals, default and alternative roles, required capabilities, and normalized resource demands. These dependency and demand values belong to the analytical model.

## `scenario_assumptions.csv`

Baseline service capacities, stress-induced capacity decrements, and binary capability assumptions corresponding to the paper's scenario-assumptions table.

## `scenario_results.csv`

Scenario-level outputs for the three goal-activating single-stressor baselines and the 19 two- and three-stressor compound scenarios used for CHFG and contingency coverage. Each row records the default outcome, failure mechanism, available capacities, default demands, capability state, and a feasible permitted response when one is available.

## `sensitivity_results.csv`

The stress-severity sensitivity reported in Figure 3C. The multiplier scales the illustrative capacity decrements while baseline capacities and binary capability states remain fixed. The eligible compound-scenario denominator remains 19 across the reported range.
