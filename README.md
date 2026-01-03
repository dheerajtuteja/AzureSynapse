# Dedicated SQL Pool Architechture
![Dedicated SQL Pool](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/media/massively-parallel-processing-mpp-architecture/massively-parallel-processing-mpp-architecture.png)

# Sharing Pattern in Dedicated SQL Pool Architechture
## Hash - Used for Fact Table
## Round Robin - Used for Staging Tables
## Replicate - Used for Small Dimensions Tables

# Hash Block Diagram
![Hash](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/media/massively-parallel-processing-mpp-architecture/hash-distributed-table.png)

```
Sample Code:
CREATE TABLE [dbo].[FactInternetSales]
(   [ProductKey]            int          NOT NULL
,   [OrderDateKey]          int          NOT NULL
,   [CustomerKey]           int          NOT NULL
,   [PromotionKey]          int          NOT NULL
,   [SalesOrderNumber]      nvarchar(20) NOT NULL
,   [OrderQuantity]         smallint     NOT NULL
,   [UnitPrice]             money        NOT NULL
,   [SalesAmount]           money        NOT NULL
)
WITH
(   CLUSTERED COLUMNSTORE INDEX
,  DISTRIBUTION = HASH([ProductKey])
);

```

# Round Robin Block Diagram
![Round Robin](https://github.com/user-attachments/assets/a3284409-f8c3-4b6f-b1bb-993a425359cc)

# Replicate Block Diagram
![Replicate](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/media/massively-parallel-processing-mpp-architecture/replicated-table.png)

