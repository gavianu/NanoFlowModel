# Experiment Log

## Test 001: Brownian Cube – Uniform Walls

- **Date:** June 18, 2025
- **Repo:** `vortex-box-test`
- **Setup:** All walls reflective. No asymmetry.
- **Outcome:** Uniform distribution. X̄ ≈ 0.0000 m

## Test 002: Brownian Cube – Dual Wall Behavior

- **Date:** June 18, 2025
- **Left walls:** Fully reflective
- **Right walls:** Absorbing (velocity dampened)
- **Result:** ~60–70% particles accumulated in right side
- **X̄:** ≈ +0.03 m
- **Insight:** Geometric asymmetry alone caused spatial bias.

## Test 003 – Heat Drift Geometry (Smart Passive Cooling)

- **Date**: June 18, 2025
- **Type**: Conceptual prototype for passive thermal drift
- **Setup**:
  - 3D rectangular room (~1m³ virtual space)
  - Left wall: reflective
  - Right wall: absorbent
  - Top corner: open drift zone ("chimney exit")
- **Particles**: Simulated air molecules (Brownian agents)
- **Hypothesis**:  
  A geometrically biased interior will passively shift particles (thermal energy) toward an exit zone, simulating passive cooling through boundary-driven accumulation.

- **Expected behavior**:  
  Net drift of particles toward the right-upper corner, where exit/absorption occurs — even without external gradients.

- **Goal**:  
  Demonstrate that asymmetry + boundary design can produce thermal biasing usable in tiny/smart homes.

  ***

### Test004 – Terrace Wall Drift (Passive Thermal Repulsion)

- **Date**: June 19, 2025
- **Type**: Digital simulation (from `vortex-box-test` project)
- **Objective**: Evaluate if a terrace-facing reflective wall can induce passive thermal drift
- **Geometry**:

  - 1 m³ virtual box
  - Reflective wall at x = 0 (simulated elastic rebound amplification)
  - Open "exit zone" at x > 0.9 and y > 0.9

- **Key Insight**:
  Elastic acceleration on one side promotes particle movement toward the exit, replicating a cooling effect
  through spatial bias — without any external energy input.

- **Results integrated in**:
  - [Results summary](03_results.md#test004--terrace-wall-drift)
  - [Future plans](04_future_plans.md#smart-passive-wall-cooling)

[↑ Back to top](#)  
[← Back to index](../index.md)
