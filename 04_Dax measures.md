# DAX Measures

The following DAX measures were created to support dashboard analysis.

---

## Total Revenue

```DAX
Total Revenue =
SUMX(
    'Coffee Shop Sales',
    'Coffee Shop Sales'[transaction_qty] *
    'Coffee Shop Sales'[unit_price]
)
```

---

## Total Transactions

```DAX
Total Transactions =
DISTINCTCOUNT('Coffee Shop Sales'[transaction_id])
```

---

## Total Quantity Sold

```DAX
Total Quantity Sold =
SUM('Coffee Shop Sales'[transaction_qty])
```

---

## Average Order Value

```DAX
Average Order Value =
DIVIDE(
    [Total Revenue],
    [Total Transactions]
)
```

---

## Average Quantity per Transaction

```DAX
Average Quantity per Transaction =
DIVIDE(
    [Total Quantity Sold],
    [Total Transactions]
)
```

---

## Revenue MoM %

```DAX
Revenue MoM % =
VAR CurrentMonth =
    [Total Revenue]

VAR PreviousMonth =
    CALCULATE(
        [Total Revenue],
        DATEADD(
            'Dim_Date'[Date],
            -1,
            MONTH
        )
    )

RETURN
DIVIDE(
    CurrentMonth - PreviousMonth,
    PreviousMonth
)
```

---

## Revenue Rank by Store

```DAX
Store Rank = 
RANKX(
    ALL(Dim_store[store_location]),
    [Total Revenue]
)
```

---

## Top Product Rank

```DAX
Product Rank = 
RANKX(
    ALL(Dim_Products[product_category]),
    [Total Revenue]
)
```

---

## Estimated Profit

Assuming a production cost of 60% of revenue.

```DAX
Estimated Profit =
[Total Revenue] * 0.40
```

---

## Profit Margin

```DAX
Profit Margin =
DIVIDE(
    [Estimated Profit],
    [Total Revenue]
)
```

---

## Dashboard KPIs

The dashboard uses the following key measures:

- Total Revenue
- Total Transactions
- Total Quantity Sold
- Average Order Value
- Revenue Growth
- Estimated Profit
- Profit Margin