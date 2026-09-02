# HW05

# 1. Test summary report

| Scenario | Samples | Duration quan sát | Throughput | Error rate | Average | Median | p90 | p95 | p99 | Min | Max |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Load | 3,098 | 118.68s s | 26.1 req/s | 0.000% | 8.38 ms | 5 ms | 23 ms | 25 ms | 28 ms | 0 ms | 153 ms |
| Stress | 8,101 | 119.28s | 67.92 req/s | 0.000% | 6.15 ms | 4 ms | 15 ms | 21 ms | 26 ms | 0 ms | 42 ms |
| Spike | 11,624 | 59.48 s | 195.44 req/s | 0.000% | 4.46 ms | 9 ms | 12 ms | 22 ms | 18 ms | 0 ms | 41 ms |
| Endurance | 15,455 | 599.19 s | 25.79 req/s | 0.000% | 8.05 ms | 5 ms | 23 ms | 24 ms | 26 ms | 0 ms | 44 ms |

* Tổng số scenario đã chạy: 38,278
* Các endpoint đã phủ: `POST /api/login`, `GET /api/products?search=...`, `POST /api/cart`, `POST /api/checkout`
* Ngưỡng chịu đưng: 25.79 req/s. Tại đây, `error rate` = 0% và `p99` = 26ms
* Số lượng bug/performance issue phát hiện: 0

# 2. Bảng đánh giá
| **No.** | **Criteria** | **Grade** | **Self-Assessed Grade** |
| --- | --- | --- | --- |
| **1** | Task 1 — Load testing | 30 | 30 |
| **2** | Task 1 — Stress testing | 20 | 20 |
| **3** | Task 1 — Spike testing | 20 | 20 |
| **4** | Task 2 — AI analysis + misinterpretation hunt (with correct values from raw logs) | 10 | 10 |
| **5** | Task 3 — Continuous Performance Testing proposal (G9.6) | 10 | 10 |
| **6** | Agent Skills | 10 | 10 |
|  | **Total** | **100** | 100 |

# 3. Demo video
* Demo performance testing: https://youtu.be/AUix8f-l1Ds
* Demo AI agent: https://youtu.be/9xftUUJMjIw
