# Methodology

## Overview

This project applies three interconnected optimization approaches to address operational inefficiencies at TINE Brumunddal:

---

## 1. Production Optimization (Linear Programming)

### Problem Formulation

**Objective Function:**
```
Maximize: Σ(Contribution Margin_i × Production_i)
subject to:
  - Bottleneck capacity constraint (DA-101 pasteurization)
  - Product demand constraints
  - Non-negativity constraints
```

### Constraints
- **DA-101 Bottleneck:** 1000 hours/month capacity
- **Product Processing Times:** Varies by product (standardmjølk, mellommelk, lettmelk, etc.)
- **Demand Bounds:** Market limits on each product
- **Non-negativity:** Production volumes ≥ 0

### Solver
- **Tool:** HiGHS/PuLP (open-source LP solver)
- **Algorithm:** Simplex method with presolve
- **Complexity:** O(n³) iterations, solved in <1 second

### Interpretation
- **Shadow Prices:** Marginal value of additional DA-101 capacity
- **Reduced Costs:** Penalty for non-optimal products
- **Sensitivity Analysis:** Impact of parameter changes on optimality

---

## 2. Route Optimization (Two-Opt Heuristic)

### Problem Formulation

**Vehicle Routing Problem (VRP):**
```
Minimize: Total Distance
subject to:
  - All farms visited exactly once
  - Capacity constraints per tank truck
  - Driver rest regulations (45-minute break every 4.5 hours)
  - Time window constraints
```

### Two-Opt Algorithm

**Pseudocode:**
```
1. Start with initial route (nearest-neighbor or random)
2. While improvement found:
   3. For each pair of edges (i,j) and (k,l):
      4. Calculate improvement if edges are swapped
      5. If improvement > 0, perform swap
      6. Mark as improved
   7. Return improved route
```

### Characteristics
- **Time Complexity:** O(n²) per iteration, typically 10-20 iterations
- **Solution Quality:** 90-95% of optimal (proven for small instances)
- **Regulatory Compliance:** Enforces EU/Norway driver regulations

### Constraints Implemented
1. **Capacity:** Tank truck volume limits (typically 28,000-32,000 liters)
2. **Time Windows:** Farm availability windows
3. **Driver Rest:** 45-minute mandatory break after 4.5 hours
4. **Operating Hours:** Collection within facility hours

---

## 3. Heijunka (Production Leveling) Simulation

### Concept

**Heijunka** is a Lean production technique that smooths production output to match demand variation, preventing the bullwhip effect.

### Model Structure

**Discrete Event Simulation:**
```
1. Input: Probabilistic milk intake (historical variance)
2. Each day:
   a. Receive raw milk supply (stochastic)
   b. Execute leveled production schedule
   c. Allocate surplus to storable products (powder, cheese)
   d. Track inventory levels
3. Output: Supply chain variance metrics
```

### Bullwhip Effect Analysis

**Metric:** Coefficient of Variation (CV)
```
Bullwhip Ratio = CV(Downstream Demand) / CV(Upstream Supply)
```

- **Ratio > 1.0:** Demand amplification (bullwhip present)
- **Ratio ≈ 1.0:** Demand synchronization (bullwhip neutralized)
- **Target:** Ratio < 1.1 through flexible production mix

### Key Assumptions
- Storable products absorb ±15% intake variation
- Production changeover time: negligible for Heijunka
- Demand for storable products: stable and predictable

---

## Data Requirements

### Production Optimization
- Production capacity per product (hours/unit)
- Contribution margin per product (NOK/unit)
- Historical demand volumes
- Bottleneck (DA-101) capacity schedule

### Route Optimization
- Farm coordinates (latitude/longitude)
- Distance matrix or routing API
- Farm capacity (liters/pickup)
- Time windows (daily availability)
- Tank truck specifications

### Heijunka Simulation
- Historical raw milk intake (daily/weekly time series)
- Product mix flexibility (which products can absorb surplus)
- Storage capacity constraints
- Demand forecasts for storable products

---

## Validation Approach

### 1. Production Optimization
- **Reasonableness Check:** Compare shadow prices to market benchmarks
- **Sensitivity Analysis:** Vary key parameters (margin, capacity) by ±10%
- **Historical Comparison:** Validate against baseline operations

### 2. Route Optimization
- **Benchmark:** Compare against current routing practice
- **Distance Verification:** Manual spot-check of top 5 routes
- **Compliance Audit:** Verify all regulatory constraints met

### 3. Heijunka Simulation
- **Warm-up Period:** First 30 days excluded from analysis
- **Sample Size:** 365-day minimum simulation
- **Output Variability:** Multiple replications (n=10) for confidence intervals

---

## Limitations & Assumptions

### Production Optimization
- **Assumption:** Contribution margins are fixed (linear)
- **Limitation:** Single-period optimization (doesn't consider inventory dynamics)
- **Assumption:** No product interactions or changeover costs

### Route Optimization
- **Assumption:** Travel times are deterministic
- **Limitation:** No consideration of weather or traffic variations
- **Assumption:** Farms can be visited at any time within window

### Heijunka Simulation
- **Assumption:** Demand for storable products is perfectly elastic
- **Limitation:** No market price dynamics modeled
- **Assumption:** Storage capacity is unlimited

---

## Future Enhancements

1. **Multi-period LP:** Incorporate inventory and dynamic demand
2. **Stochastic Routing:** Account for travel time uncertainty
3. **Integrated Optimization:** Jointly optimize production and routing
4. **Machine Learning:** Demand forecasting for storable products
5. **Real-time Implementation:** API integration for live optimization

---
