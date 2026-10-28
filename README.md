# TINE Brumunddal: Supply Chain & Operations Optimization

[![Course](https://img.shields.io/badge/Course-IND210%20Driftsledelse-blue)](https://www.nmbu.no/)
[![Institution](https://img.shields.io/badge/Institution-NMBU-green)](https://www.nmbu.no/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)](#)

> A portfolio-ready operations optimization project for TINE Brumunddal, applying Lean Production, Theory of Constraints, linear programming, heuristic routing, and production leveling to improve dairy supply chain performance.

---

## Project Overview

This project was completed as part of the course IND210 - Driftsledelse (Operations Management) at the Norwegian University of Life Sciences (NMBU). The objective was to analyze and improve a dairy supply chain operating under variability, capacity constraints, and logistical complexity.

The system was modeled as a real-world industrial operations problem where raw milk collection, production scheduling, transportation, and bottleneck management all interact. The project focused on identifying where value was being lost and applying optimization methods to improve profitability, flow, and resilience.

The core question was simple but important:

How can TINE Brumunddal improve efficiency and profitability without sacrificing operational stability or regulatory compliance?

---

## The Problem

TINE Brumunddal faces a common but difficult challenge in dairy operations: a supply chain with fluctuating raw milk intake, constrained production capacity, and complex transportation requirements.

### Main operational issues
- Raw milk supply varies significantly across time and geography
- Production capacity is limited by specific bottleneck processes
- Some product types consume scarce bottleneck time without generating sufficient margin
- Route planning across farms is inefficient if not optimized
- High variability creates bullwhip effects and unstable planning

### Why this matters
In a dairy supply chain, small inefficiencies compound quickly. If the wrong products are produced, if routes are poorly organized, or if production is not leveled, costs increase, throughput falls, and profitability suffers.

The project addresses these problems by treating the business as a system of constraints, flows, and decisions rather than isolated departments.

---

## What We Solved

This project tackled the problem from three complementary angles:

### 1) Production Optimization with Linear Programming

The first challenge was identifying the real bottleneck in production and deciding which products should be prioritized.

We used a linear programming model to optimize the product mix around the critical bottleneck, DA-101 pasteurization line.

#### Objective
Maximize contribution margin while respecting process and capacity constraints.

#### Approach
- Modeled production as a constrained optimization problem
- Identified low-margin products consuming bottleneck capacity
- Evaluated contribution margin per production hour
- Reallocated limited bottleneck time to more valuable products

#### Result
- Recommendation to phase out or reduce low-margin products such as mellommelk
- Increased daily contribution margin by approximately 9.7%
- Estimated benefit of around 29,625 NOK per day
- Demonstrated substantial annual profit potential

This is a classic Theory of Constraints application: improve the system by optimizing the constraint, not by trying to increase every process equally.

---

### 2) Route Optimization with Heuristics

The second challenge was logistics. Milk must be collected from multiple farms across a fragmented supplier network, and transportation costs can rise quickly without effective planning.

We implemented a vehicle routing heuristic based on the Two-Opt algorithm to reduce travel distance and improve truck utilization.

#### Objective
Minimize transportation distance and cost while maintaining route feasibility and compliance.

#### Approach
- Optimized collection routes from farms to production or collection points
- Included regulatory constraints such as mandatory rest periods
- Reduced unnecessary detours and inefficient sequencing

#### Result
- Lower total route length compared to baseline routing
- Improved logistics efficiency
- Better utilization of truck capacity
- Maintained compliance with driver regulations and operational constraints

This part of the project shows how operational optimization can reduce cost in indirect but impactful ways.

---

### 3) Production Leveling (Heijunka)

The third challenge was variability. Raw milk intake fluctuates, creating instability across production and inventory planning.

To reduce this instability, we implemented a Heijunka-style production leveling strategy.

#### Objective
Stabilize production and reduce the bullwhip effect caused by unpredictable supply volume.

#### Approach
- Smoothed production schedules
- Diverted excess supply into storable products where appropriate
- Reduced operational disruption caused by fluctuating inflow
- Balanced the system more effectively over time

#### Result
- Reduced volatility across the chain
- Improved production stability
- Better inventory management
- Enhanced resilience against demand and supply variation

This is where Lean thinking becomes especially valuable: smooth flow reduces waste, improves predictability, and lowers operational stress.

---

## How It Was Solved

The project combined quantitative methods with practical operations knowledge.

### Core methodology
- Linear programming for product mix optimization
- Heuristic optimization for routing problems
- Simulation-based analysis for production leveling
- Lean principles and Theory of Constraints for operational reasoning

### Decision logic
Instead of asking, "How can we produce more?", we asked,

- What is the real constraint?
- Where does value creation stop being efficient?
- Which products maximize throughput at the bottleneck?
- How can routes and schedules be smoothed for better flow?

This reframing is a major lesson in industrial systems optimization: the goal is not simply maximum output, but maximum value creation under constraints.

---

## What We Learned

This project provided several important lessons in industrial and supply chain management:

### 1. Bottlenecks determine performance
A system can only produce as much as its constraint allows. Improving non-bottleneck processes alone does not create proportional gains.

### 2. Product mix matters more than total volume
Producing more of the wrong product can reduce profitability. The right mix creates much more value than simply increasing output.

### 3. Logistics is a strategic lever
Transportation is not just a cost center; it affects service, time, product quality, and operational efficiency.

### 4. Variability is expensive
Unstable supply and demand create ripple effects across the system. Smoothing and buffering strategies reduce operational pain.

### 5. Data and optimization are decision tools, not just technical exercises
The value of the project came from connecting mathematical models to real business decisions.

---

## Technologies Used

| Component | Technology |
|-----------|------------|
| Language | Python |
| Data Processing | Pandas, NumPy |
| Optimization | SciPy, HiGHS |
| Routing & Distance Modeling | Google Routes API |
| Visualization | GeoJSON, charts, plots |
| Domain Focus | Agro-industrial supply chain, route planning, production leveling |

### Why these technologies?
- Python enabled rapid modeling and analysis
- Pandas and NumPy handled structured industrial data efficiently
- SciPy and HiGHS solved optimization problems reliably
- Google Routes API supported realistic route design
- Visualization tools made operations insights easier to interpret and present

---

## Project Structure

```text
Industrial-management-IND210/
├── README.md                          # Project documentation
├── Report.pdf                         # Final comprehensive report
├── Report.docx                        # Source report document
├── .gitignore                         # Git configuration
├── requirements.txt                   # Python dependencies
├── LICENSE                            # Project license
│
├── models/                            # Optimization and simulation models
│   ├── production_optimization.py     # Linear programming model
│   ├── route_optimization.py          # Routing heuristic implementation
│   └── heijunka_simulation.py         # Production leveling model
│
├── data/                              # Input datasets
│   ├── production_capacity.csv        # Equipment and bottleneck data
│   ├── farm_locations.csv             # Farm geographic data
│   ├── milk_intake_variance.csv       # Supply variability patterns
│   └── product_margins.csv           # Contribution margin data
│
├── results/                           # Output files
│   ├── production_analysis.csv        # Optimization results
│   ├── optimal_routes.geojson         # Route visualization
│   ├── bullwhip_analysis.png          # Production smoothing plot
│   └── summary_report.txt            # Executive summary
│
└── docs/                              # Documentation
    ├── methodology.md                 # Detailed methodology
    ├── assumptions.md                # Model assumptions
    └── references.md                 # Academic and industrial references
```

---

## Key Metrics and Business Impact

| Metric | Value | Unit |
|--------|-------|------|
| Contribution Margin Increase | 9.7% | % daily |
| Margin Impact | ~29,625 | NOK/day |
| Annual Potential | €10.8M+ | Revenue potential |
| Route Efficiency | Improved | vs. baseline |
| Bullwhip Effect | Reduced | Operational stability |
| Regulatory Compliance | 100% | Driver and route adherence |

### Business value delivered
- Increased profitability through bottleneck-focused optimization
- Reduced logistics cost and travel waste
- More stable operations under raw material variability
- Stronger planning and reduced operational risk
- Scalable framework applicable to similar industrial dairy or food supply chains

---

## Project Team

| Member | Role |
|--------|------|
| Mehdi Jamali | Lead analyst, linear programming |
| Daniel Yang Tsan | Route optimization specialist |
| Oliver Tschudi Madsen | Production simulation expert |
| Helena Liepina Vollestad | Supply chain researcher |
| Victoria Wallin | Data analyst and visualization |

---

## Documentation

- [Full Report](./Report.pdf) — Comprehensive technical report
- [Methodology](./docs/methodology.md) — Detailed model descriptions
- [Assumptions](./docs/assumptions.md) — Explicit assumptions and constraints
- [References](./docs/references.md) — Academic and industry sources

---

## Portfolio Summary

This project demonstrates the ability to combine operations research, data analysis, and business-oriented decision making in a realistic industrial context. It is a strong example of applying analytical modeling to solve meaningful problems in production, logistics, and supply chain management.

It reflects a practical skill set relevant to:
- Supply chain engineering
- Operations analytics
- Industrial optimization
- Process improvement
- Decision support and strategic planning

---

## License

This project is licensed under the MIT License. See [LICENSE](./LICENSE) for details.

---

## Contributing

Contributions are welcome. To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---

## Contact

**Project Lead:** Mehdi Jamali  
**Repository:** [Mehdij1511/Industrial-management-IND210](https://github.com/Mehdij1511/Industrial-management-IND210)  
**Course:** IND210 - Operations Management (NMBU)

---

## Acknowledgments

- TINE Brumunddal — for providing operational context and data
- NMBU Faculty — for academic guidance and support
- Course instructors — for mentoring quantitative optimization approaches

---

**Last Updated:** May 2026  
**Status:** Project Complete ✓
