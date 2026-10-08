<img width="794" height="106" alt="image" src="https://github.com/user-attachments/assets/f8d61858-f6e2-4afd-8ef2-3d6c4da45240" />

# Business Problem

Given three price/demand estimates on the demand curve, how do we determine a profit-maximizing price?

# Model Features

* Input: Sales team provides 3 estimates (low price, med price, high price)

* Demand-curve fitting: numpy.polyfit

* Optimization: SciPy minimize_scalar

* Output: Directly useful, process reusable

<img width="274" height="146" alt="image" src="https://github.com/user-attachments/assets/b1f22c0e-4be8-4fb0-8252-76eb24713a16" />

<br>
<br>

* Methodology: Adapted from Chapter 86 of Wayne L. Winston's _Microsoft Excel 2016 Data Analysis and Business Modeling_, which demonstrates pricing a product using subjectively determined demand estimates. I translated the Excel approach into Python and extended it to optimize multiple SKUs automatically.

# Solution

Traditionally, this type of problem is done in Excel using SolverTable add-in. It's what I was taught in business school. But Excel isn't built for automation, Python is. We go from input:

<img width="798" height="183" alt="image" src="https://github.com/user-attachments/assets/be62ef43-58d7-4f63-b890-a0a28d3df284" />

<p>

To fitting the demand curve:

```python
a, b, c = np.polyfit(prices, demands, 2)
```

To optimization in a highly streamlined fashion:
```python
result = minimize_scalar(
        lambda price:-profit(price),
        bounds=(product['Low_Price'], product['High_Price']),
        method='bounded'
    )
```

**About the Quadratic Demand Model**

For this model to be useful, the minimum and maximum prices need to be consistent with consumer preferences. So we need a knowledgeable sales force to come up with realistic low and high price/demand cutoffs.
```
Demand = a (price)^2 + b (price) + c
```

While this demand model only considers one predictor (i.e. price), its simplicity can be an advantage when a quick, transparent pricing estimate is more useful than a complex model. The quadratic form can capture curvature that a linear model cannot, and we can easily input more price/demand estimates to produce a more robust fit (3 is just the minimum needed!).

More sophisticated demand models could incorporate factors such as competitor pricing, promotions, or seasonality, but this approach provides a lightweight starting point and a good estimate to the ground truth.

Using this automated model, it is easy to price hundreds of thousands of products without ever having to manually copy-paste values across worksheets.

<br>

📗 Based on _Microsoft Excel 2016 Data Analysis and Business Modeling_ by Wayne L. Winston, Chapter 86, "Pricing products by using subjectively determined demand"
