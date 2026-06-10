---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/netsuite-overview/"
title: "Oracle NetSuite"
---
# Oracle NetSuite

Foundry supports connecting to Oracle NetSuite with various methods depending on your use case: NetSuite SuiteAnalytics is recommended for extraction of larger volumes of data as it provides better performance and scalability on read operations. SuiteAnalytics requires you to provide Oracle NetSuite's JDBC driver and only supports username/password authentication. Get started with NetSuite SuiteAnalytics. NetSuite SuiteTalk (JDBC) has broad support for many NetSuite entities. However, SuiteTalk (JDCBC) leverages an older SOAP-based ↗ service and may face performance issues with large tables. SuiteTalk (JDBC) only supports token-based authentication (TBA). Get started with NetSuite SuiteTalk (JDBC). NetSuite SuiteQL (JDBC) has support for a smaller range of NetSuite entities but provides much better read performance. SuiteQL (JDBC) only supports token-based authentication. Get started with NetSuite SuiteQL (JDBC).
