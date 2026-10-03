# L5 Narrow / L2 General Classification — api-oss-labs
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Experimental Anticloud features: sandboxed testing environment for new capabilities

## L5 Narrow
api-oss-labs specializes in experimental anticloud features: sandboxed testing environment for new capabilities within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-labs is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B is used in api-oss-labs to evaluate experimental features: given an experiment description and results, PAX recommends promote/discard and explains the reasoning.

## AIOSS Audit Relevance
Every experiment event (experiment ID + hypothesis hash + result hash + promote/discard decision) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
NIST SSDF PW.4 (review and test), ISO 27001 A.12.6 (vulnerability management)
