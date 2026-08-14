# TINE Brumunddal: Supply Chain & Operations Optimization

This project was conducted for the course **IND210 - Driftsledelse** at the **Norwegian University of Life Sciences (NMBU)**. It explores the operational challenges of balancing a "push"-based raw milk supply (*mottakerplikt*) against a "pull"-based market demand at the TINE dairy facility in Brumunddal.

## 📌 Project Overview
The primary objective was to apply quantitative methods to optimize production management and logistics. By integrating **Lean Production**, the **Theory of Constraints (TOC)**, and **Linear Programming**, we developed decision-support tools to identify bottlenecks and reduce supply chain variability.

## 🛠️ Technical Stack
* **Language:** Python
* **Data Handling:** Pandas
* **Mathematical Solvers:** SciPy, HiGHS
* **Logistics API:** Google Routes API
* **Domains:** Agro-industrial supply chain, route planning, production leveling (Heijunka)

## 🚀 Key Components & Results

### 1. Production Optimization (Linear Programming)
* **Action:** Built an LP model to maximize contribution margin at the critical bottleneck (**DA-101**).
* **Result:** Recommended phasing out low-margin *mellommelk* (semi-skimmed milk) for higher-value products.
* **Impact:** Increased daily contribution margin by **9.7% (~29,625 NOK/day)**.

### 2. Route Optimization (Heuristics)
* **Action:** Implemented the **Two-opt algorithm** for tank trucks collecting organic milk from 20+ farms in Innlandet.
* **Result:** Drastically reduced transit distances compared to baseline routing.
* **Compliance:** Maintained strict adherence to driver rest regulations.

### 3. Heijunka (Production Leveling)
* **Action:** Simulated a production leveling strategy to balance unpredictable raw milk intake.
* **Strategy:** Diverted surplus milk into storable products like milk powder and cheese.
* **Result:** Successfully neutralized the **Bullwhip effect** across the supply chain.

## 👥 Project Team
* **Mehdi Jamali**
* **Daniel Yang Tsan**
* **Oliver Tschudi Madsen**
* **Helena Liepina Vollestad**
* **Victoria Wallin**
