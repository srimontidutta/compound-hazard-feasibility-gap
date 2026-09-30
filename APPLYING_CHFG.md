# Applying CHFG to an adaptation or hazard-mitigation plan

CHFG can be applied before a plan has been encoded in a specialized planning language. The practical task is to represent enough of the response logic, operational dependencies, and compound operating state to test whether separately feasible responses remain jointly executable.

## 1. Select the plan fragment

Choose the protection goals and documented actions relevant to the hazards under study. Preserve source identifiers and record the owners, facilities, backup actions, and operating conditions stated in the plan. The source record and the analytical model should remain distinguishable throughout the audit.

[`templates/action_record.csv`](templates/action_record.csv) provides a starting structure.

## 2. Map operational dependencies

For each action, identify the capabilities that must remain available and the shared resources consumed while the action is active. Depending on the plan, these may include road or facility access, communications, grid service, fuel support, response teams, specialized equipment, transport capacity, or other jointly constrained services.

Operational records can supply these values when they are available. Analytical assumptions can also be used for stress testing, provided they are identified as such and applied consistently across constituent and compound checks.

## 3. Define the scenario family

Separate stressors that activate protection goals from disruptions that alter the operating state. Each evaluated scenario should specify:

- active stressors;
- response-triggering constituents;
- active protection goals;
- capability availability;
- renewable-resource capacities over the response window;
- the analysis weight, when weighted evaluation is used.

[`templates/scenario_record.csv`](templates/scenario_record.csv) can be adapted to the scenario representation used by the application.

## 4. Validate constituent responses

Evaluate each response-triggering hazard in its corresponding single-stressor state. Record constituent coverage before computing CHFG. The eligible compound set \(\mathcal C^+\) contains scenarios whose relevant constituent responses pass these checks.

This step establishes the baseline needed to distinguish a composition failure from a response that was already infeasible in isolation.

## 5. Declare the merge rule and test the default composition

Specify how the constituent responses are combined when their triggering hazards occur together. Preserve internal temporal and precedence constraints and make cross-response timing or synchronization choices explicit enough for a reproducible feasibility check.

For each eligible compound scenario, evaluate whether the default composition retains required capabilities, respects shared renewable-resource capacity, and achieves all active protection goals.

## 6. Retain the failure witness

For each failed default composition, record the capability and resource mechanisms that explain the failure. A scenario can contain a disabled required capability, an overloaded shared resource, or both.

The witness is often the most actionable part of the audit because it identifies the dependency or capacity that prevents the constituent responses from composing.

## 7. Evaluate permitted alternatives

When the plan contains alternatives, define the response combinations that are permitted for the active goals and evaluate them in the same scenario state. Contingency coverage uses the same eligible set as CHFG and records the share for which at least one permitted response remains feasible.

## 8. Report the audit

A compact application report includes constituent coverage, CHFG, contingency coverage, the evaluated scenario family and weighting rule, failure witnesses, feasible alternatives, and any protection goals that remain unmet. [`templates/audit_record.md`](templates/audit_record.md) provides a reporting structure.

For climate-horizon applications, the same plan representation can be reevaluated as evidence changes scenario weights and, where projections support it, scenario-conditioned capabilities or capacities. This allows changes in compound hazard conditions to be translated into changes in plan executability while the response plan itself is held fixed.

## Suggested working sequence

1. Fill [`templates/action_record.csv`](templates/action_record.csv) from the source plan.
2. Add the capability and resource model used for the audit.
3. Build single and compound scenario records with [`templates/scenario_record.csv`](templates/scenario_record.csv).
4. Validate constituent responses and identify \(\mathcal C^+\).
5. Evaluate default compositions and retain their failure witnesses.
6. Evaluate permitted alternatives and compute contingency coverage.
7. Summarize the audit with [`templates/audit_record.md`](templates/audit_record.md).

The New York City worked example in [`examples/nyc_worked_example.md`](examples/nyc_worked_example.md) shows the same sequence in the controlled case reported in the paper.
