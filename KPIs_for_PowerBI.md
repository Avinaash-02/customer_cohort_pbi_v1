# Key Performance Indicators (KPIs) for Power BI Visualization
## Customer Cohort & Retention Analysis - NFX Case Study

---

## **1. CORE RETENTION & ENGAGEMENT KPIs**

### 1.1 Cohort Retention Rate
- **Definition:** Percentage of customers from a specific cohort (onboarding month) who remain active after X months
- **Data Source:** `Customer_Dimension` (customer_cohort, status), `Customer_Revenue_Fact` (revenue, invoice_date)
- **Calculation:** (Retained Customers in Cohort / Total Customers Onboarded in Cohort) × 100
- **Visualization:** Cohort Retention Matrix/Heatmap showing retention decay over time
- **Business Value:** Identify which onboarding periods produced the most loyal customers
- **Dimensions to Slice:** By acquisition_channel, service_tier, region, customer_size

### 1.2 Churn Rate
- **Definition:** Percentage of customers who stopped being active in a given time period
- **Data Source:** `Customer_Dimension` (status = 'Churned')
- **Calculation:** (Customers with Churned Status / Total Active Customers at Start of Period) × 100
- **Visualization:** Line chart showing churn trend over months, Gauge for current month churn %
- **Business Value:** Early warning indicator for customer attrition trends
- **Target Benchmark:** Compare against industry standards (aim for <15% monthly churn)
- **Dimensions:** By region, service_tier, acquisition_channel, customer_size

### 1.3 Active Customer Count (Daily/Weekly/Monthly)
- **Definition:** Total number of unique customers with revenue transactions or active_flag = 'Yes' in a period
- **Data Source:** `Customer_Revenue_Fact` (active_flag, invoice_date)
- **Calculation:** Count of distinct customer_ids where active_flag = 'Yes' for the time period
- **Visualization:** Multi-line chart (Daily, Weekly, Monthly active users), Scorecard showing current active count
- **Business Value:** Measure platform engagement and usage trends
- **Dimensions:** By service_line, engagement_bucket, region, acquisition_channel

### 1.4 Engagement Bucket Distribution
- **Definition:** Breakdown of customers by engagement level
- **Data Source:** `Customer_Revenue_Fact` (engagement_bucket)
- **Calculation:** Count of distinct customers in each engagement_bucket category
- **Visualization:** Stacked bar chart, Pie chart showing segment distribution
- **Business Value:** Identify at-risk customers (low engagement) and advocates (high engagement)
- **Engagement Levels:** Typically High/Medium/Low based on transaction frequency
- **Dimensions:** By cohort, region, service_tier

---

## **2. CUSTOMER ACQUISITION & CHANNEL PERFORMANCE KPIs**

### 2.1 New Customers per Month
- **Definition:** Total number of new customers acquired in each month
- **Data Source:** `Customer_Dimension` (onboard_date)
- **Calculation:** Count of distinct customer_ids by month from onboard_date
- **Visualization:** Column chart showing acquisition trend, YoY comparison
- **Business Value:** Track acquisition pipeline effectiveness and growth trajectory
- **Dimensions:** By acquisition_channel, service_tier, region

### 2.2 Customer Acquisition Cost (CAC) by Channel
- **Definition:** Average cost per customer acquired through each channel
- **Data Source:** `Customer_Dimension` (acquisition_channel), Marketing spend data (external)
- **Calculation:** Total Marketing Spend by Channel / Number of Customers from Channel
- **Visualization:** Bar chart comparing CAC by channel, Gauge for average CAC
- **Business Value:** Optimize marketing budget allocation and identify ROI by channel
- **Note:** Requires linking marketing spend data to acquisition_channel

### 2.3 Channel Effectiveness Score
- **Definition:** Weighted score based on acquisition volume, customer quality, and retention
- **Data Source:** `Customer_Dimension`, `Customer_Revenue_Fact`
- **Calculation:** (Customers Acquired × Retention Rate × Avg Revenue per Customer) / Total Possible
- **Visualization:** Ranked scorecard or bar chart by channel
- **Business Value:** Identify best-performing acquisition channels for investment
- **Dimensions:** Show growth rate, churn rate, revenue contribution

### 2.4 Customer Lifetime Value (CLV) by Channel
- **Definition:** Total expected revenue from a customer acquired through a specific channel
- **Data Source:** `Customer_Dimension` (acquisition_channel), `Customer_Revenue_Fact` (revenue)
- **Calculation:** Sum of all revenue per customer, grouped by acquisition_channel
- **Visualization:** Horizontal bar chart showing CLV by channel, Comparison with CAC
- **Business Value:** Determine true ROI of acquisition channels; CAC Payback Period analysis
- **Segments:** Track CLV by service_tier and region

---

## **3. ONBOARDING & TIME-TO-VALUE KPIs**

