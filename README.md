# Supply-Chain-PowerBI

# Power BI Supply Chain Dashboard (SAP MM Simulation)

This Power BI project simulates a simplified **SAP Material Management (MM)** environment to visualize and analyze key supply chain metrics such as inventory status, purchase order fulfillment, and delivery performance.

Built as a demo project to showcase data modeling, ETL concepts, and dashboard design using Power BI — with mock SAP-style data.


---

## 🔧 Data Sources

1. **Material Master**
   - `Material_ID`, `Material_Desc`, `Material_Type`, `Plant`, `Stock_Qty`, `Reorder_Level`

2. **Purchase Orders**
   - `PO_ID`, `Material_ID`, `Qty_Ordered`, `Order_Date`, `Delivery_Date`

3. **Goods Receipt**
   - `Receipt_ID`, `PO_ID`, `Material_ID`, `Qty_Received`, `Receipt_Date`

---

##  Dashboard Features

### Inventory Analysis
- Shows available stock per material and plant
- Highlights materials below reorder levels

###  Purchase Order Fulfillment
- Compares quantity ordered vs. quantity received
- Highlights discrepancies and pending POs

### Delivery Performance
- Calculates and flags late deliveries using DAX
- Displays on-time vs. late delivery count

---

## Key DAX Logic

### Late Delivery Flag:
```DAX
Is_Late = 
VAR DeliveryDate = RELATED(Purchase_Orders[Delivery_Date])
RETURN
    IF(Goods_Receipt[Receipt_Date] > DeliveryDate, 1, 0)

## Fulfillment Rate:
Fulfillment_Rate = 
DIVIDE(SUM(Goods_Receipt[Qty_Received]), SUM(Purchase_Orders[Qty_Ordered]))














