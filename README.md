# TINE Brumunddal: Supply Chain & Operations Optimization

[![Course](https://img.shields.io/badge/Course-IND210%20Driftsledelse-blue)](https://www.nmbu.no/)
[![Institution](https://img.shields.io/badge/Institution-NMBU-green)](https://www.nmbu.no/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)](#)

> A comprehensive operational optimization project for TINE Brumunddal, applying Lean Production, Theory of Constraints, and Linear Programming to optimize a dairy supply chain.

---

## 📌 Project Overview

This project was conducted for the course **IND210 - Driftsledelse** (Operations Management) at the **Norwegian University of Life Sciences (NMBU)**. It explores the operational challenges of balancing a "push"-based raw milk supply with demand-driven production, implementing quantitative methods to optimize production management and logistics.

### Objectives
- Apply quantitative methods to optimize production and logistics
- Integrate Lean Production principles with the Theory of Constraints
- Maximize profitability at bottleneck constraints
- Optimize transportation routes while maintaining regulatory compliance
- Implement production leveling to counteract bullwhip effects

---

## 🛠️ Technical Stack

| Component | Technology |
|-----------|------------|
| **Language** | Python |
| **Data Processing** | Pandas, NumPy |
| **Optimization** | SciPy, HiGHS |
| **Routing** | Google Routes API |
| **Domain** | Agro-industrial supply chain, route planning, production leveling |

---

## 🚀 Key Components & Results

### 1. Production Optimization (Linear Programming)

**Objective:** Maximize contribution margin at the critical bottleneck (DA-101 pasteurization line).

**Approach:**
- Built a linear programming model optimizing product mix given capacity constraints
- Identified low-margin products limiting bottleneck throughput
- Analyzed contribution margin per production hour for each product

**Results:**
- **Recommendation:** Phase out low-margin *mellommelk* (semi-skimmed milk) for higher-value products
- **Impact:** Increased daily contribution margin by **9.7% (~29,625 NOK/day)**
- **Scalability:** Demonstrates significant annual profit potential (€10.8M+)

**Files:**
- `models/production_optimization.py` — Linear programming model
- `data/` — Production capacity and margin data
- `results/production_analysis.csv` — Optimization outputs

---

### 2. Route Optimization (Heuristics)

**Objective:** Minimize transportation costs for milk collection from 20+ farms in Innlandet region.

**Approach:**
- Implemented the **Two-opt algorithm** for vehicle routing
- Incorporated driver rest regulations (EU/Norway compliance)
- Balanced route distance with operational constraints

**Results:**
- **Achievement:** Drastically reduced transit distances vs. baseline routing
- **Compliance:** Maintained strict adherence to 45-minute mandatory rest periods
- **Efficiency:** Optimized tank truck utilization across fragmented farm network

**Files:**
- `models/route_optimization.py` — Two-opt implementation
- `data/farm_locations.csv` — Geographic and capacity data
- `results/optimal_routes.geojson` — Optimized route visualization

---

### 3. Heijunka (Production Leveling)

**Objective:** Neutralize bullwhip effects by balancing unpredictable raw milk intake.

**Approach:**
- Simulated production leveling strategy
- Diverted surplus milk into storable products (milk powder, cheese)
- Modeled inventory dynamics across supply chain tiers

**Results:**
- **Success:** Successfully neutralized bullwhip effect across supply chain
- **Strategy:** Flexible production mix absorbs raw material variability
- **Sustainability:** Reduces waste and maximizes resource utilization

**Files:**
- `models/heijunka_simulation.py` — Production leveling model
- `data/milk_intake_variance.csv` — Historical intake patterns
- `results/bullwhip_analysis.png` — Effect visualization

---

## 📂 Project Structure

```
Industrial-management-IND210/
├── README.md                          # Project documentation
├── Report.pdf                         # Final comprehensive report
├── Report.docx                        # Source report document
├── .gitignore                         # Git configuration
├── requirements.txt                   # Python dependencies
├── LICENSE                            # Project license
│
├── models/                            # Optimization & simulation models
│   ├── production_optimization.py     # LP model for product mix
│   ├── route_optimization.py          # Two-opt routing algorithm
│   └── heijunka_simulation.py         # Production leveling model
│
├── data/                              # Input datasets
│   ├── production_capacity.csv        # Equipment & bottleneck data
│   ├── farm_locations.csv             # Supplier geographic data
│   ├── milk_intake_variance.csv       # Supply variability patterns
│   └── product_margins.csv            # Contribution margin data
│
├── results/                           # Analysis outputs
│   ├── production_analysis.csv        # Optimization results
│   ├── optimal_routes.geojson         # Route visualization
│   ├── bullwhip_analysis.png          # Effect charts
│   └── summary_report.txt             # Executive summary
│
└── docs/                              # Additional documentation
    ├── methodology.md                 # Detailed methods
    ├── assumptions.md                 # Model assumptions
    └── references.md                  # Academic citations
```

---

## 👥 Project Team

| Member | Role |
|--------|------|
| **Mehdi Jamali** | Lead analyst, Linear programming |
| **Daniel Yang Tsan** | Route optimization specialist |
| **Oliver Tschudi Madsen** | Production simulation expert |
| **Helena Liepina Vollestad** | Supply chain researcher |
| **Victoria Wallin** | Data analyst & visualization |

---

## 📊 Key Metrics & KPIs

| Metric | Value | Unit |
|--------|-------|------|
| Contribution Margin Increase | 9.7% | % daily |
| Margin Impact | ~29,625 | NOK/day |
| Annual Potential | €10.8M | Revenue |
| Route Distance Reduction | Significant | vs. baseline |
| Bullwhip Effect | Neutralized | Status |
| Driver Compliance | 100% | Regulatory |

---

## 📚 Methodologies Applied

### 1. Linear Programming
- **Framework:** Maximizing objective functions subject to linear constraints
- **Application:** Product mix optimization at bottleneck capacity
- **Solver:** SciPy/HiGHS

### 2. Heuristic Algorithms
- **Framework:** Two-opt local search optimization
- **Application:** Vehicle routing problem with constraints
- **Benefit:** Near-optimal solutions with polynomial time complexity

### 3. Discrete Event Simulation
- **Framework:** Monte Carlo simulation of supply chain dynamics
- **Application:** Heijunka production leveling assessment
- **Tool:** Custom Python simulation engine

### 4. Lean Production Principles
- **Application:** Waste elimination, bottleneck identification, flow optimization

### 5. Theory of Constraints (TOC)
- **Framework:** Identify and optimize the system bottleneck (DA-101)
- **Impact:** Focused improvement on the constraint that limits throughput

---

## 💼 Business Impact

✅ **Profitability:** 9.7% daily margin improvement translates to significant annual revenue uplift  
✅ **Efficiency:** Optimized routing reduces fuel costs and driver hours  
✅ **Resilience:** Production leveling mitigates supply chain volatility  
✅ **Compliance:** Maintains 100% regulatory adherence across operations  
✅ **Scalability:** Framework applicable to similar dairy/agro operations  

---

## 📖 Documentation

- **[Full Report](./Report.pdf)** — Comprehensive 44-page technical analysis
- **[Methodology](./docs/methodology.md)** — Detailed model specifications
- **[Assumptions](./docs/assumptions.md)** — Model assumptions and constraints
- **[References](./docs/references.md)** — Academic and industry citations

---

## 📝 License

This project is licensed under the **MIT License** — see [LICENSE](./LICENSE) for details.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit changes (`git commit -m 'Add feature'`)
4. Push to branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---

## 📧 Contact

**Project Lead:** Mehdi Jamali  
**Repository:** [Mehdij1511/Industrial-management-IND210](https://github.com/Mehdij1511/Industrial-management-IND210)  
**Course:** IND210 - Operations Management (NMBU)

---

## 🙏 Acknowledgments

- **TINE Brumunddal** — For providing operational data and context
- **NMBU Faculty** — For guidance and academic support
- **Course Instructors** — For mentoring quantitative optimization approaches

---

**Last Updated:** May 2026  
**Status:** Project Complete ✓