### 3.1 Time to First Action (Days)
- **Definition:** Number of days from onboarding until customer's first revenue transaction
- **Data Source:** `Customer_Revenue_Fact` (time_to_first_action_days)
- **Calculation:** Average/Median/Percentile of time_to_first_action_days by cohort
- **Visualization:** Box plot, Distribution histogram, Trend line showing improvement over cohorts
- **Business Value:** Measure onboarding efficiency; identify and resolve activation bottlenecks
- **Target Benchmark:** Aim for median <7 days, identify cohorts with >14 day delays
- **Dimensions:** By acquisition_channel, service_tier, region, customer_size

### 3.2 Customer Activation Rate
- **Definition:** Percentage of customers who made at least one transaction within X days of onboarding
- **Data Source:** `Customer_Revenue_Fact` (time_to_first_action_days)
- **Calculation:** (Customers with time_to_first_action ≤ X days / Total Customers Onboarded) × 100
- **Visualization:** Gauge chart (% activated within 7 days), Waterfall chart showing activation funnel
- **Business Value:** Indicator of onboarding experience quality and product fit
- **Thresholds:** Track 7-day, 14-day, 30-day activation rates
- **Dimensions:** By channel, cohort, service_tier

### 3.3 Onboarding Speed by Channel & Cohort
- **Definition:** Comparative analysis of how quickly customers engage across segments
- **Data Source:** `Customer_Dimension`, `Customer_Revenue_Fact`
- **Calculation:** Average days to first action grouped by acquisition_channel and customer_cohort
- **Visualization:** Heatmap or matrix showing speed scores by channel × cohort
- **Business Value:** Identify which channels produce fast-to-engage customers
- **Action Items:** Replicate onboarding processes from faster channels

---

## **4. REVENUE & PROFITABILITY KPIs**

### 4.1 Total Revenue by Cohort
- **Definition:** Cumulative revenue generated from customers in each onboarding cohort
- **Data Source:** `Customer_Revenue_Fact` (revenue, invoice_date), `Customer_Dimension` (customer_cohort)
- **Calculation:** Sum of revenue grouped by customer_cohort and time period
- **Visualization:** Stacked area chart showing revenue contribution by cohort over time
- **Business Value:** Understand which cohorts have the highest lifetime value
- **Dimensions:** By service_line, region, customer_size

### 4.2 Average Revenue Per User (ARPU) by Segment
- **Definition:** Average revenue generated per customer in each segment
- **Data Source:** `Customer_Revenue_Fact` (revenue), `Customer_Dimension`
- **Calculation:** Total Revenue / Number of Unique Customers by segment
- **Visualization:** Bar chart by service_tier, region; Trend line showing ARPU evolution
- **Business Value:** Identify highest-value customer segments for retention focus
- **Dimensions:** By acquisition_channel, service_tier, engagement_bucket, customer_size

### 4.3 Revenue per Transaction
- **Definition:** Average revenue value per individual transaction
- **Data Source:** `Customer_Revenue_Fact` (revenue)
- **Calculation:** Sum of all revenue / Count of transactions
- **Visualization:** Gauge chart, KPI card, Distribution histogram
- **Business Value:** Understand transaction value trends and pricing effectiveness

### 4.4 Month-over-Month (MoM) Revenue Growth
- **Definition:** Percentage change in revenue from one month to the next
- **Data Source:** `Customer_Revenue_Fact` (revenue, invoice_date)
- **Calculation:** ((Current Month Revenue - Previous Month Revenue) / Previous Month Revenue) × 100
- **Visualization:** Line chart showing growth rate trend, Gauge for current MoM %
- **Business Value:** Track business momentum and identify growth/decline periods
- **Benchmark:** Compare growth by cohort, channel, and service line

---

## **5. PRODUCT & SERVICE ADOPTION KPIs**

### 5.1 Cross-Product Holding (Product Adoption Rate)
- **Definition:** Number of different services/products each customer uses
- **Data Source:** `Customer_Revenue_Fact` (cross_holding_products)
- **Calculation:** Average/Distribution of cross_holding_products per customer
- **Visualization:** Box plot, Histogram, Distribution curve showing adoption range
- **Business Value:** Measure upsell/cross-sell success; identify single-product vs. multi-product customers
- **Target:** Increase average from current baseline to 4+ products per customer
- **Dimensions:** By cohort, service_tier, region, engagement_bucket

### 5.2 Product Adoption Velocity
- **Definition:** How quickly customers expand from 1 product to multiple products
- **Data Source:** `Customer_Revenue_Fact` (cross_holding_products, invoice_date)
- **Calculation:** Median time to reach 2+ products, 3+ products from first purchase
- **Visualization:** Survival/adoption curve showing % of customers reaching each product tier over time
- **Business Value:** Understand growth trajectory and identify expansion opportunities
- **Dimensions:** By acquisition_channel, service_tier

