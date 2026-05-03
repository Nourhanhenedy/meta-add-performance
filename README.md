# 📊 Meta Ad Performance Analysis Dashboard

> An interactive Power BI dashboard analyzing Facebook and Instagram ad performance across impressions, clicks, purchases, engagement, demographics, and geography.


<img width="1338" height="755" alt="Meta Ad Performance Analysis 4_19_2026 7_46_41 PM" src="https://github.com/user-attachments/assets/d9f16e89-b5de-4035-9143-2a9eaa4f0423" />


---

## 🧠 Project Overview

This project analyzes Meta advertising data (Facebook & Instagram) to uncover performance patterns across platforms, demographics, geographies, and time. The dashboard enables marketers and analysts to make data-driven decisions on budget allocation, audience targeting, and campaign timing.

---

## 📌 Key Metrics

| Metric | Value |
|---|---|
| Total Impressions | 216.0K |
| Total Clicks | 25K |
| Total Purchases | 1K |
| Total Engagements | 29K |
| Comments | 3K |
| Shares | 1K |
| CTR | 11.76% |
| Engagement Rate | 13.56% |
| Conversion Rate | 5.21% |
| Purchase Rate | 0.61% |
| Total Budget | $2.54M |
| Avg. Budget per Ad | $50.72K |

---

## 📂 Dashboard Pages & Visuals

### 🔹 KPI Cards Row
Top-level performance summary showing Impressions, Clicks, Comments, Purchases, Shares, and Engagements at a glance.

### 🔹 Purchases by User Age
Histogram showing purchase volume distribution across age groups (18–50+). Peak purchasing age group: **25–35**.

### 🔹 Purchases by Gender
Donut chart showing gender split:
- Female: **572** purchases (67%)
- Male: **279** purchases (33%)

### 🔹 Purchases by Geography (Map)
Bubble map showing purchase concentration by country across North America, Europe, South America, and Africa.

### 🔹 Purchases by Week Number
Stacked bar chart showing weekly purchase trends across Facebook and Instagram, broken down by campaign name.

### 🔹 Purchases by Day (Matrix)
Matrix table showing purchases by week number and day of week — helps identify the best days to run campaigns.

### 🔹 Hourly Trend Line
Line chart showing purchase activity by hour of day — identifies peak engagement windows.

---

## 🎛️ Filters & Slicers

| Slicer | Options |
|---|---|
| Platform | Facebook / Instagram |
| Select Dynamic Measure | Purchases, Clicks, Impressions, Engagements, etc. |
| Campaign Name | All / Individual campaigns |
| Month | All / Specific month |

The **Dynamic Measure** slicer allows the user to switch all visuals between different KPIs without changing the page — built using a disconnected table and DAX `SWITCH` logic.

---

## ⚙️ DAX Measures Used

```dax
-- Dynamic measure selection
Selected_Measure =
SWITCH(
    SELECTEDVALUE(MeasureTable[Measure]),
    "Purchases", SUM(Ads[Purchases]),
    "Clicks", SUM(Ads[Clicks]),
    "Impressions", SUM(Ads[Impressions]),
    "Engagements", SUM(Ads[Engagements]),
    SUM(Ads[Purchases])
)

-- CTR
CTR = DIVIDE(SUM(Ads[Clicks]), SUM(Ads[Impressions]), 0) * 100

-- Engagement Rate
Engagement_Rate = DIVIDE(SUM(Ads[Engagements]), SUM(Ads[Impressions]), 0) * 100

-- Conversion Rate
Conversion_Rate = DIVIDE(SUM(Ads[Purchases]), SUM(Ads[Clicks]), 0) * 100

-- Purchase Rate
Purchase_Rate = DIVIDE(SUM(Ads[Purchases]), SUM(Ads[Impressions]), 0) * 100

-- Avg Budget per Ad
Avg_Budget_Per_Ad = DIVIDE(SUM(Ads[Total_Budget]), COUNTROWS(Ads), 0)
```

---

## 🗂️ Data Source

| Field | Description |
|---|---|
| Platform | Facebook or Instagram |
| Campaign Name | Name of the individual ad campaign |
| Age | Target audience age group |
| Gender | Target audience gender |
| Country | Country where ad was served |
| Impressions | Number of times ad was shown |
| Clicks | Number of clicks on the ad |
| Purchases | Number of purchases resulting from the ad |
| Engagements | Total engagement actions |
| Comments | Comment count |
| Shares | Share count |
| Total Budget | Campaign budget in USD |
| Event Hour | Hour of day the event occurred |
| Week Number | ISO week number |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Power BI Desktop | Dashboard development |
| DAX | Measures, KPIs, Dynamic selection |
| Power Query | Data cleaning and transformation |
| Bing Maps | Geographic visualization |

---

## 💡 Key Insights

1. **Female audience drives 67% of purchases** — campaigns should be weighted toward female targeting for conversion optimization
2. **Peak purchase age is 25–35** — ad creative and messaging should be tailored to this demographic
3. **CTR of 11.76% is strong** — above industry average, indicating good ad relevance
4. **Conversion Rate of 5.21%** — healthy rate; focus on reducing drop-off between click and purchase
5. **Purchase Rate of 0.61%** — opportunity to improve landing page and checkout experience to increase this
6. **Weekly patterns show clear peak weeks** — budget should be front-loaded in high-performing weeks

---

## 📁 Repository Structure

```
📦 Meta-Ad-Performance-Dashboard
 ┣ 📊 Meta_Ad_Performance.pbix       # Power BI file
 ┣ 📸 Meta_Ad_Performance_Analysis.png  # Dashboard screenshot
 ┣ 📄 README.md                      # This file
 ┗ 📂 data/
    ┗ 📄 meta_ads_data.csv           # Source dataset
```

---

## 🚀 How to Use

1. Clone this repository
```bash
git clone https://github.com/Nourhanhenedy/meta-ad-performance-dashboard.git
```

2. Open `Meta_Ad_Performance.pbix` in **Power BI Desktop**

3. If prompted, update the data source path to point to `data/meta_ads_data.csv`

4. Use the slicers to filter by **Platform**, **Campaign**, **Month**, and **Dynamic Measure**

---

