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

## At a glance
- **ER modeling → normalized schema** (3NF) with clear entity boundaries.  
- **Integrity** via **PK/FK** and **UNIQUE** constraints; **CHECK** rules for valid ranges.  
- **Redundancy removed**; **indexes** added for high-traffic joins and filters.  
- **30+ queries** for service popularity, customer trends, job profitability, seasonality.

---

## Project overview
A legacy DB mixed customers, jobs, materials, labor, and services in a few wide tables, making reporting unreliable.  
I re-modeled the domain, implemented a normalized schema in **SQL Server**, migrated/standardized data, and produced a query pack that the business can use for routine reporting and ad-hoc analysis.

---

## Design & schema

### Core entities
- **Client** (accounts)  
- **Project** (a scheduled job for a client)  
- **Service** (mowing, mulch install, aeration, etc.)  
- **ProjectService** (junction: which services a project included)  
- **Material** (mulch, sod, fertilizer)  
- **LaborEntry** (crew time logs)  
- **Supplier** (for materials)

### Example DDL (excerpt)
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
CREATE INDEX IX_Project_Client           ON dbo.Project (ClientID, ScheduledOn);
CREATE INDEX IX_ProjectService_Service   ON dbo.ProjectService (ServiceID);
CREATE INDEX IX_LaborEntry_Project       ON dbo.LaborEntry (ProjectID);