### 5.3 Service Line Performance
- **Definition:** Revenue and customer count by each service line offering
- **Data Source:** `Customer_Revenue_Fact` (service_line_id, revenue), `Service_Line` (reference table)
- **Calculation:** Sum revenue and count customers by service_line
- **Visualization:** Ranked bar chart, Pie chart showing revenue mix, Line chart for top services
- **Business Value:** Identify flagship services and underperforming offerings
- **Dimensions:** By region, customer_size, engagement_bucket

---

## **6. CUSTOMER REACTIVATION KPIs**

### 6.1 Reactivation Rate
- **Definition:** Percentage of previously inactive customers who resume activity
- **Data Source:** `Customer_Revenue_Fact` (reactivation_event)
- **Calculation:** (Customers with reactivation_event = 'Yes' / Total Churned Customers) × 100
- **Visualization:** Gauge chart showing reactivation %, Waterfall showing recovery flow
- **Business Value:** Measure win-back campaign effectiveness and save rate
- **Benchmark:** Compare reactivation success by cohort and acquisition channel
- **Dimensions:** By time since churn, original service tier, region

### 6.2 Time to Reactivation
- **Definition:** Days between churn and return to active status
- **Data Source:** Derived from transaction history and reactivation events
- **Calculation:** Average days between last transaction and reactivation transaction
- **Visualization:** Distribution histogram, Trend line showing reactivation speed improvement
- **Business Value:** Evaluate effectiveness of win-back campaigns and timing
- **Insights:** Identify optimal window for re-engagement efforts

---

## **7. GEOGRAPHIC & DEMOGRAPHIC KPIS**

### 7.1 Regional Performance Dashboard
- **Definition:** Comparative metrics across geographic regions
- **Data Source:** `Customer_Dimension` (region, city)
- **Metrics Included:**
  - Total customers and active customers by region
  - Regional retention rate and churn rate
  - Revenue contribution by region
  - New customers acquired by region
- **Visualization:** Map showing regional performance, Regional comparison chart
- **Business Value:** Identify strongest and weakest markets; geo-specific strategies
- **Dimensions:** By city, acquisition_channel, service_tier

### 7.2 Customer Size Performance
- **Definition:** Metrics segmented by business size classification
- **Data Source:** `Customer_Dimension` (customer_size)
- **Metrics Included:**
  - Count and revenue by customer_size
  - Average ARPU and CLV
  - Retention rate by size
  - Product adoption rate
- **Visualization:** Grouped bar charts, Comparative cards by size
- **Business Value:** Understand if SMBs or Enterprise customers are more valuable
- **Strategic Use:** Tailor acquisition and retention strategies by size

### 7.3 Service Tier Analysis
- **Definition:** Performance metrics by subscription/service tier
- **Data Source:** `Customer_Dimension` (service_tier)
- **Metrics Included:**
  - Customer count and revenue per tier
  - Churn rate and retention by tier
  - Time to first action by tier
  - Upgrade/downgrade rates
- **Visualization:** Waterfall chart, Stacked bar chart, Tier comparison scorecard
- **Business Value:** Identify which tier drives profitability and loyalty

---

## **8. ANOMALY & HEALTH CHECK KPIs**

### 8.1 Customer Health Score
- **Definition:** Composite metric indicating customer satisfaction and churn risk
- **Data Source:** Multiple fields from `Customer_Dimension` and `Customer_Revenue_Fact`
- **Calculation:** Weighted combination of:
  - Engagement level (40%)
  - Revenue trend (30%)
  - Time since last activity (20%)
  - Product adoption (10%)
- **Visualization:** Gauge by customer segment, Distribution showing at-risk vs. healthy
- **Business Value:** Proactive identification of at-risk customers for retention outreach
- **Segmentation:** Color-coded (Red/Yellow/Green) for immediate action visibility

### 8.2 Month-over-Month Churn Variation
- **Definition:** Tracking whether churn rate is increasing, stable, or decreasing
- **Data Source:** `Customer_Dimension` (status)
- **Calculation:** (Current Month Churn Rate - Previous Month Churn Rate) / Previous Month Churn Rate
- **Visualization:** Trend line, Variance gauge showing direction and magnitude
- **Business Value:** Early warning system for unexpected churn escalation
- **Alerts:** Flag if variation > ±5% from trend

### 8.3 Cohort Health Over Time
- **Definition:** Monitoring degradation or improvement in each cohort's engagement
- **Data Source:** `Customer_Dimension`, `Customer_Revenue_Fact`
- **Calculation:** Rolling average of active_flag by cohort across months
- **Visualization:** Multi-line chart showing health trajectory for top cohorts
- **Business Value:** Identify if recently onboarded cohorts are underperforming

---

