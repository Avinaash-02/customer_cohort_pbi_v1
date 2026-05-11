# Project Overview & Complete Workflow Guide
## Customer Cohort & Retention Analysis for NFX

---

## **TABLE OF CONTENTS**
1. [Project Executive Summary](#1-project-executive-summary)
2. [Problem Statement](#2-problem-statement)
3. [Project Objectives](#3-project-objectives)
4. [Data Overview](#4-data-overview)
5. [Stakeholders & Roles](#5-stakeholders--roles)
6. [Workflow Steps: Start to End](#6-workflow-steps-start-to-end)
7. [Key Deliverables](#7-key-deliverables)
8. [Timeline & Milestones](#8-timeline--milestones)
9. [Success Criteria](#9-success-criteria)
10. [Post-Launch Support](#10-post-launch-support)

---

## **1. PROJECT EXECUTIVE SUMMARY**

### **Project Name:** 
Customer Cohort & Retention Analysis - NFX Case Study

### **Organization:** 
NFX (Digital-First Professional Services Company)

### **Project Duration:** 
4-5 weeks (Definition through Power BI dashboard delivery)

### **Business Context:**
NFX has achieved steady customer acquisition but faces challenges with:
- Inconsistent platform engagement and repeat usage
- Limited visibility into customer loyalty and lifecycle patterns
- Unclear effectiveness of different acquisition channels
- Lack of retention trend data by customer segments

### **Strategic Goal:**
Develop comprehensive analytics to understand customer retention patterns, identify high-value segments, and provide data-driven recommendations to improve long-term customer loyalty and reduce churn.

### **Business Impact:**
- Improve customer retention by identifying at-risk segments
- Optimize acquisition channel spend based on lifetime value
- Enhance onboarding process to accelerate time-to-value
- Increase product adoption through targeted cross-sell strategies

---

## **2. PROBLEM STATEMENT**

### **Current Situation:**
- NFX has acquired over 10,000 customers with 149,698+ transactions recorded
- Despite consistent acquisition, engagement levels remain inconsistent
- No systematic understanding of which customer cohorts are most loyal
- Unclear which acquisition channels drive long-term value vs. short-term acquisition
- Lack of visibility into geographic, service tier, and customer size performance
- No proactive mechanism to identify and reactivate churned customers

### **Business Questions to Answer:**
1. **Retention:** Which customer cohorts exhibit the highest retention rates? How do retention patterns vary by acquisition channel?
2. **Churn:** What are the churn trends? Which segments are most at-risk?
3. **Onboarding:** How quickly do customers engage after signup? Where are activation bottlenecks?
4. **Revenue:** Which segments generate the highest lifetime value? How does ARPU vary?
5. **Product:** What is the cross-product adoption rate? How can we accelerate expansion?
6. **Geographic:** Which regions and customer sizes are most valuable and loyal?
7. **Strategy:** Where should we focus retention investments for maximum impact?

### **Data Gap:**
- Historical transaction data exists but lacks cohesive analysis and visualization
- No unified view of customer journey from acquisition to churn/retention
- Missing connection between acquisition channel effectiveness and long-term outcomes
- No quantified KPIs or benchmarks for segment performance

---

## **3. PROJECT OBJECTIVES**

### **Primary Objectives:**

#### **OBJ-1: Understand Retention Patterns**
- Develop cohort-based retention analysis
- Create retention curves by acquisition channel, geography, service tier
- Identify early warning signs of churn
- **Success Metric:** Ability to forecast retention rates by segment with >80% accuracy

#### **OBJ-2: Evaluate Channel Effectiveness**
- Calculate Customer Lifetime Value (CLV) by acquisition channel
- Compare Customer Acquisition Cost (CAC) ROI across channels
- Identify best-performing channels for investment scaling
- **Success Metric:** Clear ranking of channels by profitability and retention

#### **OBJ-3: Accelerate Customer Activation**
- Analyze time-to-first-action by cohort and segment
- Identify onboarding bottlenecks
- Benchmark onboarding speed against industry standards
- **Success Metric:** Identify optimization opportunities for <7-day activation

#### **OBJ-4: Maximize Customer Lifetime Value**
- Segment customers by engagement level and profitability
- Develop targeted retention strategies by segment
- Create product adoption roadmaps for expansion
- **Success Metric:** Increase ARPU through data-driven product positioning

#### **OBJ-5: Enable Data-Driven Decision Making**
- Deliver interactive Power BI dashboard with real-time metrics
- Create self-service analytics for different stakeholder groups
- Enable quick scenario analysis and trend exploration
- **Success Metric:** Dashboard adoption >70% among target users

### **Secondary Objectives:**
- Identify reactivation opportunities for churned customers
- Create repeatable methodology for ongoing cohort analysis
- Establish performance benchmarks for future tracking
- Document insights and recommendations for strategic initiatives

---

## **4. DATA OVERVIEW**

### **Data Sources:**
- **Primary File:** `NFX_Customer_Cohort_CaseStudy_Data.xlsx` (3 sheets)
- **Supporting File:** `customer_cohort_analysis.pbix` (existing Power BI model)

### **Data Structure:**

#### **Sheet 1: Customer Dimension (10,000 records)**
Unique customer profiles with attributes for segmentation

| Field | Type | Purpose |
|-------|------|---------|
| customer_id | Integer | Primary key for customer |
| customer_name | String | Customer identifier |
| region | String | Geographic region (country/area) |
| city | String | City location |
| service_tier | String | Service package level (e.g., Basic, Premium, Enterprise) |
| acquisition_channel | String | How acquired (Direct, Partner, Affiliate, Paid Ads, etc.) |
| customer_size | String | Business size (SMB, Mid-Market, Enterprise) |
| customer_cohort | String | Onboarding month/year cohort |
| onboard_date | Date | Customer start date (DD-MM-YYYY format) |
| status | String | Current status (Active/Churned) |

**Key Insights:**
- 10,000 unique customers across multiple regions
- Multiple acquisition channels represented
- Status field indicates whether customer is retained or churned
- Cohort field enables period-based analysis

#### **Sheet 2: Service Line (22 records)**
Reference table of available services/products

| Field | Type | Purpose |
|-------|------|---------|
| service_line_id | Integer | Primary key |
| service_line_name | String | Service offering name |

**Services Include:**
- Occupational Hygiene
- Physiotherapy
- Flu Services
- NHS Revenue
- Medical Emergencies
- (17 additional services)

#### **Sheet 3: Customer Revenue Fact (149,698 records)**
Transaction-level data capturing revenue and engagement

| Field | Type | Purpose |
|-------|------|---------|
| customer_id | Integer | Foreign key to Customer Dimension |
| service_line_id | Integer | Foreign key to Service Line |
| service_name | String | Service provided (denormalized) |
| invoice_date | Date | Transaction date |
| revenue | Currency | Revenue from transaction |
| active_flag | String | Engagement indicator (Yes/No) |
| engagement_bucket | String | Engagement level (High/Medium/Low) |
| time_to_first_action_days | Integer | Days from onboard to first transaction |
| reactivation_event | String | Win-back indicator (Yes/No) |
| cross_holding_products | Integer | Number of products customer uses (1-5 range) |

**Data Characteristics:**
- 149,698 transactions from 10,000 customers = ~15 transactions per customer average
- Spans multiple time periods enabling trend analysis
- Rich engagement and behavioral indicators

### **Data Quality Considerations:**
- ✓ Complete and structured format
- ✓ Consistent date formatting enabling analysis
- ✓ Sufficient historical depth for cohort tracking (multiple years)
- ✓ Granular transaction-level detail
- ⚠ Assume data is clean (validate for nulls, duplicates during analysis)

---

## **5. STAKEHOLDERS & ROLES**

### **Executive Stakeholders:**
- **Chief Marketing Officer (CMO):** Oversees acquisition channel optimization and ROI
- **Chief Customer Officer (CCO):** Owns customer retention and experience strategy
- **Chief Financial Officer (CFO):** Focuses on CLV and customer profitability

### **Project Team:**
- **Project Manager:** Coordinates timeline, deliverables, and stakeholder communication
- **Data Analyst:** Performs data exploration, validates quality, creates analysis
- **Power BI Developer:** Builds dashboard, creates visualizations, ensures performance
- **Business Analyst:** Translates requirements, validates outputs, prepares recommendations

### **End Users:**
- **Marketing Leadership:** Channel performance analysis, acquisition optimization
- **Customer Success Leadership:** Retention insights, at-risk customer identification
- **Finance/Revenue Operations:** Revenue trends, profitability analysis, forecasting
- **Product Leadership:** Product adoption metrics, cross-sell opportunities

### **Governance:**
- **Data Governance:** IT/Data team ensures data security and compliance
- **Business Approval:** Executive sponsor validates findings and recommendations
- **Access Control:** Role-based access to sensitive customer data

---

## **6. WORKFLOW STEPS: START TO END**

### **PHASE 1: PLANNING & REQUIREMENTS (Days 1-5)**

#### **Step 1.1: Project Kickoff**
- **Participants:** Executive sponsor, project manager, core team
- **Activities:**
  - Review case study document and business objectives
  - Confirm project scope and success criteria
  - Identify critical business questions to answer
  - Establish governance and approval processes
- **Deliverable:** Project charter and requirements document
- **Owner:** Project Manager
- **Duration:** 1 day

#### **Step 1.2: Stakeholder Requirements Gathering**
- **Participants:** Business analyst, key stakeholders from marketing, customer success, finance
- **Activities:**
  - Conduct stakeholder interviews (CMO, CCO, Product lead)
  - Identify specific metrics and KPIs needed
  - Understand dashboard usage patterns and user types
  - Gather reporting frequency requirements
  - Document ad-hoc analysis requests
- **Deliverable:** Detailed requirements document, KPI prioritization matrix
- **Owner:** Business Analyst
- **Duration:** 2 days

#### **Step 1.3: Data Source Validation**
- **Participants:** Data analyst, IT team
- **Activities:**
  - Verify data file availability and accessibility
  - Confirm data refresh frequency (one-time vs. recurring)
  - Assess file size and performance implications
  - Identify any missing or problematic fields
  - Document data lineage and definitions
- **Deliverable:** Data source inventory and validation report
- **Owner:** Data Analyst
- **Duration:** 1 day

#### **Step 1.4: Technical Architecture Planning**
- **Participants:** Power BI developer, IT infrastructure team
- **Activities:**
  - Determine Power BI deployment approach (Desktop, Service, Cloud)
  - Plan data load and refresh strategy
  - Assess performance requirements and optimization needs
  - Design security and access control model
  - Plan for scalability and future growth
- **Deliverable:** Technical architecture document
- **Owner:** Power BI Developer
- **Duration:** 1 day

---

### **PHASE 2: DATA EXPLORATION & ANALYSIS (Days 6-12)**

#### **Step 2.1: Data Import and Preparation**
- **Participants:** Data analyst, Power BI developer
- **Activities:**
  - Import data from Excel file into Power BI Desktop
  - Verify data types and formats
  - Check for null values, duplicates, outliers
  - Validate record counts against source
  - Document any data quality issues
- **Deliverable:** Data preparation checklist, quality report
- **Owner:** Data Analyst
- **Duration:** 1 day

#### **Step 2.2: Exploratory Data Analysis (EDA)**
- **Participants:** Data analyst
- **Activities:**
  - Calculate descriptive statistics for all key fields
  - Identify distribution patterns in key variables
  - Explore relationships between dimensions
  - Analyze time period coverage and data recency
  - Create summary statistics by key segments
  - Example analyses:
    - Customers by region, service tier, acquisition channel
    - Revenue distribution by customer, time period
    - Engagement levels and distribution
    - Time-to-first-action statistics
    - Product adoption rates
- **Deliverable:** EDA report with summary statistics and visualizations
- **Owner:** Data Analyst
- **Duration:** 2 days

#### **Step 2.3: Cohort Definition and Calculation**
- **Participants:** Data analyst, business analyst
- **Activities:**
  - Verify cohort definitions in onboard_date field
  - Create cohort date tables (by month, quarter)
  - Calculate cohort size and characteristics
  - Identify completeness of cohort data
  - Establish baseline metrics by cohort
  - Example outputs:
    - 2024-01 cohort: 850 customers, 15% churn, $4.2M revenue
    - 2024-02 cohort: 920 customers, 12% churn, $5.1M revenue
- **Deliverable:** Cohort summary table, cohort analysis baseline report
- **Owner:** Data Analyst
- **Duration:** 2 days

#### **Step 2.4: Key Metric Validation**
- **Participants:** Data analyst, business analyst
- **Activities:**
  - Calculate core metrics from data:
    - Active customer counts by period
    - Churn rates by segment
    - Revenue totals by cohort
    - Time-to-first-action by channel
    - Product adoption rates
  - Validate against known business metrics
  - Identify any discrepancies to reconcile
  - Establish metric definitions and calculation methods
- **Deliverable:** Metric validation report, metric definitions document
- **Owner:** Data Analyst
- **Duration:** 1 day

#### **Step 2.5: Segment Performance Analysis**
- **Participants:** Data analyst, business analyst
- **Activities:**
  - Analyze performance by acquisition channel
    - Customer count, churn rate, CLV, onboarding speed
  - Analyze performance by geography
    - Revenue contribution, customer size, retention
  - Analyze performance by service tier
    - Customer count, ARPU, engagement level
  - Analyze performance by customer size
    - Growth potential, churn risk, product adoption
  - Identify high-value and at-risk segments
- **Deliverable:** Segment performance summary, recommendations for focus areas
- **Owner:** Data Analyst
- **Duration:** 1 day

---

### **PHASE 3: DATA MODEL & TRANSFORMATION (Days 13-17)**

#### **Step 3.1: Create Data Model**
- **Participants:** Power BI developer, data analyst
- **Activities:**
  - Design star schema with fact and dimension tables
  - Create relationships between tables (Customer_Dimension ←→ Customer_Revenue_Fact)
  - Establish primary and foreign keys
  - Optimize for query performance
  - Model structure:
    - **Fact Table:** Customer_Revenue_Fact (transactions)
    - **Dimension Tables:** 
      - Customer_Dimension (customer attributes)
      - Service_Line (products)
      - Date_Dimension (time periods)
- **Deliverable:** Data model diagram, relationship definitions
- **Owner:** Power BI Developer
- **Duration:** 1 day

#### **Step 3.2: Create Calculated Columns**
- **Participants:** Power BI developer, data analyst
- **Activities:**
  - Add calculated columns needed for analysis:
    - YearMonth from invoice_date
    - DaysActive (from onboard_date to invoice_date)
    - MonthsSinceOnboard
    - QuarterOnboarded
    - Revenue Tier (by amount)
    - Engagement Classification
    - Churn Indicator (0/1)
  - Ensure calculations are accurate and performant
  - Document calculation logic
- **Deliverable:** Calculated columns specifications, validation report
- **Owner:** Power BI Developer
- **Duration:** 1 day

#### **Step 3.3: Create Measures and KPI Definitions**
- **Participants:** Power BI developer, data analyst, business analyst
- **Activities:**
  - Develop DAX measures for all KPIs:
    - `Total Customers = COUNT(Customer_Dimension[customer_id])`
    - `Active Customers = CALCULATE(COUNT(...), active_flag = "Yes")`
    - `Churn Rate = DIVIDE(Churned Customers, Total Customers)`
    - `Total Revenue = SUM(Customer_Revenue_Fact[revenue])`
    - `ARPU = DIVIDE(Total Revenue, Total Customers)`
    - Time-to-first-action measures
    - Cohort retention calculations
  - Validate measure calculations against EDA
  - Optimize for performance
  - Document measure definitions and assumptions
- **Deliverable:** Measures library, measure calculation document
- **Owner:** Power BI Developer
- **Duration:** 2 days

#### **Step 3.4: Create Date Dimension**
- **Participants:** Power BI developer
- **Activities:**
  - Create comprehensive date table (if not provided)
  - Include calendar hierarchy (Year, Quarter, Month, Week, Day)
  - Add fiscal period fields if applicable
  - Add holiday/special date flags
  - Ensure covers entire data range with forward projection
- **Deliverable:** Date dimension table, calendar specifications
- **Owner:** Power BI Developer
- **Duration:** 1 day

---

### **PHASE 4: DASHBOARD DESIGN & DEVELOPMENT (Days 18-27)**

#### **Step 4.1: Dashboard Wireframe & Design**
- **Participants:** Power BI developer, business analyst, stakeholders
- **Activities:**
  - Design dashboard layout for each stakeholder group:
    - **Executive Dashboard:** 5-6 KPI cards with trends
    - **Retention Dashboard:** Cohort matrix, churn trends, segment breakdown
    - **Channel Performance:** Channel comparison, CAC/CLV analysis
    - **Product & Revenue:** Service line performance, adoption rates
    - **Regional Dashboard:** Geographic breakdown, segment performance
    - **Risk & Health:** At-risk customers, health scores, reactivation opportunities
  - Create wireframes for each dashboard
  - Identify filters and drill-down capabilities needed
  - Plan color scheme and visual hierarchy
  - Define page layout and navigation flow
- **Deliverable:** Dashboard wireframes, design specifications
- **Owner:** Power BI Developer (with Business Analyst review)
- **Duration:** 2 days

#### **Step 4.2: Build Executive Summary Dashboard**
- **Participants:** Power BI developer
- **Activities:**
  - Create landing page with top-level metrics:
    - Total Customers (current, vs. prior period)
    - Active Customers (current, vs. prior period)
    - Total Revenue (current, vs. prior period)
    - Churn Rate (current, vs. prior period)
    - Average ARPU (with trend)
  - Add visual indicators (up/down arrows for trends)
  - Add slicers for filtering (Date, Region, Channel, Service Tier)
  - Include navigation to detailed dashboards
  - Design for C-level audience (minimal detail, focus on summary)
- **Deliverable:** Executive dashboard page
- **Owner:** Power BI Developer
- **Duration:** 2 days

#### **Step 4.3: Build Cohort & Retention Dashboard**
- **Participants:** Power BI developer
- **Activities:**
  - Create cohort retention heatmap/matrix
    - Rows: Onboarding cohorts (months)
    - Columns: Months since onboard
    - Values: Retention rate percentage
    - Color scale showing retention decay
  - Create churn rate trend line chart
  - Create segment comparison (retention by channel, tier, region)
  - Create engagement bucket distribution
  - Add drill-down capability to see customer lists
  - Include interactive filters
- **Deliverable:** Cohort & retention dashboard pages
- **Owner:** Power BI Developer
- **Duration:** 3 days

#### **Step 4.4: Build Channel Performance Dashboard**
- **Participants:** Power BI developer
- **Activities:**
  - Create new customers acquired by channel (bar chart, trend)
  - Create revenue by channel (stacked bar, trend)
  - Create CAC vs. CLV comparison (scatter or bar chart)
  - Create acquisition channel rankings
  - Create onboarding speed by channel
  - Create activation rate by channel
  - Add channel profitability metrics
- **Deliverable:** Channel performance dashboard pages
- **Owner:** Power BI Developer
- **Duration:** 2 days

#### **Step 4.5: Build Product & Revenue Dashboard**
- **Participants:** Power BI developer
- **Activities:**
  - Create service line performance breakdown (revenue, customer count)
  - Create product adoption curve
  - Create cross-holding products distribution
  - Create revenue trend by time period (MoM growth)
  - Create revenue per transaction metrics
  - Create segment ARPU comparison
  - Create expansion opportunity analysis
- **Deliverable:** Product & revenue dashboard pages
- **Owner:** Power BI Developer
- **Duration:** 2 days

#### **Step 4.6: Build Geographic & Risk Dashboards**
- **Participants:** Power BI Developer
- **Activities:**
  - **Geographic Dashboard:**
    - Regional revenue and customer distribution
    - Regional retention and churn rates
    - City-level performance breakdown
    - Geographic performance rankings
  - **Risk & Health Dashboard:**
    - Customer health score distribution (at-risk, stable, healthy)
    - Churn prediction indicators
    - Reactivation opportunities (churned customers)
    - Time-to-reactivation metrics
    - At-risk customer list (drill-down)
- **Deliverable:** Geographic and Risk dashboard pages
- **Owner:** Power BI Developer
- **Duration:** 2 days

#### **Step 4.7: Add Interactivity & Filtering**
- **Participants:** Power BI developer
- **Activities:**
  - Add slicers/filters to all pages:
    - Date range selector
    - Geographic filters (Region, City)
    - Acquisition channel filter
    - Service tier filter
    - Customer size filter
  - Create drill-down capabilities
  - Add bookmarks for filtered views
  - Implement cross-highlighting between visuals
  - Test filter interactions for usability
- **Deliverable:** Interactive dashboard with working filters
- **Owner:** Power BI Developer
- **Duration:** 2 days

#### **Step 4.8: Optimize Performance**
- **Participants:** Power BI developer
- **Activities:**
  - Review query performance on each page
  - Optimize slow measures using CALCULATE, FILTER
  - Implement aggregations for large tables if needed
  - Test with typical user scenarios
  - Monitor refresh times
  - Identify bottlenecks and resolve
  - Document performance metrics
- **Deliverable:** Performance optimization report
- **Owner:** Power BI Developer
- **Duration:** 1 day

---

### **PHASE 5: VALIDATION & TESTING (Days 28-31)**

#### **Step 5.1: Data Accuracy Validation**
- **Participants:** Data analyst, business analyst
- **Activities:**
  - Spot-check metrics against source data
  - Validate sample calculations manually
  - Compare dashboard totals against known values
  - Test edge cases and filters
  - Verify cohort calculations
  - Validate segmentation accuracy
  - Check for data gaps or anomalies
- **Deliverable:** Data validation sign-off report
- **Owner:** Data Analyst
- **Duration:** 1 day

#### **Step 5.2: User Acceptance Testing (UAT)**
- **Participants:** Key stakeholders, end users, business analyst
- **Activities:**
  - Conduct UAT with target user groups:
    - Marketing team tests channel performance views
    - Customer success team tests retention insights
    - Finance team tests revenue metrics
  - Verify dashboard meets requirements
  - Test ease of use and navigation
  - Gather feedback on visualizations and insights
  - Identify any missing or incorrect elements
  - Document issues and requested enhancements
- **Deliverable:** UAT report, feedback summary, issues log
- **Owner:** Business Analyst
- **Duration:** 2 days

#### **Step 5.3: Performance & Load Testing**
- **Participants:** Power BI developer, IT team
- **Activities:**
  - Test dashboard load time with various filters applied
  - Simulate multiple concurrent users
  - Test on different devices (desktop, tablet)
  - Verify performance on slow network connections
  - Check refresh performance for scheduled updates
  - Document performance benchmarks
- **Deliverable:** Performance testing report
- **Owner:** Power BI Developer
- **Duration:** 1 day

#### **Step 5.4: Issues Resolution & Refinement**
- **Participants:** Power BI developer, data analyst
- **Activities:**
  - Address all issues identified in testing
  - Incorporate feedback from UAT
  - Refine visualizations for clarity
  - Optimize any slow-performing elements
  - Conduct re-testing of resolved issues
  - Final sign-off from stakeholders
- **Deliverable:** Updated dashboard, refined design
- **Owner:** Power BI Developer
- **Duration:** 1 day

---

### **PHASE 6: DEPLOYMENT & LAUNCH (Days 32-35)**

#### **Step 6.1: Prepare Deployment Environment**
- **Participants:** IT team, Power BI developer
- **Activities:**
  - Set up Power BI Service workspace (if moving from Desktop)
  - Configure security and access controls
  - Set up data refresh schedule
  - Configure alerts and notifications
  - Document deployment process
  - Prepare rollback procedures
- **Deliverable:** Deployment environment ready, access controls configured
- **Owner:** IT Team / Power BI Developer
- **Duration:** 1 day

#### **Step 6.2: Create User Documentation**
- **Participants:** Business analyst, Power BI developer
- **Activities:**
  - Create user guide with screenshots
  - Document each dashboard's purpose and KPIs
  - Explain filters and how to use them
  - Provide interpretation guide (what metrics mean)
  - Create quick-start guide for new users
  - Document known limitations
  - Prepare FAQ document
- **Deliverable:** User guides, FAQ, interpretation documentation
- **Owner:** Business Analyst
- **Duration:** 1 day

#### **Step 6.3: Conduct User Training**
- **Participants:** All end users, Power BI developer, business analyst
- **Activities:**
  - Conduct training sessions by user group:
    - Executive summary for leadership
    - In-depth training for analysts
    - Quick-start for casual users
  - Demo dashboard functionality
  - Practice with sample queries
  - Q&A session
  - Distribute training materials
- **Deliverable:** Training materials, attendance records
- **Owner:** Business Analyst / Power BI Developer
- **Duration:** 1 day

#### **Step 6.4: Go-Live**
- **Participants:** IT team, project manager
- **Activities:**
  - Publish dashboard to production environment
  - Grant access to user groups
  - Monitor initial usage for issues
  - Verify email notifications working (if configured)
  - Confirm data refresh schedule active
  - Create rollback plan if issues arise
- **Deliverable:** Go-live checklist completed, production dashboard live
- **Owner:** IT Team / Project Manager
- **Duration:** 1 day

#### **Step 6.5: Post-Launch Support**
- **Participants:** Power BI developer, data analyst, support team
- **Activities:**
  - Monitor dashboard usage and performance
  - Address user questions and issues within 24 hours
  - Track usage analytics to identify adoption
  - Collect feedback for future enhancements
  - Document common issues and solutions
  - Provide support for 1 week post-launch
- **Deliverable:** Support ticket log, usage analytics
- **Owner:** Support Team / Power BI Developer
- **Duration:** Ongoing (1 week intensive)

---

### **PHASE 7: INSIGHTS & RECOMMENDATIONS (Days 33-35, parallel with deployment)**

#### **Step 7.1: Deep-Dive Analysis**
- **Participants:** Data analyst, business analyst
- **Activities:**
  - Conduct deeper analysis of data findings
  - Perform cohort comparison and statistical testing
  - Analyze channel ROI in detail
  - Identify key retention drivers
  - Segment customers by profitability and risk
  - Create customer journey flow analysis
  - Document all findings with supporting data
- **Deliverable:** Analysis findings report
- **Owner:** Data Analyst
- **Duration:** 2 days

#### **Step 7.2: Create Executive Recommendations**
- **Participants:** Business analyst, project manager, stakeholder input
- **Activities:**
  - Synthesize findings into strategic recommendations
  - Prioritize recommendations by business impact
  - Develop action plans for top recommendations:
    - Which channels to invest in
    - Which segments to focus retention efforts on
    - Onboarding improvements to implement
    - Product expansion opportunities
  - Estimate financial impact of recommendations
  - Define success metrics for initiatives
- **Deliverable:** Executive recommendations document
- **Owner:** Business Analyst
- **Duration:** 1 day

#### **Step 7.3: Prepare Presentation**
- **Participants:** Business analyst, data analyst
- **Activities:**
  - Create PowerPoint presentation covering:
    - Business context and objectives
    - Key findings with visualizations
    - Segment performance highlights
    - Retention and churn insights
    - Channel effectiveness analysis
    - Strategic recommendations
    - Implementation roadmap
    - Success metrics and next steps
  - Prepare speaker notes
  - Anticipate questions
  - Practice presentation
- **Deliverable:** Executive presentation deck
- **Owner:** Business Analyst
- **Duration:** 1 day

---

### **PHASE 8: ONGOING OPERATIONS (Post-Launch)**

#### **Step 8.1: Scheduled Maintenance**
- **Participants:** Power BI developer, data team
- **Activities:**
  - Monitor dashboard performance regularly
  - Verify data refresh schedules are working
  - Monitor data quality continuously
  - Address performance issues proactively
  - Apply Power BI updates and patches
- **Frequency:** Weekly
- **Owner:** Power BI Developer

#### **Step 8.2: Quarterly Business Review**
- **Participants:** All stakeholders, data analyst
- **Activities:**
  - Review KPI trends against benchmarks
  - Identify new insights and patterns
  - Assess impact of implemented recommendations
  - Plan refinements or new analyses
  - Prepare quarterly update presentation
- **Frequency:** Quarterly
- **Owner:** Business Analyst

#### **Step 8.3: Dashboard Enhancements**
- **Participants:** Power BI developer, business analyst, users
- **Activities:**
  - Implement user-requested features
  - Add new KPIs based on business evolution
  - Optimize underutilized pages
  - Incorporate feedback from usage analytics
  - Keep dashboard aligned with business priorities
- **Frequency:** As needed / Quarterly sprint
- **Owner:** Power BI Developer

---

## **7. KEY DELIVERABLES**

| Deliverable | Description | Owner | Timing |
|---|---|---|---|
| **Project Charter** | Scope, objectives, success criteria | PM | Day 1 |
| **Requirements Document** | Detailed stakeholder requirements and KPIs | BA | Day 3 |
| **Data Validation Report** | Data quality assessment and findings | DA | Day 5 |
| **EDA Report** | Exploratory analysis with statistics | DA | Day 8 |
| **Cohort Analysis** | Baseline metrics by onboarding cohort | DA | Day 10 |
| **Metric Definitions** | Detailed calculation methods for all KPIs | DA | Day 12 |
| **Data Model Diagram** | Star schema design and relationships | Dev | Day 14 |
| **DAX Measures Library** | Complete measure definitions and logic | Dev | Day 16 |
| **Dashboard Wireframes** | Layout and design specifications | Dev | Day 18 |
| **Executive Dashboard** | High-level KPI summary page | Dev | Day 21 |
| **Cohort & Retention Dashboard** | Detailed retention analysis pages | Dev | Day 24 |
| **Channel Performance Dashboard** | Acquisition and channel analysis | Dev | Day 25 |
| **Product & Revenue Dashboard** | Service and revenue analysis | Dev | Day 26 |
| **Geographic & Risk Dashboards** | Geographic and at-risk customer views | Dev | Day 27 |
| **Data Validation Sign-Off** | Accuracy verification completed | DA | Day 29 |
| **UAT Report** | User acceptance testing findings | BA | Day 30 |
| **Performance Report** | Load and performance testing results | Dev | Day 31 |
| **User Documentation** | User guides, FAQ, training materials | BA | Day 34 |
| **Training Records** | Completed user training sign-offs | BA | Day 34 |
| **Analysis Findings Report** | Deep-dive analysis and key insights | DA | Day 35 |
| **Executive Recommendations** | Strategic recommendations with action plans | BA | Day 35 |
| **Executive Presentation** | PowerPoint with findings and recommendations | BA | Day 35 |
| **Go-Live Checklist** | Completed deployment and launch tasks | PM | Day 35 |

---

## **8. TIMELINE & MILESTONES**

### **Project Timeline Overview:**

```
Week 1: Planning & Requirements
  └─ Days 1-5: Project kickoff, stakeholder interviews, data validation

Week 2: Data Exploration & Analysis
  └─ Days 6-12: Data import, EDA, cohort analysis, metric validation

Week 3: Modeling & Dashboard Development
  └─ Days 13-17: Data model, calculations, measures
  └─ Days 18-27: Dashboard design and development

Week 4: Testing & Deployment
  └─ Days 28-31: Validation, UAT, refinement
  └─ Days 32-35: Deployment, training, go-live

Week 5 (Optional): Post-Launch
  └─ Days 36-40: Support, optimization, insights
```

### **Key Milestones:**

| Milestone | Target Date | Criteria for Success |
|-----------|------------|----------------------|
| **Project Kickoff Complete** | Day 1 | Charter signed, team aligned |
| **Requirements Finalized** | Day 5 | All stakeholders approve requirements |
| **Data Analysis Complete** | Day 12 | EDA done, metrics validated |
| **Data Model Ready** | Day 17 | Schema designed, measures created |
| **Dashboard MVP Ready** | Day 24 | Executive and retention dashboards functional |
| **All Dashboards Complete** | Day 27 | All pages built and integrated |
| **UAT Passed** | Day 31 | All major issues resolved, stakeholders approve |
| **Go-Live** | Day 35 | Dashboard deployed, users trained, live |

---

## **9. SUCCESS CRITERIA**

### **Project Success Metrics:**

#### **Delivery Success:**
- ✓ All deliverables completed on time and on budget
- ✓ Dashboard deployed to production successfully
- ✓ Zero critical defects at launch
- ✓ User training completed with >80% attendance

#### **Dashboard Adoption Success:**
- ✓ >70% of target users access dashboard within first month
- ✓ >50% of users access dashboard at least weekly
- ✓ Average session duration >5 minutes (engaged usage)
- ✓ <2% error rate in dashboard operations

#### **Business Metrics Success:**
- ✓ Identify at least 3 high-impact strategic recommendations
- ✓ Achieve >80% accuracy in retention predictions by segment
- ✓ Quantify ROI potential from top 3 recommendations
- ✓ Enable 30%+ faster decision-making vs. manual reporting

#### **Data Quality Success:**
- ✓ <0.1% data discrepancies between dashboard and source
- ✓ All KPI calculations validated and documented
- ✓ Data refresh completes <1 hour daily
- ✓ 99.5% dashboard uptime

#### **User Satisfaction Success:**
- ✓ User satisfaction survey score >4.0/5.0
- ✓ <5 unresolved help requests post-launch
- ✓ Positive feedback in stakeholder interviews
- ✓ Dashboard recommended for expansion to other areas

### **Failure Criteria (Triggers for Re-Assessment):**
- ⚠ Dashboard deployment delayed >1 week beyond schedule
- ⚠ UAT identifies critical data accuracy issues (>0.5% error)
- ⚠ Dashboard load time exceeds 10 seconds with typical filters
- ⚠ User adoption <50% of target group after 2 weeks
- ⚠ Severe functionality gaps vs. approved requirements

---

## **10. POST-LAUNCH SUPPORT**

### **Immediate Support (Days 1-7 Post-Launch):**
- **Support Availability:** 8 AM - 6 PM business hours
- **Response Time:** Critical issues <1 hour, non-critical <4 hours
- **Support Channels:** Email, Slack, in-person
- **Focus:** User questions, troubleshooting, minor fixes

### **Ongoing Support (Week 2 Onwards):**
- **Support Availability:** Weekday business hours
- **Response Time:** Critical issues <4 hours, non-critical <24 hours
- **Support Level:** Transition to IT help desk
- **Focus:** Performance monitoring, updates, enhancements

### **Maintenance Schedule:**
- **Daily:** Monitor dashboard health and data refresh
- **Weekly:** Performance review, issue log review
- **Monthly:** User feedback collection, usage analytics review
- **Quarterly:** Business review, enhancement prioritization

### **Enhancement Requests Process:**
1. Users submit requests via support email/form
2. Business analyst triages and prioritizes
3. Monthly batch of enhancements planned
4. Quarterly release of new features and improvements

### **Escalation Path:**
- Level 1 (Support Team) → Level 2 (Power BI Developer) → Level 3 (Project Manager/Executive)

---

## **11. RISK MANAGEMENT**

### **Identified Risks:**

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|-----------|
| Data quality issues discovered | Medium | High | Conduct thorough EDA, implement validation |
| Scope creep from stakeholders | High | Medium | Firm requirements, change management process |
| Performance issues with large dataset | Medium | High | Early performance testing, optimization plan |
| User adoption slower than expected | Medium | Medium | Extensive training, champion program |
| Schedule delays | Medium | High | Agile approach, buffer time, re-prioritization |
| Stakeholder misalignment | Low | High | Regular communication, steering committee |

---

## **12. LESSONS LEARNED TEMPLATE**

After project completion, capture:
- ✓ What worked well
- ✓ What could be improved
- ✓ Key insights discovered
- ✓ Recommendations for future projects
- ✓ Reusable assets and templates

---

**Document Version:** 1.0 | **Last Updated:** May 2026  
**Project:** NFX Customer Cohort & Retention Analysis | **Status:** Ready for Execution
