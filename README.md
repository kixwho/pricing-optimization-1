# Business Problem

Given three price/demand estimates on the demand curve, how do we determine a profit-maximizing price?

# Model Features

* Input: Sales team provides estimates

* Demand-curve fitting: numpy.polyfit

* Optimization: SciPy minimize_scalar

* Output: Directly useful, process reusable

# Step-by-Step Solution

SKU-level price/demand estimates provided by sales team

profit=demand*(price-unit_cost)

"For the quadratic demand model to be useful, the minimum and maximum prices must be consistent with consumer preferences. A knowledgeable sales force should be able to come up with realistic minimum and maximum prices."

easily price hundreds or thousands of products
SolverTable add-in
Python starts massively outperforming a manually configured spreadsheet.

one recipe → every SKU

based on Winston book
