# Model Assumptions & Constraints

## Production Optimization Model

### Assumptions

1. **Linear Cost Structure**
   - Contribution margins are constant per unit
   - No quantity discounts or non-linear pricing
   - Fixed costs excluded from margin calculation

2. **Bottleneck Identification**
   - DA-101 pasteurization line is the binding constraint
   - No other equipment limits production
   - Bottleneck capacity: 1,000 hours/month (fixed)

3. **Product Independence**
   - No product interactions or cannibalization
   - No changeover times or setup costs
   - Processing times are deterministic and proportional to volume

4. **Demand Constraints**
   - Market demand is independent of production decision
   - Demand floors and ceilings are exogenously fixed
   - No price elasticity modeled

5. **Single-Period Optimization**
   - Optimization window: one month
   - No carryover inventory to future periods
   - Historical demand is representative of future demand

### Constraints

| Constraint | Value | Unit |
|-----------|-------|------|
| DA-101 Capacity | 1,000 | hours/month |
| Standardmjølk (3.5% fat) | 800-1,200 | liters/day |
| Mellommelk (1.5% fat) | 400-600 | liters/day |
| Lettmelk (0.5% fat) | 200-400 | liters/day |
| Skjumpe/Other | 100-300 | liters/day |

---

## Route Optimization Model

### Assumptions

1. **Deterministic Travel Times**
   - Travel times are fixed (no traffic/weather variation)
   - Google Routes API distances are accurate
   - No toll roads or alternative routing options

2. **Farm Capacity & Availability**
   - Each farm has a fixed storage capacity (queues impossible)
   - Time windows are inflexible (hard constraints)
   - Farms produce milk continuously within windows

3. **Tank Truck Constraints**
   - Truck capacity: 28,000-32,000 liters (fixed)
   - Loading/unloading time: 15 minutes per farm
   - Single driver per truck (not considering split shifts)

4. **Regulatory Compliance**
   - EU/Norway driver regulations enforced strictly
   - 45-minute mandatory rest after 4.5 hours driving
   - Maximum 10 hours driving per day
   - No night driving (23:00-06:00)

5. **Two-Opt Convergence**
   - Local optima from Two-Opt is acceptable (~90-95% of global optimum)
   - Neighborhood is sufficient to find practical solutions
   - No need for global optimization (e.g., genetic algorithms)

### Constraints

| Constraint | Value |
|-----------|-------|
| Number of farms | 20+ in Innlandet region |
| Geographic radius | ~100 km |
| Tank truck capacity | 28,000-32,000 liters |
| Driver shift duration | 10 hours maximum |
| Mandatory rest | 45 minutes per 4.5 hours |
| Time windows | 06:00-20:00 typical |

---

## Heijunka (Production Leveling) Simulation

### Assumptions

1. **Stochastic Milk Intake**
   - Raw milk supply follows historical distribution
   - Daily intake varies ±15% from mean (95% confidence)
   - Supply variation is independent across days

2. **Flexible Production Mix**
   - Surplus milk can be diverted to storable products:
     - Milk powder (shelf life: 24 months)
     - Cheese (shelf life: 12+ months)
     - Butter/cream (shelf life: 6 months)
   - Production volumes smoothed via inventory buffering

3. **Demand for Storable Products**
   - Stable, predictable demand (low variance)
   - Price elasticity negligible over medium term
   - Inventory absorption rate: ~20% of intake variation

4. **Storage Capacity**
   - Sufficient capacity to absorb ±20% daily swings
   - No storage cost modeled (simplification)
   - Spoilage/waste rate: negligible for refrigerated products

5. **Production Changeover**
   - Negligible changeover time between product lines
   - Equipment flexibility allows rapid product switching
   - No changeover cost incurred

### Simulation Parameters

| Parameter | Value | Unit |
|-----------|-------|------|
| Simulation length | 365 | days |
| Warm-up period | 30 | days |
| Daily intake mean | 50,000 | liters |
| Daily intake std dev | 7,500 | liters |
| CV (intake) | 0.15 | (unitless) |
| Storable product capacity | 10,000 | liters/day |
| Target production ratio | 60% standard / 40% storable | % |

---

## Cross-Model Constraints

### Material Balance
- Total milk input = Standardized products + Storable products + Waste
- Constraint: Waste ≤ 2% of total intake

### Timing
- Production optimization uses target intake levels from Heijunka simulation
- Route optimization must deliver milk to facility by 08:00 for pasteurization
- Collection rounds complete before 18:00 (facility closing)

### Quality & Food Safety
- Raw milk temperature: ≤ 4°C maintained during transport
- Tank truck sterilization: between every 3-4 pickups
- No cross-contamination between farms

---

## Sensitivity Analysis

### Production Optimization

**Key sensitivity factors:**
1. ±10% change in contribution margin → ±~5% optimal value shift
2. ±5% change in DA-101 capacity → ±~8% optimal value shift (shadow price effect)
3. ±20% demand range widening → <2% optimal value change

### Route Optimization

**Key sensitivity factors:**
1. ±5% farm location error → ±2-3% distance increase
2. Time window constraints → +15-20% distance if windows narrow
3. Truck capacity -10% → may require additional truck, +50% cost

### Heijunka Simulation

**Key sensitivity factors:**
1. Intake variability ±30% → Bullwhip ratio 1.05-1.15
2. Storable capacity ±20% → CV reduction 40-60%
3. Demand volatility → Critical for buffer sizing

---

## Validation Checkpoints

✓ All hard constraints (capacity, time windows, regulatory) verified  
✓ Soft constraints (preferred solutions) documented and weighted  
✓ Sensitivity analysis ranges documented  
✓ Historical baseline comparison completed  
✓ Team consensus on assumptions obtained  

---
