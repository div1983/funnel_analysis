# E-commerce Funnel Analysis — 12-Week Sample Dataset

## Project Overview

I built this project to understand where users are being lost between the first visit and the final purchase on an e-commerce website.

Instead of looking only at the final conversion rate, I broke the customer journey into individual stages and then compared performance across **marketing channels** and **devices**. The idea was to answer a practical business question:

> **Where is the biggest opportunity to improve the funnel, and which channel/device should the business focus on first?**

This is a **portfolio practice project using synthetic data**. It is not based on real company or customer data.

---

## Dashboard Preview

![E-commerce Funnel Dashboard](assets/ecommerce-funnel-dashboard.png)

The dashboard is currently built in **Microsoft Excel**. I kept the design relatively simple because the focus of the project is on the analysis and the business decisions behind the numbers rather than visual decoration.

---

## Dataset

### What type of data am I working with?

The dataset represents weekly e-commerce funnel activity for a 12-week period.

Each record is broken down by:

- **Week** — Week 1 to Week 12
- **Channel** — Organic Search, Paid Ads, Email, Social
- **Device** — Desktop, Mobile, Tablet
- **Visits**
- **Product Views**
- **Add to Cart**
- **Checkout Started**
- **Purchases**

The data is **synthetic/generated for portfolio practice**. The purpose is to simulate the type of dataset an analyst might receive from an e-commerce business and then turn it into useful funnel insights.

### Data structure

The current setup has 4 acquisition channels and 3 device types for each week. With a complete 12-week combination, that represents:

**12 weeks × 4 channels × 3 devices = 144 rows**

The funnel metrics are sequential, meaning the number of users generally decreases as they move through the customer journey:

`Visits → Product Views → Add to Cart → Checkout Started → Purchases`

---

## Raw Data Preview

![Raw Dataset Preview](assets/raw-dataset-preview.png)

The screenshot above shows the structure of the working dataset. In the actual Excel workbook, the full 12-week dataset is used for the calculations and dashboard.

---

# Business Questions

I designed the analysis around a few questions that would actually matter to an e-commerce or growth team:

1. What percentage of visitors eventually purchase?
2. At which stage does the largest drop-off happen?
3. Which acquisition channel converts visitors into customers most effectively?
4. Which channel has the strongest movement from cart to checkout and checkout to purchase?
5. How does performance differ across desktop, mobile and tablet?
6. Is there a particular stage where improving conversion could create a meaningful revenue impact?
7. If checkout-to-purchase conversion improves, how many additional purchases could be generated?

---

# Analysis Process

I followed this general workflow rather than jumping directly into charts.

### 1. Understand the raw data

First, I checked the dimensions of the dataset and understood what each column represented. Since the data is funnel-based, I also checked that the stages followed a logical order.

### 2. Aggregate the funnel

I summed the users at each funnel stage across the 12-week period to get an overall view of the customer journey.

### 3. Calculate stage conversion

For each stage, I calculated conversion relative to the previous stage.

For example:

```text
Product View Conversion
= Product Views / Visits

Add-to-Cart Conversion
= Add to Cart / Product Views

Checkout Conversion
= Checkout Started / Add to Cart

Purchase Conversion
= Purchases / Checkout Started
```

### 4. Calculate stage drop-off

I used the complementary percentage to understand how many users were lost between two consecutive stages.

```text
Step Drop-off = 1 - Step Conversion
```

This makes it easier to identify the stage where the funnel is leaking the most users.

### 5. Segment the results

After looking at the overall funnel, I broke the results down by:

- Acquisition channel
- Device

This prevents the overall conversion rate from hiding important differences between customer segments.

### 6. Build the dashboard

Finally, I converted the calculations into a compact Excel dashboard with KPI tables and charts so that the main findings could be understood quickly.

---

# Key Results From the Current Analysis

Based on the current 12-week sample:

| Funnel Stage | Users | % of Visits |
|---|---:|---:|
| Visits | 310,627 | 100.0% |
| Product Views | 180,183 | 58.0% |
| Add to Cart | 49,166 | 15.8% |
| Checkout Started | 26,076 | 8.4% |
| Purchases | 14,597 | 4.7% |

### Overall conversion

The overall **Visit-to-Purchase conversion rate is 4.7%**.

That means roughly 4.7 out of every 100 visits result in a purchase in this sample.

### Biggest funnel drop-off

The largest stage drop-off is between **Product Views and Add to Cart**.

- Product View → Add to Cart conversion: **27.3%**
- Corresponding drop-off: **72.7%**

This is the first area I would investigate because a large number of users are viewing products but not showing enough intent to add them to the cart.

