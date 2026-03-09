# Customer-and-revenue-cohorts
Analyse customer cohort together with revenue cohort to analyse customer retention

# Customer & Revenue Cohort Analysis (SQL + Tableau)

## Business question:
**Do customers come back after their first purchase — and if they do, do they also keep spending money?**  
To answer it, I built **customer retention cohorts** and **revenue cohorts** from raw transactional data and visualized the results in Tableau heatmaps.

## What I built
### 1) Customer retention cohorts
For each cohort month + month number, I calculated:
- **Active Customers** = unique customers who placed at least one order in that month
- **Cohort Size** = customers active in month 0 (their first month)
- **Retention %** = active_customers / cohort_size

### 2) Revenue cohorts
For each cohort month + month number, I calculated:
- **Total Revenue** = sum of revenue from order items
- **Revenue Retention %** = revenue in month N compared to revenue in month 0 (cohort baseline)

## Visual outputs (Tableau heatmaps)
I created 4 heatmaps:
1. **Customer cohort %** (retention rate)
2. **Cohort customers** (active customers count)
3. **Cohort revenue** (absolute revenue)
4. **Cohort revenue %** (revenue retention)

## Key insights

- Most customers do not return after the first purchase. Retention drops sharply after month 1.
- Some customers return later. In several cohorts retention increases again in later months, which may indicate seasonal purchases or a longer buying cycle. Customer acquisition and revenue peaks in October–December, supporting a seasonal shopping pattern.
- Returning customers generate a significant revenue share. Even though the number of returning users is small, their spending is relatively high.
- The business relies heavily on new customers. Most revenue is generated during the first purchase.

## Business recommendations

- Getting customers to come back for a second purchase, especially in the first month after they buy. This can be done by improving post-purchase engagement (email, loyalty, reminders) or creating repeat purchase incentives after first order.
- Identifying the charateristics of returning customers and target similar audiences.
- Marketing campaigns should begin before the peak season so the company can capture customer interest early and maximize sales during the holiday period.

### Tools useed
- **PostgreSQL / Supabase**: data modeling + cohort calculations
- **Tableau Public**: cohort heatmaps and story view

### Data model (tables used)
- `customers` (customer_id, location fields)
- `orders` (order_id, order_date, customer_id, geo fields)
- `order_items` (order_id, product_id, quantity, revenue, profit)
- `products` (product attributes and unit price)
- 
## Link to the online dashboard 
https://public.tableau.com/app/profile/alina.lihostaieva/viz/Customercohortprojecttableaunew/Story1?publish=yes 

<img width="946" height="759" alt="Screenshot 2026-03-07 at 09 46 09" src="https://github.com/user-attachments/assets/d8fe8509-fc48-47b9-ad01-50440775a9a2" />

<img width="951" height="734" alt="Screenshot 2026-03-07 at 09 46 54" src="https://github.com/user-attachments/assets/2b6ad273-4b8b-4c01-b526-0936f5faa4d3" />
<img width="949" height="762" alt="Screenshot 2026-03-07 at 09 47 12" src="https://github.com/user-attachments/assets/45f8facf-81cf-4474-8b3a-7be96abec4ff" />

<img width="973" height="730" alt="Screenshot 2026-03-07 at 09 50 49" src="https://github.com/user-attachments/assets/862cb2a3-9cab-43c2-aad6-a967a524c673" />

<img width="1129" height="253" alt="Sample dataset" src="https://github.com/user-attachments/assets/df5f4787-4203-4d96-b397-78450a22b7ba" />

<img width="773" height="554" alt="Data model" src="https://github.com/user-attachments/assets/7ee33bd4-c008-42b3-becf-22f8d6319a4b" />

## What is a cohort here?
A **cohort** = a group of customers who made their **first purchase in the same month**.  
Example: everyone whose first order was in **Jan 2023** belongs to the **Jan 2023 cohort**.
