# Product Requirements Document: Trade Aggregator

## 1. Problem & Context
**Why are we building this?**
Small traders execute many transactions across multiple brokerage accounts. Each brokerage provides transaction data in entirely different formats. Manually consolidating, formatting, and de-duplicating this data on a weekly or daily basis is massive toil and prone to errors. 

**Why now?**
The trader needs a reliable, unified view of their positions and PnL to make informed daily trading decisions without spending hours on repetitive data entry.

## 2. Target Audience
Small, independent traders dealing with commodities and other assets across multiple disconnected brokerage platforms.

## 3. Scope & Key Features
- **File Upload:** Ability to upload multiple Excel/CSV files from different brokerages simultaneously via a modern web interface.
- **Data Normalization:** Map differing brokerage export formats into a single, unified database schema.
- **Deduplication:** Automatically identify and ignore duplicate transactions upon upload, strictly using `Transaction ID` and `Date`.
- **Dashboard View:** A clean, modern, and user-friendly data grid displaying the consolidated report, featuring a fresh color scheme, icons, and illustrations for an engaging UX.
- **Local Storage:** Use a local SQLite database for data privacy, persistence, and fast retrieval.

### Core Output Dataset
The output dashboard must contain the following standard columns:
1. Account name / Number
2. Transaction Date
3. Commodity Name / Ticker
4. Quantity
5. Position details
6. Expiry date
7. Purchase price
8. Sold price
9. Total (Sold - Purchase)
10. Status

## 4. Technical Stack
- **Backend:** Python (FastAPI/Flask + `pandas` for robust Excel/CSV parsing).
- **Database:** Local SQLite.
- **Frontend:** React (incorporating a modern UI framework like Tailwind CSS, with clear typography and fresh UI elements).

## 5. Success Criteria
- **Time Saved:** Trader can generate the final consolidated report in merely seconds.
- **Accuracy:** Zero duplicate transactions in the system on repeated uploads of the same overlapping date ranges.
- **Usability:** High-quality, aesthetic frontend that seamlessly handles the data upload flow and visualizes the structured table format beautifully.

## 6. Out of Scope (for v1)
- Direct OAuth / API integrations with brokers (relying strictly on file uploads to start).
- Real-time market data fetching for live PnL.
