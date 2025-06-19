# 05 – Theoretical Framework and Simulation Model

## 🎯 Purpose

This section provides the theoretical foundation for the experimental simulations performed in NanoFlowModel. The goal is to describe how particle behavior can be mathematically modeled and numerically implemented to simulate Brownian drift in asymmetric environments.

The experiments are based on the assumption that **geometry and material boundaries** can influence particle dynamics at the microscopic level — a hypothesis that we aim to explore through both simulation and future physical prototyping.

## 🌊 Brownian Motion and Thermal Agitation

Brownian motion describes the random movement of particles suspended in a fluid, caused by collisions with the much smaller, fast-moving molecules of the medium. The phenomenon was first observed by botanist Robert Brown in 1827 and later explained theoretically by Einstein in 1905.

In NanoFlowModel, we simulate Brownian-like particles (also called _agents_) that undergo constant, small, random displacements, mimicking this chaotic interaction — even though we use simplified rules to approximate it computationally.

Key concepts:

- Motion is **random** but statistically predictable.
- Energy is **conserved** on a macroscopic average.
- Local directionality can emerge from **boundary design**.

## 🧮 Mean Squared Displacement (MSD)

The spread of particles due to Brownian motion is described statistically using the **mean squared displacement**:

### LaTeX form:

$$
\langle x^2(t) \rangle = 2 D t \quad \text{(1D)}, \quad \langle r^2(t) \rangle = 6 D t \quad \text{(3D)}
$$

### Notebook-style:

⟨x²(t)⟩ = 2 · D · t  (for one dimension)  
⟨r²(t)⟩ = 6 · D · t  (for three dimensions)

Where:

- ⟨x²(t)⟩ is the mean squared displacement
- D is the diffusion coefficient
- t is time

The MSD grows linearly with time, which is a signature of diffusive behavior.

In our simulations:

- Time steps are counted in arbitrary units.
- Drift is detected if the net motion deviates **directionally** (e.g. higher mean X or Z over time).

## 🔬 Diffusion Coefficient – Stokes–Einstein Relation

For a spherical particle in a viscous fluid, the diffusion coefficient \( D \) is given by the **Stokes–Einstein equation**:

### LaTeX form:

$$
D = \frac{k_B T}{6 \pi \eta r}
$$

### Notebook-style:

D = (k_B · T) / (6 · π · η · r)

Where:

- D is the diffusion coefficient
- k_B is Boltzmann’s constant
- T is absolute temperature
- η is dynamic viscosity
- r is the particle radius

This equation shows:

- **Higher temperature** increases diffusion
- **Larger particles or more viscous fluids** slow down diffusion

In simulation:

- We assume uniform values (unit particles, unit viscosity)
- \(D\) becomes a normalized parameter

## ⚛️ Maxwell–Boltzmann Velocity Distribution

In real gases, particles follow a velocity distribution depending on temperature:

### LaTeX form:

$$
f(v) = \left( \frac{m}{2 \pi k_B T} \right)^{3/2} \cdot 4 \pi v^2 \cdot e^{- \frac{m v^2}{2 k_B T}}
$$

### Notebook-style:

f(v) = (m / (2 · π · k_B · T))^(3/2) × 4 · π · v² · e^( - m·v² / (2·k_B·T) )

Where:

- f(v) is the probability density
- m is particle mass
- v is speed
- T is temperature
- k_B is Boltzmann constant
- e is the base of natural logarithms

This function tells us that:

- Most particles have a **moderate speed**
- Some move **very fast** or **very slow**

In simulation:

- We assign constant speed or random small variations.
- Velocity is normalized (e.g. 1 unit/step).
- No temperature dependency is currently used — but it can be added.

## 🔄 Langevin Equation – Brownian Motion with Friction

The Langevin equation is a stochastic differential equation that models the motion of a particle under both friction and random thermal forces:

### LaTeX form:

$$
m \frac{d^2x}{dt^2} = -\gamma \frac{dx}{dt} + \sqrt{2 \gamma k_B T} \cdot \xi(t)
$$

### Notebook-style:

m · d²x/dt² = – γ · dx/dt + sqrt(2 · γ · k_B · T) · ξ(t)

Where:

- **m** = mass of the particle
- **γ** = friction (or damping) coefficient
- **k_B** = Boltzmann constant
- **T** = temperature
- **ξ(t)** = random (white noise) force with ⟨ξ(t)⟩ = 0

### Interpretation:

- The first term on the right (–γv) represents viscous drag
- The second term represents **thermal fluctuations**
- The balance of these forces results in **Brownian motion with dissipation**

### Notes for Simulation:

In NanoFlowModel, we simplify:

- Discrete steps (no time derivatives)
- No mass or friction terms directly used
- Thermal randomness is represented by random direction changes

This equation underlies more detailed simulations in molecular dynamics or thermodynamic systems and justifies why particles in our model behave chaotically without external gradients.

## 🧪 Fokker–Planck Equation – Probability Density Evolution

