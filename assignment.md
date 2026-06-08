## Track G — Predictive Maintenance for Industrial Machines

### The Story

**FactoryPulse** operates multiple manufacturing plants with production lines
that run around the clock.  Each line depends on rotating machinery —
compressors, conveyor motors, pumps — whose failure can halt an entire
production sequence within minutes.  When a machine breaks down without
warning, the repair cost is only part of the problem: the lost production
time, the scramble for emergency parts, and the downstream knock-on effects
can multiply the actual cost several times over.

The reliability engineering team collects sensor readings, maintenance logs,
and operational parameters for each machine on a rolling basis.  Their goal
is a 30-day failure horizon model: given a snapshot of a machine's current
state, how likely is it to fail within the next month?  If the model flags
a machine early enough, a preventive maintenance window can be scheduled
during a planned downtime slot, avoiding the chaos of an unplanned breakdown.

For FactoryPulse, the value of the model depends entirely on how it is used
in practice.  A score assigned to each machine only becomes useful when it
is converted into a maintenance decision — and that decision carries real
financial consequences either way.  Your task is not just to build a model
that predicts well in the abstract, but to propose a concrete policy for
how the reliability team should act on it, and to defend that policy in terms
of the operational trade-offs the company faces.

### Dataset Files

| File | Rows | Columns | Target |
|---|---|---|---|
| `track_g_predictive_maintenance_train.csv` | 1300 | 13 | `failure_30d` |
| `track_g_predictive_maintenance_test.csv` | 350 | 13 | `failure_30d` |

### Feature Reference

| Feature | Type | Range | Description |
|---|---|---|---|
| `machine_age_years` | float | 0.5–18 | Age of machine in years. |
| `operating_hours_week` | float | 20–120 | Weekly operating hours. |
| `temperature_c` | float | 35–105 | Average operating temperature. |
| `vibration_rms_mm_s` | float | 0.8–10 | RMS vibration measure. |
| `vibration_peak_mm_s` | float | 0.5–18 | Peak vibration measure. |
| `pressure_bar` | float | 2–14 | Operating pressure. |
| `load_factor_pct` | float | 40–110 | Relative load factor percentage. |
| `maintenance_delay_days` | int | 0–60 | Days of delay vs maintenance schedule. |
| `prior_failures_12mo` | int | 0–3 | Number of failures in last 12 months. |
| `operator_experience_years` | float | 0–20 | Experience of assigned operator. |
| `ambient_humidity_pct` | float | 20–95 | Ambient humidity around the machine. |
| `shift_code` | int | 1–3 | Shift identifier. |
| **`failure_30d`** | binary | 0/1 | **Target: 1 = failure within next 30 days.** |