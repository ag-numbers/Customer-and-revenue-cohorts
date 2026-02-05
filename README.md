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

- Strong drop after month 1: Most customers make only one purchase
- Stable long-term retention: After month 3–4, retention stabilizes at ~2–4%
- Revenue retention > customer retention: Fewer returning customers, but higher spend per returning user
- High dependency on new customers: Month 0 generates the majority of revenue across all cohorts
- No clear improvement in newer cohorts: Retention patterns remain consistent over time

## Business recommendations

- Getting customers to come back for a second purchase, especially in the first month after they buy. This can be done by improving post-purchase engagement (email, loyalty, reminders)
or creating repeat purchase incentives after first order.
- Identifying and targeting high-value repeat customers, since they generate a high share of revenue
- Relying mostly on new customer acquisition is risky, so improving retention could make growth more sustainable
- Running experiments to improve month 1 retention, which has the biggest drop

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
https://public.tableau.com/shared/TFS8YPDP4?:display_count=n&:origin=viz_share_link 

<img width="1126" height="589" alt="Customer cohort" src="https://github.com/user-attachments/assets/7e79fdcd-2557-41fb-8044-f05d373e9972" />

<img width="1079" height="593" alt="Customer cohort %" src="https://github.com/user-attachments/assets/6b40bb81-1e7e-4827-89f3-3725e38b32e3" />

<img width="1124" height="602" alt="Revenue cohort %" src="https://github.com/user-attachments/assets/94b8b840-fab3-47c5-a302-c69f5bf0c577" />

<img width="1121" height="593" alt="Cohort revenue" src="https://github.com/user-attachments/assets/97103514-041c-4e0c-86c4-d58a9e7a3799" />

<img width="1129" height="253" alt="Sample dataset" src="https://github.com/user-attachments/assets/df5f4787-4203-4d96-b397-78450a22b7ba" />

<img width="773" height="554" alt="Data model" src="https://github.com/user-attachments/assets/7ee33bd4-c008-42b3-becf-22f8d6319a4b" />

## What is a cohort here?
A **cohort** = a group of customers who made their **first purchase in the same month**.  
Example: everyone whose first order was in **Jan 2023** belongs to the **Jan 2023 cohort**.
