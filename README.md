# Customer Complaint & Service Performance Analytics

**Tableau | Business Intelligence | Customer Experience Analytics | Independent Portfolio Project**

An interactive Tableau dashboard exploring customer complaint patterns, service responsiveness, priority tags, complaint issues, and geographic distribution. The goal is to translate historical complaint records into questions and recommendations that a customer service or operations team could investigate.

![Dashboard overview](screenshots/dashboard-overview-2.png)

## Business questions

- Which issues generate the most complaints?
- How frequently are complaints recorded as receiving a timely response?
- How many complaints are disputed or tagged high priority?
- How do complaint counts vary across years, locations, products, and submission channels?
- What operational improvements would be worth testing?

## Dataset

- **Source:** Historical customer complaint spreadsheet supplied with this independent project; original publisher and redistribution license not yet verified.
- **Records:** 40,814 (one complaint per row; `Number of Complaints` equals 1 for every record).
- **Fields:** 14, including product, category, issue, consumer dispute status, received/submitted dates, submission channel, tags, timely response flag, state, and company response.
- **Date received:** December 1, 2011 – October 13, 2020.
- **Tools:** Tableau Public Desktop; spreadsheet source.

**Data sharing note:** The `data/` folder is included in the local project package for reproducibility. Before making the GitHub repository public, verify that you have permission to redistribute this dataset. If permission is unclear, remove the spreadsheet and provide an authorized source link instead. Review the customer identifiers and ZIP codes for privacy implications before publication.

## Dashboard components

1. KPI cards: total complaints, timely response rate, consumer dispute rate, and high-priority complaints.
2. Complaint counts by product and product category.
3. Historical complaint volume trend.
4. Geographic complaint map by state.
5. Leading complaint issues.
6. Complaint submission methods.
7. Company response status comparisons.
8. Product category filtering.

## Verified findings

| Metric | Value | Interpretation |
| --- | ---: | --- |
| Total complaints | 40,814 | Total source records |
| Timely responses | 20,382 (49.94%) | `Timely response? = Yes` |
| Not timely | 20,432 (50.06%) | `Timely response? = No` |
| Consumer disputed | 13,380 (32.78%) | `Consumer disputed? = Yes` |
| Consumer dispute pending | 13,707 (33.58%) | Distinct from confirmed disputes |
| High-priority tagged | 10,276 (25.18%) | `Tags = High Priority` |
| Shipping damage | 4,651 (11.40%) | Most frequent issue in the dataset |
| Size mismatch | 4,587 | Second most frequent issue |
| Expired product | 4,575 | Third most frequent issue |

Percentages use 40,814 as the denominator and are rounded. The dataset contains no independent definition of the service deadline, so 'timely' is interpreted strictly as the supplied flag.

### Tableau calculated KPI: high-priority complaints

```tableau
IF [Tags] = "High Priority"
THEN [Number of Complaints]
ELSE 0
END
```

The dashboard displays `SUM([High Priority Complaints])`. This counts complaints **already labeled** high priority in the source; it is not a new risk-scoring model.

## Business interpretation and recommendations

- **Investigate response timeliness:** More than half of the records are flagged not timely. Break down response performance by product, issue, and response status, then review staffing, routing, and escalation practices.
- **Review fulfillment quality:** Shipping damage is the most common recorded issue. Audit packaging, warehouse handling, and carrier-related processes before choosing interventions.
- **Prioritize tagged cases:** Review the 10,276 high-priority cases for recurring issues and opportunities to improve escalation workflows.
- **Monitor channel coverage:** Email, website, and phone complaints are nearly evenly distributed. Ensure service reporting covers all three channels.

These are **proposed investigations**, not documented improvements achieved by a real organization. See [business recommendations](docs/business-recommendations.md).

## Limitations

- Independent portfolio analysis; no company deployment or measured business impact is claimed.
- Complaint volumes are not normalized by orders, customers, or sales; they cannot establish defect rates or customer satisfaction.
- The dataset's original publisher and licensing terms are unverified.
- `Pending` disputes must not be counted as confirmed `Yes` disputes.
- Priority status is an existing data tag, not a predicted severity score.
- Historical complaint trends may reflect reporting coverage or business volume changes.
- Some dashboard views may require resizing or scrolling at smaller screen resolutions.

## Open the project

1. Download `dashboard/customer-complaint-dashboard.twbx`.
2. Open it with Tableau Desktop or Tableau Public Desktop.
3. Navigate to **Customer Complaint Dashboard** and use the category filter to explore the views.
4. If you want to inspect the source, see `data/customer-complaints.xlsx` (subject to the sharing note above).

## Repository layout

```text
customer-complaint-analytics/
├── README.md
├── .gitignore
├── dashboard/
│   └── customer-complaint-dashboard.twbx
├── data/
│   └── customer-complaints.xlsx
├── screenshots/
│   ├── dashboard-overview-1.png
│   ├── dashboard-overview-2.png
│   ├── complaint-breakdown.png
│   └── response-analysis.png
└── docs/
    └── business-recommendations.md
```

## Author

**Namra Ali** — Applied AI & Data Analytics  
[GitHub profile](https://github.com/nali2011)
