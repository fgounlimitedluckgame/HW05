# AI Audit Log

# Interaction 1
* AI Tool Name: Antigravity SUT Performance Testing Agent (Gemini 3.5 Flash)
* Date & Time: 4:23 PM, 8/26/2026
* User Prompt:
Generate parameterized JMeter scripts for the workflow: Login -> Search -> Add to Cart -> Checkout following the naming convention for the three following scenarios: Load, Spike, Stress. Student ID: 23127108.

## Output Summary:
* Generated JMX templates programmatically through the workspace file generate_jmx.js.
* Generated and seeded the database with 200 distinct performance users.
* Created users.csv, search_terms.csv, and checkout_data.csv.
* Structured Load, Stress, and Spike configurations adhering to the required thread settings, think times, assertions, and target report listener views.
* Human Review / Correction: Đã sửa lại JMX template của summary view, thông số test, cấu hình API và response assertion bị sai. Ngoài ra, đã sửa lại data trong csv nhằm đơn giản hoá quá trình làm

# Interaction 2
- AI Tool: Antigravity IDE (Gemini 3.5 Flash)
- Date & Time: 2026-08-27 00:01 AM
- User Prompt: Request to analyze EShop performance metrics from raw CSV and JSON logs, assess bottlenecks, and propose feasible database optimizations.
- Actions & Outputs:
    - Scanned results/ folder containing Load, Stress, Spike, and Endurance logs.
    - Wrote a Node.js script to extract and calculate: Throughput, p90/p95/p99 latency, Average, Min/Max latency, and Error Rate.
    - Verified calculated CSV numbers against raw JSON statistics files (0.00% error rate detected across all tests).
    - Scanned SUT backend files (`database.js` and `server.js`) to identify missing indexes on `users(email)` and `orders(user_id)`.
    Documented results and analyzed feasibility of SQLite WAL mode vs. connection pools in the artifact
- Human Review / Correction: Đã đính chính lại các đánh giá của AI về hệ thống dựa trên số liệu nhân được và các đề xuất cải thiện hiệu năng (note: trong phần misinterpretation không tính phần connection pool ở phần cải thiện hiệu năng do AI đã tự nhận định giới hạn trong đề xuất này)

# Interaction 3
- AI Tool: GitHub Copilot
- Date & Time: 2026-08-27 11:52 PM
- User prompt: According to the homework requirements, generate a flow chart of the continuous performance testing implementation
- Output: The mermaid flow chart
- Human review: Đã thay đổi các bước sau:
    - `Run unit and API smoke checks` -> `Allow merge`
    - `Block or require approval and create issue` -> `Update threshold or baseline metrics`