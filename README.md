# Cheat Sheet Repository

This repository contains concise cheat sheets and quick references for programming, operating systems, tools, and more. Use these to quickly look up commands, code patterns, and best practices.

---

## Operating Systems
- [Linux](Linux): Linux commands, scripting, and tips
- [Windows](Windows): Windows commands, PowerShell, and shortcuts

## Programming Languages
- [Cpp](Cpp): C++ syntax, STL, and best practices
- [C](C): C language basics and patterns
- [Python](Python): Python libraries, modules, and tools

## Tools & Frameworks
- [GStreamer](GStreamer): Multimedia framework usage
- [ROS](ROS): Robot Operating System quick reference
- [Makefile](Makefile): Makefile syntax and usage
- [Docker](Docker): Containerization and Docker commands
- [Git](Git): Version control with Git
- [Cloudflare](Cloudflare): DNS, CDN, security and performance optimization

## Databases & Data
- [MySQL](MySQL): MySQL commands and queries
- [Text](Text): Text processing and manipulation
- [Paper](Paper): Paper writing and formatting tips

## System Design & Architecture
- [SystemDesign](SystemDesign): Scalability, reliability, CAP theorem, load balancing, caching, and database design principles

## Algorithms & Data Structures
- [Algorithm](Algorithm): Common algorithms and patterns
- [Data Structure](DataStructures): Data structure usage and examples

## System Design Study Plan
| 週次       | 主題                                       | 核心關鍵詞                                                             | 重點問題                  |
| -------- | ---------------------------------------- | ----------------------------------------------------------------- | --------------------- |
| Week 1   | [**Scalability & Load Balancer** ](./SystemDesign/Scaling_And_LR.md)         | Vertical / Horizontal Scaling, Auto Scaling, Round Robin, IP Hash | 如何應對高併發？如何分散負載？       |
| Week 2   | [**Cache 設計與策略** ](./SystemDesign/Cache.md)                         | Read-Through, Write-Through, TTL, LRU, Redis                      | 如何用 Cache 提高效能又保持一致性？ |
| Week 3   | **Database 選型與 Sharding**                | SQL vs NoSQL, Sharding, Replication, CAP                          | 什麼情況選 MySQL？什麼情況拆 DB？ |
| Week 4   | **Data Consistency & Message Queue**     | Eventual Consistency, Kafka, RabbitMQ, Idempotency Key            | 系統怎麼確保資料一致？怎麼防重複？     |
| Week 5   | **Rate Limiting & Circuit Breaker**      | Token Bucket, Leaky Bucket, Retry, Backoff, Hystrix               | 如何保護系統不被濫用或雪崩？        |
| Week 6   | **CDN & Global System Design**           | Cloudflare, Geo DNS, Edge Cache                                   | 如何設計給全球用戶？如何用 CDN 加速？ |
| Week 7   | **Monitoring & Reliability**             | SLA, SLO, SLI, Prometheus, Grafana, Healthcheck                   | 如何設計一個穩定且可觀察的系統？      |
| Week 8   | **Design Real Systems & Interview Case** | Design YouTube, Messenger, TinyURL, LLM Infra                     | 如何答出一個完整的系統設計題？       |

---

Browse each section for quick code examples, explanations, and best practices.