Possible business areas to investigate would include:

- Product pricing
- Product page quality
- Images and product information
- Reviews and trust signals
- Shipping costs or delivery expectations
- Availability/stock issues
- CTA placement and usability
- Mobile product-page experience

I would **not** treat these as confirmed causes from this dataset alone. They are hypotheses that would need additional data or testing.

---

# Channel Analysis

The channel-level results currently look like this:

| Channel | Visits | Purchases | Conversion Rate | Cart → Checkout | Checkout → Purchase |
|---|---:|---:|---:|---:|---:|
| Organic Search | 116,473 | 6,972 | 6.0% | 55.6% | 57.2% |
| Paid Ads | 91,296 | 2,401 | 2.6% | 45.4% | 47.6% |
| Email | 39,063 | 4,257 | 10.9% | 62.7% | 64.2% |
| Social | 63,795 | 967 | 1.5% | 39.9% | 43.5% |

## Chart: Conversion Rate by Channel

![Conversion Rate by Channel](assets/ecommerce-funnel-dashboard.png)

### Why did I choose a column/bar chart here?

A bar/column chart works well because the main purpose is **comparison between independent categories**. I want the difference between channels to be visible immediately.

A line chart would imply that the channels have an ordered progression, which they do not. A pie chart would also make comparison harder, especially when the objective is to compare conversion rates rather than show market share.

### What stands out?

**Email has the highest conversion rate at 10.9%**, followed by Organic Search at 6.0%.

Paid Ads convert at 2.6%, while Social is currently the weakest at 1.5%.

The important point is that I would not automatically conclude that Email should receive the most marketing budget. Email and paid acquisition serve different purposes and have different costs/scales. The next step would be to combine conversion with metrics such as spend, revenue, customer value and incremental conversions.

---

# Device Analysis

The device-level results are:

| Device | Visits | Purchases | Conversion Rate | Cart → Checkout | Checkout → Purchase |
|---|---:|---:|---:|---:|---:|
| Desktop | 108,839 | 6,597 | 6.1% | 55.1% | 66.4% |
| Mobile | 171,303 | 6,747 | 3.9% | 52.2% | 48.4% |
| Tablet | 30,485 | 1,253 | 4.1% | 49.2% | 57.0% |

### Why is device analysis useful?

Overall website conversion can hide a device-specific problem.

Mobile generates the largest amount of traffic in this sample, but its conversion rate is lower than desktop. More importantly, the **checkout-to-purchase rate on mobile is 48.4% compared with 66.4% on desktop**.

That makes mobile checkout a useful area for further investigation.

Potential hypotheses could include:

- Checkout usability
- Page speed
- Payment failures
- Form complexity
- Mobile UI issues
- Unexpected delivery charges
- Limited payment options

Again, these are hypotheses rather than conclusions because the current dataset does not contain the detailed diagnostic fields required to prove the cause.

---

# Funnel Chart

![Funnel Dashboard](assets/ecommerce-funnel-dashboard.png)

### Why did I choose a horizontal bar chart for the funnel stages?

The purpose of this visual is to show how quickly the user population decreases at every stage.

A horizontal bar chart makes the stage names easy to read and provides a direct visual comparison of user volume.

The chart clearly shows the large movement from:

**310,627 Visits → 180,183 Product Views → 49,166 Add to Cart → 26,076 Checkout → 14,597 Purchases**

The visual is useful because the drop-off is much easier to understand at a glance than from a table alone.

---

# What-if Analysis: Checkout Improvement

I also added a simple scenario analysis to connect conversion improvement with a potential business outcome.

### Current assumption

- Current checkout-to-purchase rate: **56.0%**
- Improvement assumption: **+5 percentage points**
- Additional purchases estimated: **1,304**
- Assumed AOV: **₹1,800**
- Estimated additional revenue: **₹23,46,840**

The revenue estimate is calculated as:

```text
Additional Revenue
= Additional Purchases × Assumed Average Order Value

= 1,304 × ₹1,800
= ₹23,46,840
```

### Why did I include a what-if analysis?

A dashboard should ideally go beyond describing what happened. It should also help answer **“So what?”**

The what-if section connects a conversion-rate improvement to a potential business outcome. This makes the analysis more useful from a decision-making perspective.

However, this is a **scenario, not a forecast**. The ₹1,800 AOV and +5 percentage-point improvement are assumptions for portfolio practice and would need to be replaced with actual business values in a real project.

---

# Chart Selection — My Reasoning

I did not want to add charts just to make the dashboard look busy. Each visual has a specific purpose.

