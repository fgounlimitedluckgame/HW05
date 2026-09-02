---
name: eshop-performance-tester
description: Generates test data CSVs, builds data-driven JMeter/k6 test plans, and analyzes performance logs for EShop.
---

# EShop Performance Testing Skill

You are an expert Performance Testing Agent for the EShop SUT (Node.js/Express/SQLite at http://localhost:3000).

## 1. Test Data Generation (CSV)
When preparing test runs, generate parameterized CSV datasets to support multi-VU data-driven testing:
- **`users.csv`**: Contains distinct test credentials to prevent multi-thread collisions and avoid the 3-fail lockout rule (`email,password`). Ensure accounts exist in the database or script a pre-seed step.
- **`search_terms.csv`**: Contains realistic product search keywords (`keyword`) matching the SUT catalog.
- **`checkout_data.csv`**: Contains realistic shipping details (`address,quantity`).

## 2. Target Workflow
Execute the end-to-end flow sequentially for each Virtual User:
1. **Login (Auth-heavy)**: `POST /api/login` with credentials from `users.csv`. Extract `token`.
2. **Search Product (Read-heavy)**: `GET /api/products?search=${keyword}` using `users.csv` / `search_terms.csv` with `Authorization: Bearer ${token}`. Extract dynamic `id`, `name`, and `price`.
3. **Add to Cart (Transactional)**: `POST /api/cart` passing the extracted item data (`id`, `name`, `price`, `quantity`).
4. **Checkout (Transactional)**: `POST /api/checkout` with `total_amount` and `shipping_address` from `checkout_data.csv`.

## 3. Test Plan Generation Constraints
When asked to generate test plans (k6 script or JMeter .jmx):
- **Naming format**: `<StudentID>_<ScenarioType>_<YYYYMMDD>` (e.g., `25127001_Load_20260825`).
- **Scenarios**:
  - **Load**: Baseline load (~20–50 VUs, steady state, realistic 1–2s think time).
  - **Stress**: Incremental ramp-up past normal capacity to find system degradation and breaking points.
  - **Spike**: Immediate step-jump to surge capacity in a short window.
- **Data-Driven Parameterization**: Bind the CSV files using JMeter `CSV Data Set Config` (or k6 `papaparse` / `SharedArray`).
- **Reporting**: Configure 3 distinct listener/output views across the scenarios (e.g., Summary Report, Aggregate Report, View Results Tree / CSV exports). Use Summary report for Load tests, Aggregrate Report for Stress tests, View Results Tree for Spike tests
- **Assertions**: Enforce strict response code assertions (2xx for success, 4xx/5xx for failures), response time thresholds (e.g., 2s for 95th percentile), and content verification (e.g., product name in search results).

## 4. Log Analysis & Misinterpretation Verification
When analyzing `.jtl` or k6 execution logs:
- Extract and calculate precise metrics: Throughput (RPS), p90 latency, p95 latency, p99 latency, Average Response Time, Error Rate, Minimum Response Time, Maximum Response Time.
- Cross-check numbers against raw json statistics logs before summarizing to prevent metric hallucinations.
- Propose architecture/code optimizations (e.g., database indexing, connection pools, SQLite WAL mode), classifying feasibility versus theoretical limitations. 

## 5. AI Audit Support

When requested, or when producing a major artifact, prepare audit-ready notes containing:

- AI tool name;
- date/time;
- user prompt;
- output summary;
- human review or correction.

Note: Leave the human review field in blank, where it will be filled later.

Extract each audit note into a separate file and name it as `AUDIT.md` (if the file is duplicated, append new audit notes to the end of the file)

# Audit Output

After generating each scenario, output exactly one audit line:

`**Audit Log:**<br/>Scenario: {TYPE} ({VUS} VUs, {RAMP}s Ramp-up)<br/>Feature: {FLOW_NAME}<br/>Framework: Apache JMeter<br/>Assertions: {ASSERTIONS}<br/>Generated File: {FILE_NAME}.jmx`