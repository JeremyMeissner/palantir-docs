---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isValidIpV4V1/"
parquet_url: "/foundry/pb-functions-expression/isValidIpV4V1/"
title: "Is valid IPv4"
fetched_at: "2026-05-12T19:34:36.740Z"
---
Is valid IPv4. Supported in: Batch. Returns true if the input is a valid IPv4 address. Expression categories: Cyber. Declared arguments. Expression: IP address to check. Expression<String> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: ip. ipOutput 192.168.1.1. true. 10.0.0.1. true. 172.16.0.1. true. 255.255.255.255. true. 0.0.0.0. true. 127.0.0.1. true. 1.2.3.4. true. 256.1.1.1. false. 192.168.1.256. false. 192.168.1. false. 192.168.1.1.1. false. abc.def.ghi.jkl. false. 192.168.1.a. false. -1.2.3.4. false. empty string. false. false. 192.168.1.0/24. false. 10.0.0.0/8. false. 192. false. a.b.c.d/255.0.0.0. false. ::1. false. 2001:db8::1. false. null. false.