| Visual | Purpose | Why I chose it |
|---|---|---|
| Funnel stage horizontal bars | Show user volume at each stage | Makes the decline through the funnel easy to see |
| Conversion rate by channel | Compare channels | Bar/column charts are effective for category comparison |
| KPI tables | Show exact values | Tables are better when precise numbers matter |
| What-if block | Show potential impact | Converts an analytical finding into a business scenario |

The main principle I followed was **one chart = one question**.

---

# Important Insights

From the current sample, I would highlight the following:

### 1. The overall funnel converts at 4.7%

The business is getting 14,597 purchases from 310,627 visits. This gives a useful baseline against which future improvements can be measured.

### 2. Product view → add-to-cart is the biggest leakage point

Only 27.3% of product viewers add an item to their cart. This is the largest stage-level drop-off in the current funnel.

### 3. Email is the strongest converting channel

Email has a 10.9% visit-to-purchase conversion rate, which is substantially higher than the other channels in this sample.

### 4. Social has the weakest conversion rate

Social converts at 1.5%. This does not automatically mean the channel should be stopped. I would first check audience quality, campaign intent, landing-page experience and acquisition cost.

### 5. Mobile deserves attention

Mobile accounts for the largest number of visits but converts at 3.9%, below desktop's 6.1%.

The lower mobile checkout-to-purchase rate is particularly interesting and would be a good starting point for a deeper UX/payment analysis.

---

# Limitations

There are several things this project intentionally does **not** try to claim.

### Synthetic data

The dataset is generated for portfolio practice and does not represent a real company's performance.

### No customer-level data

The current data is aggregated. I cannot identify individual customer journeys, repeat purchases or customer cohorts.

### No revenue/profit data in the raw dataset

The revenue scenario uses an assumed AOV of ₹1,800. Actual revenue analysis would require order value, discounts, refunds, shipping costs and ideally contribution margin.

### No marketing cost data

Conversion rate alone is not enough to evaluate channel profitability. A real channel analysis should also consider spend, CAC, ROAS and customer lifetime value.

### No diagnostic event data

The funnel tells me **where** users are dropping off, but not necessarily **why**. Additional event-level data would be required to investigate the cause.

---

# What I Would Do Next With Real Data

If I were working with this data in an actual e-commerce business, I would extend the analysis in the following direction:

1. **Add revenue and AOV** by channel and device.
2. Calculate **CAC, ROAS and contribution margin** for paid channels.
3. Break the funnel down by **week** to identify trends or sudden changes.
4. Compare conversion by **landing page/product/category**.
5. Investigate the mobile checkout journey using detailed event data.
6. Add **payment method** and payment-failure information.
7. Analyse new vs returning customers.
8. Build cohort analysis for customer retention and repeat purchases.
9. Use A/B testing data to validate improvements rather than relying only on observational comparisons.
10. Rebuild the dashboard in **Power BI** and connect it to SQL-based data preparation for a more scalable workflow.

---

# Tools Used

- **Microsoft Excel** — data aggregation, calculations, scenario analysis and dashboard creation
- **Excel Charts** — funnel and channel visualisation
- **Analytical thinking** — funnel analysis, segmentation, drop-off analysis and what-if modelling

### Potential next version

The next version of this project can move the data preparation into **SQL** and the reporting layer into **Power BI**, while keeping the same business questions and analytical logic.

---

# Project Structure

A simple repository structure for this project is:

```text
ecommerce-funnel-analysis/
│
├── README.md
├── data/
│   └── ecommerce_funnel_12_week_sample.xlsx
│
├── dashboard/
│   └── ecommerce_funnel_dashboard.xlsx
│
└── assets/
    ├── ecommerce-funnel-dashboard.png
    └── raw-dataset-preview.png
```

The Excel workbook contains the working calculations and dashboard, while this README explains the business problem, analytical process, chart choices and conclusions.

---

# Final Takeaway

The main thing I wanted to demonstrate through this project is that **funnel analysis is not just about calculating a conversion rate**.

The useful part is moving from:

**Raw data → Funnel metrics → Segmentation → Drop-off identification → Business hypothesis → What-if scenario → Recommended next analysis**

For this sample, the biggest opportunity appears to be around the **Product View → Add to Cart stage**, while **mobile checkout** is another area worth investigating. At the channel level, **Email and Organic Search show stronger conversion performance**, while Social and Paid Ads need more context before making any budget decision.

Because the data is synthetic, I would treat these findings as a demonstration of my analytical approach rather than claims about actual e-commerce performance.

---

## Author

**Divyanshu Rai**  
Supply Chain / Process Excellence | Analytics & Business Problem Solving

This project is part of my portfolio to demonstrate practical data analysis, business thinking and dashboard development using real-world style datasets.
