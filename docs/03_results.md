# Experimental Results Summary

| Test # | Description         | Net Flow     | X̄ Position | Notes                                   |
| ------ | ------------------- | ------------ | ---------- | --------------------------------------- |
| 001    | Uniform cube        | None         | ~0.0000 m  | Baseline for Brownian chaos             |
| 002    | Dual-wall asymmetry | Rightward    | ~+0.0300 m | Passive entropic accumulation           |
| 003    | Heat Drift Geometry | Strong drift | ~+0.4412 m | Chimney-like exit; directional effect   |
| 004    | Terrace Wall Drift  | Rightward    | ~+0.42 m   | Simulated heat rejection via reflection |

---

### Interpretation

The results suggest that **directional accumulation** can occur in completely random systems when **geometric or material asymmetries** are present — a principle that could lead to energy guiding or harvesting systems at the nanoscale.

---

### Test002 – Dual-wall asymmetry

- ![📈 plot](../results/test002_dual_wall_asymmetry_plot.png)

---

### Test003 – Heat Drift with Exit

- Extended to 10,000 steps
- Chimney-like exit defined at top-right (x > 0.90, y > 0.90)
- Significant drift detected

Output:

- [CSV log](../results/heat_drift_with_exit_positions.csv)
- [📈 Position plot](../results/test003_mean_position_plot.png)

#### Test003 Results Summary

The inclusion of an asymmetric "exit" region at the top-right corner leads to a visible shift in the mean particle positions, confirming the geometric biasing hypothesis.

![Test003 Plot](../results/test003_mean_position_plot.png)

👉 See [04_future_plans.md](./04_future_plans.md) for product applications and prototyping.

---

### Test004 – Terrace Wall Drift

- **Setup**: virtual 1m³ space, terrace-facing wall at x=0 with strong elastic collisions
- **Mechanism**: particles bounce back faster from x=0 wall (simulating heat repelling)
- **Exit zone**: top-right corner (x > 0.9, y > 0.9)

**Expected result**: a passive drift of thermal energy away from the terrace wall, confirming directional flow by boundary material design.

📊 Output:

- [CSV log](../results/test004_terrace_wall_drift.csv)

_Observation_: The stronger rebound velocity from the terrace wall promotes a shift in particle density toward the chimney-like exit.

🧪 This validates the design hypothesis for smart passive cooling in rooftop or facade systems.

---

### 🔍 Test005 – Observations

| Test ID | Name           | Description                     | Exit % (after 2000 steps) | Visual Output                                     |
| ------- | -------------- | ------------------------------- | ------------------------- | ------------------------------------------------- |
| 005     | Flow Amplifier | Chamber with directional funnel | ~36%                      | ![plot](../results/test005/test005_exit_plot.png) |

- 100 particles were simulated over 2000 timesteps.
- 36 particles exited through the funnel opening (36% efficiency).
- Exits occurred gradually but showed mild clustering after ~500 steps, suggesting potential cumulative effects.

---

↩️ [Back to top](#)  
⬅️ [Back to index](../index.md)