## **9. ADVANCED/PREDICTIVE KPIs**

### 9.1 Revenue Concentration Index (Herfindahl Index)
- **Definition:** Measure of revenue dependency on specific customer segments
- **Data Source:** `Customer_Revenue_Fact` (revenue)
- **Calculation:** Sum of (Revenue by Customer / Total Revenue)² across all customers
- **Visualization:** Single metric card showing concentration level (0-1 scale)
- **Business Value:** Identify over-reliance on few customers; diversification needs
- **Range:** 0 = perfectly distributed; 1 = single customer concentration

### 9.2 Cohort Strength Ranking
- **Definition:** Composite ranking of cohorts by overall business contribution
- **Data Source:** All prior KPIs combined
- **Calculation:** Weighted score of retention × ARPU × product adoption × growth rate
- **Visualization:** Ranked scorecard, Bubble chart showing cohort positioning
- **Business Value:** Strategic resource allocation to nurture high-performing cohorts

### 9.3 Customer Lifetime Profitability
- **Definition:** Net profit expected from customer lifetime minus acquisition and operational costs
- **Data Source:** `Customer_Revenue_Fact` (revenue), Cost data (external)
- **Calculation:** Total Revenue - COGS - Customer Acquisition Cost - Operational Cost
- **Visualization:** Distribution curve, Segment breakdown showing profitable vs. loss-making segments
- **Business Value:** Identify most/least profitable customer types for strategic focus
- **Payback Period:** Show when each segment breaks even

---

## **10. DASHBOARD COMPOSITION RECOMMENDATIONS**

### **Executive Summary Dashboard**
- KPIs: Total Customers, Active Customers, Churn Rate, Total Revenue, ARPU
- Visualizations: 5 large KPI cards with trend indicators

### **Retention & Cohort Health Dashboard**
- KPIs: Cohort Retention Heatmap, Churn Rate Trend, Engagement Distribution
- Visualizations: Cohort matrix, Line chart with trends by dimension

### **Channel Performance Dashboard**
- KPIs: New Customers by Channel, CLV by Channel, Activation Rate by Channel
- Visualizations: Stacked bar, Comparison cards, Scatter plot (CAC vs CLV)

### **Product & Revenue Dashboard**
- KPIs: Cross-Product Adoption, Revenue by Service Line, ARPU, MoM Growth
- Visualizations: Adoption curve, Revenue trend, Tier comparison

### **Geographic & Segment Performance Dashboard**
- KPIs: Regional Performance, Customer Size Analysis, Service Tier Breakdown
- Visualizations: Map, Waterfall chart, Comparative scorecard

### **Risk & Health Dashboard**
- KPIs: At-Risk Customers, Health Score Distribution, Reactivation Opportunities
- Visualizations: Gauge charts, Distribution histogram, Waterfall

---

## **11. DATA REQUIREMENTS FOR KPI CALCULATION**

| Required Field | Location | Usage |
|---|---|---|
| customer_id | Customer_Dimension | Join transactions with customer attributes |
| onboard_date | Customer_Dimension | Calculate cohort, time in customer |
| status | Customer_Dimension | Determine churn status |
| acquisition_channel | Customer_Dimension | Channel performance analysis |
| invoice_date | Customer_Revenue_Fact | Period grouping, time calculations |
| revenue | Customer_Revenue_Fact | All financial metrics |
| active_flag | Customer_Revenue_Fact | Active customer counts |
| engagement_bucket | Customer_Revenue_Fact | Engagement segmentation |
| cross_holding_products | Customer_Revenue_Fact | Product adoption metrics |
| time_to_first_action_days | Customer_Revenue_Fact | Onboarding efficiency |
| reactivation_event | Customer_Revenue_Fact | Win-back tracking |
| service_line_id / service_name | Customer_Revenue_Fact | Service analysis |
| region / city | Customer_Dimension | Geographic analysis |
| service_tier | Customer_Dimension | Tier-based segmentation |
| customer_size | Customer_Dimension | Size-based analysis |

---

## **12. IMPLEMENTATION PRIORITY**

### **Tier 1 (Must-Have for MVP)**
1. Cohort Retention Rate
2. Churn Rate
3. Active Customer Count
4. New Customers per Month
5. Total Revenue by Cohort
6. ARPU by Segment

### **Tier 2 (Should-Have for v1.1)**
1. Time to First Action
2. Product Adoption Rate
3. Service Line Performance
4. Revenue by Channel
5. Customer Health Score

### **Tier 3 (Nice-to-Have for v2.0)**
1. CLV by Channel
2. Reactivation Rate
3. Regional Performance Dashboard
4. Predictive Health Scores
5. Advanced Cohort Analysis

---

**Document Version:** 1.0 | **Last Updated:** May 2026 | **Project:** NFX Customer Cohort & Retention Analysis
