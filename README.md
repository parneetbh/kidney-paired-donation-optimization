# 🔬 Kidney Exchange Optimization

## 📌 Overview
This project models and solves a **Kidney Paired Donation (KPD)** optimization problem using **integer programming**. The goal is to **maximize the total number of transplants** under a structured set of compatibility and participation constraints.

The project is framed as an **academic optimization exercise** designed to demonstrate modeling, solver usage, and analytical reasoning. The data and assumptions are illustrative and not intended to represent real world transplant decisions.

## 🧠 Problem Context
Kidney paired donation programs involve matching donor recipient pairs who are incompatible with each other but may be compatible with others in the pool.

As the pool size grows, the number of feasible match combinations increases rapidly 📈. This makes manual matching impractical and motivates the use of **optimization solvers** to efficiently explore the solution space.

This project demonstrates how **integer programming** can be applied to a complex matching problem with multiple constraints.

## 🎯 Objectives
- ✅ Maximize the total number of transplants
- 🩸 Enforce blood type compatibility
- 🧬 Enforce tissue type compatibility
- 👤 Ensure each donor donates at most one kidney
- 🧑‍⚕️ Ensure each patient receives at most one kidney
- 🔗 Enforce non altruistic donor behavior, where a donor only participates if their paired patient also receives a kidney

## 📊 Data and Inputs
- 25 donor recipient pairs
- Blood type compatibility matrix
- Tissue type compatibility matrix
- Pair linkage between each donor and their associated patient

Compatibility matrices are constructed to indicate whether a donor can donate to a specific patient based on predefined medical rules.

## 📐 Model Formulation
The baseline model is an **integer programming formulation** with binary decision variables indicating whether donor *i* donates to patient *j*.

### 🔢 Decision Variable
- `x_ij = 1` if donor *i* donates to patient *j*, `0` otherwise

### 🏁 Objective Function
Maximize the total number of transplants across all donor patient matches.

### ⛓️ Constraints
- **Donor capacity**: each donor can donate to at most one patient
- **Patient assignment**: each patient can receive at most one kidney
- **Compatibility**: donation allowed only if blood type and tissue type are compatible
- **Paired donation**: a donor only donates if their paired patient also receives a kidney

## 📈 Baseline Results
- 🏆 Maximum of **12 transplants** achieved
- 👥 24 individuals participate out of the original pool of 50
- 📊 Approximately **50 percent conversion rate**

The optimal solution satisfies all imposed constraints and illustrates how tradeoffs emerge in constrained matching problems.

## 🔄 Model Variations
To explore how assumptions impact optimal outcomes, additional model variants were tested.

### 🤝 Prioritizing Internal Pair Compatibility
When donor recipient pairs are assumed to prioritize donating within their own pair if compatible:
- 🔍 One pair exits the exchange pool
- 📉 Optimal transplants drop from **12 to 9**

This highlights how behavioral assumptions can materially affect system level outcomes.

### 🧪 Blood Type Conversion Extension
A hypothetical extension explores the impact of converting donor blood types to **type O**.

#### 🔧 Key Changes
- Blood type compatibility constraint removed
- Matching depends only on tissue type compatibility

#### 🚀 Results
- Total transplants increase from **12 to 20**
- More original donor recipient pairs are able to match directly
- Demonstrates sensitivity of outcomes to constraint relaxation

## 💡 Key Takeaways
- 📐 Integer programming is well suited for complex matching problems
- 🔍 Small modeling assumptions can significantly change optimal solutions
- ⚙️ Optimization solvers like **Gurobi** can efficiently handle large combinatorial search spaces
- 🧠 The project demonstrates strong formulation, constraint design, and result interpretation skills

## 🛠️ Technologies Used
- 🐍 Python
- 📐 Integer Programming
- ⚙️ Gurobi Optimizer
- 📓 Jupyter Notebook
- 📄 CSV based compatibility matrices
