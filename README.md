# Business Problem

Given three price/demand estimates on the demand curve, how do we determine a profit-maximizing price?

# Model Features

* Input: Sales team provides 3 estimates (low price, med price, high price)

* Demand-curve fitting: numpy.polyfit

* Optimization: SciPy minimize_scalar

* Output: Directly useful, process reusable

<img width="274" height="146" alt="image" src="https://github.com/user-attachments/assets/b1f22c0e-4be8-4fb0-8252-76eb24713a16" />


# Solution

Traditionally this type of problem is done in Excel using SolverTable add-in. It's what I was taught in business school. But Excel isn't built for automation, Python is. We go from input:

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

For this model to be useful, the minimum and maximum prices need to be consistent with consumer preferences. So we need a knowledgeable sales force to come up with realistic minimum and maximum prices/demands.
```
Demand = a (price)^2 + b (price) + c
```

While this demand model only considers one predictor (i.e. price), it provides a good estimate to the true demand curve when we don't know the price elasticity, or if linear/power demand curve aren't suitable. The simplicity of this model can be its strength, because we can easily buttress the model by adding more price/demand estimates to get a better fit.

Using this automated model, it is easy to price hundreds of thousands of products without ever having to manually copy/pasting values across worksheets.


based on Winston book
