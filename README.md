# Business Problem

Given three specified points on the demand curve (SKU-level price/demand estimates provided by sales team), how do we determine a profit-maximizing price?

# Solution

profit=demand*(price-unit_cost)

Fitting:np.polyfit
Optimization:minimize_scalar

"For the quadratic demand model to be useful, the minimum and maximum prices must be consistent with consumer preferences. A knowledgeable sales force should be able to come up with realistic minimum and maximum prices."

easily price hundreds or thousands of products
SolverTable add-in
Python starts massively outperforming a manually configured spreadsheet.
one recipe → every SKU
np.polyfit() handles the demand-curve fitting.
minimize_scalar() handles the actual optimization.
directly useful output