The Fokker–Planck equation describes how the **probability density function** \( P(\vec{r}, t) \) evolves over time in systems with stochastic motion, such as Brownian diffusion.

### 📏 1D Form:

$$
\frac{\partial P(x, t)}{\partial t} = D \cdot \frac{\partial^2 P(x, t)}{\partial x^2}
$$

📓 Notebook-style:
∂P(x, t)/∂t = D · ∂²P(x, t)/∂x²

---

### 📐 2D Form:

$$
\frac{\partial P(x, y, t)}{\partial t} = D \cdot \left( \frac{\partial^2 P}{\partial x^2} + \frac{\partial^2 P}{\partial y^2} \right)
$$

📓 Notebook-style:
∂P(x, y, t)/∂t = D · (∂²P/∂x² + ∂²P/∂y²)

---

### 🧊 3D Form (used in our simulations):

$$
\frac{\partial P(x, y, z, t)}{\partial t} = D \cdot \left( \frac{\partial^2 P}{\partial x^2} + \frac{\partial^2 P}{\partial y^2} + \frac{\partial^2 P}{\partial z^2} \right)
$$

📓 Notebook-style:
∂P(x, y, z, t)/∂t = D · (∂²P/∂x² + ∂²P/∂y² + ∂²P/∂z²)

---

### Interpretation:

- These are **partial differential equations (PDEs)** modeling how particle density spreads over time
- Used to describe ensemble behavior, not single particles
- In symmetric geometries, the density spreads evenly
- In **asymmetric** ones (like in our experiments), boundary conditions may produce a drift

### Application in NanoFlowModel:

Even though we simulate each particle step-by-step, these equations help us **predict the macroscopic behavior**:

- Whether particle density accumulates in certain zones
- How geometry affects the equilibrium distribution

## 🌐 Continuity Equation – Conservation of Particles in Flow

The continuity equation expresses the **conservation of a quantity** (like mass, particle number, or energy) in a flowing system. It states that what exits a volume must have entered or been generated inside it.

### General vector form:

$$
\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \vec{v}) = 0
$$

📓 Notebook-style:
∂ρ/∂t + ∇·(ρ·v⃗) = 0

Where:

- **ρ** = particle density (number per unit volume)
- **v⃗** = local flow velocity vector
- **∇·(ρ·v⃗)** = divergence (outflow rate per unit volume)

---

### 📏 Expanded forms:

#### 1D:

$$
\frac{\partial \rho(x,t)}{\partial t} + \frac{\partial}{\partial x} \left( \rho(x,t) \cdot v(x,t) \right) = 0
$$

#### 2D:

$$
\frac{\partial \rho}{\partial t} + \frac{\partial}{\partial x}(\rho v_x) + \frac{\partial}{\partial y}(\rho v_y) = 0
$$

#### 3D (used conceptually in our simulations):

$$
\frac{\partial \rho}{\partial t} + \frac{\partial}{\partial x}(\rho v_x) + \frac{\partial}{\partial y}(\rho v_y) + \frac{\partial}{\partial z}(\rho v_z) = 0
$$

---

### Interpretation:

- If **∂ρ/∂t = 0**, the system is in **steady state** (no change in time)
- If **∇·(ρ·v⃗) ≠ 0**, particles are accumulating or escaping somewhere

In **NanoFlowModel**:

- While velocity is random at the individual level, **collective motion (drift)** emerges in asymmetric geometries
- The accumulation of particles near the exit zone (in Test 003/004) implies **local divergence ≠ 0**
- We can infer that the geometry is **biasing flow**, even though no external field is present

---

### Applications:

- Used in fluid dynamics, electromagnetism, thermodynamics
- Foundation for **designing flow channels, cooling paths**, and motion amplifiers

## ⚙️ Coefficient of Restitution – Collision Elasticity

The **coefficient of restitution (e)** quantifies how elastic a collision is between a particle and a surface (like a wall).

### Formula:

$$
e = \frac{v*{\text{after}}}{v*{\text{before}}}
$$

📓 Notebook-style:
e = v_after / v_before

Where:

- **v_before** = velocity just before impact (normal to the surface)
- **v_after** = velocity just after impact (normal component)
- **e** ∈ [0, 1], dimensionless

---

### Types of collisions:

| Type                | Value of e | Description                   |
| ------------------- | ---------- | ----------------------------- |
| Perfectly elastic   | e = 1      | No energy lost; fully bounces |
| Inelastic           | 0 < e < 1  | Partial energy loss; slowed   |
| Perfectly inelastic | e = 0      | No bounce; particle sticks    |

---

### In NanoFlowModel:

- **Reflective walls**: modeled with e ≈ 1
- **Absorbent walls**: modeled with e ≈ 0 or with randomization and speed reduction
- This parameter allows us to simulate **energy retention or dissipation** on collision

---

### Applications:

- Particle physics simulations
- Nano-mechanical surface modeling
- Smart materials with selective energy reflection or absorption

[↑ Back to top](#)  
[← Back to index](../index.md)
