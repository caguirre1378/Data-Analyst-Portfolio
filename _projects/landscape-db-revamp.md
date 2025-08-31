---
layout: single
title: "Landscape Database Revitalization"
excerpt: "Turn a fragmented landscaping DB into an analytics-ready system."
classes: wide
category: sql
tags: [sql-server, ssms, erdplus, database-design, normalization]
thumbnail: /assets/images/landscape-splash.png
permalink: /projects/landscape-db/
weight: 20
---

> **Goal** — Turn a fragmented landscaping database into a normalized, analytics-ready system.  
> **Stack** — SQL Server, SSMS, ERDPlus.  

---

## Project Overview

This project tackled the restructuring of a fragmented landscaping company’s database, transforming it into a streamlined, normalized system that supports reliable analytics and business decision-making.

Using SQL Server Management Studio, SQL Server, and ERDPlus, the legacy database—originally composed of wide, denormalized tables—was rebuilt into a clean, normalized schema. The process involved resolving redundancies, enforcing constraints, indexing high-traffic paths, and creating over 30 advanced SQL queries to uncover insights such as service popularity, customer trends, and project profitability.

---

## At a glance

- **ER modeling → normalized schema** (3NF) with clearly defined entity boundaries.  
- **Data integrity** via **PRIMARY/FOREIGN KEYS**, **UNIQUE constraints**, and **CHECK rules** for valid values.  
- **Redundancy removed** through normalization; **indexes** added to improve performance.  
- **30+ SQL queries** developed for business insights and strategic reporting.

---

## Technical Specifications

**Software Used:** SQL Server Management Studio, SQL Server, ERDPlus  

**Techniques Applied:**  

### Data Standardization and Normalization
- Converted inconsistent values into standardized formats.
- Designed schema to eliminate redundancy and optimize performance.
- Organized fragmented data into structured, normalized tables.

### Advanced SQL Query Development
- Created 30+ advanced SQL queries using joins, aggregations, subqueries, and window functions.
- Focused on business intelligence: customer behaviors, service use, and profitability.

---

## Design & Schema

### Core Entities
- **Client** — Maintains customer accounts.
- **Project** — Represents a scheduled landscaping job for a client.
- **Service** — Mowing, aeration, sod laying, etc.
- **ProjectService** — Junction table linking services to specific projects.
- **Material** — Mulch, fertilizer, sod.
- **LaborEntry** — Crew labor logs (hours, rates).
- **Supplier** — Vendor providing materials.

### ER Modeling
An entity-relationship model was created in ERDPlus, defining attributes, relationships, and cardinality. The schema was refined to ensure support for analytics and minimize anomalies during inserts and updates.

---

## Example DDL (Schema Excerpt)

```sql
CREATE TABLE dbo.Client (
  ClientID        INT IDENTITY PRIMARY KEY,
  Name            NVARCHAR(120) NOT NULL,
  Phone           NVARCHAR(30)  NULL,
  Email           NVARCHAR(120) NULL,
  CONSTRAINT UQ_Client_Email UNIQUE (Email)
);

CREATE TABLE dbo.Project (
  ProjectID   INT IDENTITY PRIMARY KEY,
  ClientID    INT NOT NULL REFERENCES dbo.Client(ClientID),
  ScheduledOn DATE NOT NULL,
  Status      NVARCHAR(20) NOT NULL CHECK (Status IN ('Scheduled','InProgress','Complete','Canceled')),
  AddressLine NVARCHAR(180) NULL,
  City        NVARCHAR(80)  NULL,
  StateCode   CHAR(2)       NULL,
  Zip         NVARCHAR(10)  NULL,
  CONSTRAINT IX_Project_ScheduledOn  UNIQUE (ProjectID, ScheduledOn)
);

CREATE TABLE dbo.Service (
  ServiceID   INT IDENTITY PRIMARY KEY,
  Name        NVARCHAR(80) NOT NULL,
  BaseRate    DECIMAL(10,2) NOT NULL CHECK (BaseRate >= 0),
  CONSTRAINT UQ_Service_Name UNIQUE (Name)
);

CREATE TABLE dbo.ProjectService (
  ProjectID   INT NOT NULL REFERENCES dbo.Project(ProjectID),
  ServiceID   INT NOT NULL REFERENCES dbo.Service(ServiceID),
  Qty         DECIMAL(10,2) NOT NULL CHECK (Qty > 0),
  UnitPrice   DECIMAL(10,2) NOT NULL CHECK (UnitPrice >= 0),
  CONSTRAINT PK_ProjectService PRIMARY KEY (ProjectID, ServiceID)
);

CREATE TABLE dbo.Material (
  MaterialID  INT IDENTITY PRIMARY KEY,
  Name        NVARCHAR(80) NOT NULL,
  UnitCost    DECIMAL(10,2) NOT NULL CHECK (UnitCost >= 0),
  SupplierID  INT NULL REFERENCES dbo.Supplier(SupplierID),
  CONSTRAINT UQ_Material_Name UNIQUE (Name)
);

CREATE TABLE dbo.LaborEntry (
  LaborEntryID INT IDENTITY PRIMARY KEY,
  ProjectID    INT NOT NULL REFERENCES dbo.Project(ProjectID),
  CrewMember   NVARCHAR(80) NOT NULL,
  Hours        DECIMAL(6,2)  NOT NULL CHECK (Hours > 0),
  HourlyRate   DECIMAL(10,2) NOT NULL CHECK (HourlyRate >= 0)
);

-- Helpful indexes
CREATE INDEX IX_Project_Client         ON dbo.Project (ClientID, ScheduledOn);
CREATE INDEX IX_ProjectService_Service ON dbo.ProjectService (ServiceID);
CREATE INDEX IX_LaborEntry_Project     ON dbo.LaborEntry (ProjectID);
```

---

## Querying and Analysis

Advanced SQL queries were developed for reporting on:
- Most requested services
- Seasonal project distribution
- Material cost trends
- Profitability by project or service
- Labor hours by crew member or job type

These queries allow stakeholders to make informed decisions based on reliable and structured data.

---

## Testing and Debugging

- All queries were tested using dummy and live sample data.
- PK/FK relationships were validated to avoid referential integrity issues.
- Queries were optimized for performance using indexes and query plans.

---

## Usage Instructions

**System Requirements:** SQL Server, SQL Server Management Studio (SSMS)  
**Hardware Requirements:** Standard workstation with sufficient memory and CPU for SQL Server

**Steps:**
1. Import SQL scripts into SSMS.
2. Execute DDL to create schema and tables.
3. Populate tables with test data or migrate real operational data.
4. Run analytical queries for reporting and trend analysis.

---

## Contribution and Licensing

This is an academic project for advanced SQL coursework and database management best practices. Not licensed for commercial use without instructor approval.

---

## Future Enhancements

- Integrate Tableau or Power BI dashboards using the normalized schema.
- Automate ETL pipelines for data refresh.
- Expand query library to include financial projections and customer segmentation.
