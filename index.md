---
slug: github-supreme-court-meta-relationships
title: Java Workflow for Creating Neo4j Relationships from PostgreSQL Nodes
repo: justin-napolitano/supreme-court-meta-relationships
githubUrl: https://github.com/justin-napolitano/supreme-court-meta-relationships
generatedAt: '2025-11-23T09:42:06.710583Z'
source: github-auto
summary: >-
  Demonstrates automated creation of node relationships in Neo4j using Java after migrating data
  from PostgreSQL tables.
tags:
  - java
  - neo4j
  - postgresql
  - data-migration
  - graph-database
seoPrimaryKeyword: neo4j relationships
seoSecondaryKeywords:
  - java neo4j
  - postgresql to neo4j
  - graph data workflow
seoOptimized: true
---

# Postgres to Neo4j Workflow: Relationships

This project addresses the challenge of establishing meaningful relationships between nodes in a Neo4j graph database after data migration from PostgreSQL. While the initial data export populates nodes, the relationships that define the graph's structure require explicit creation.

## Motivation

Graph databases like Neo4j depend heavily on relationships to provide context and enable complex queries. When transferring data from relational databases such as PostgreSQL, it is common to export tables as nodes but omit or delay relationship creation. This project fills that gap by programmatically creating relationships based on metadata.

## Problem Statement

The previous workflow exported data from PostgreSQL to Neo4j nodes using Java but lacked automated creation of relationships between those nodes. Without relationships, the graph's utility is limited, reducing the ability to analyze connections and patterns.

## Solution Overview

The `RelationshipCreator` Java class encapsulates the logic to create relationships between various node types, such as CallNumber, Resource, Contributor, and Subject, to Item nodes. It uses the Neo4j Java Driver to open a session and execute write transactions for relationship creation.

## Implementation Details

- **Neo4j Session Management:** The class obtains a session through a `Neo4jConnection` utility (assumed to handle driver lifecycle and configuration).

- **Transaction Work:** Each relationship type has a dedicated method that executes Cypher queries within a transaction, ensuring atomicity.

- **Logging:** SLF4J is used for logging the start, completion, and any errors during the relationship creation process, aiding in debugging and monitoring.

- **Extensibility:** The design allows adding more relationship creation methods as needed, supporting scalability.

## Practical Considerations

- The Neo4j connection details must be correctly configured before running the workflow.

- The data model in Neo4j should align with the expected node labels and properties referenced in the Cypher queries.

- Error handling is centralized to catch exceptions during the session lifecycle and transaction execution.

- The workflow assumes prior successful data export from PostgreSQL to Neo4j nodes.

## Conclusion

This project provides a focused, practical solution to a common problem in graph data workflows: establishing relationships post-node creation. It leverages Java and Neo4j's capabilities to automate relationship creation, enhancing the graph's semantic richness and query potential.

For full context and data export steps, refer to the companion repository: https://github.com/justin-napolitano/supreme-court-transfer

