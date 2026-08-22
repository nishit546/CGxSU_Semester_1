# Partitioning and Sharding in DBMS

## 1. Why Database Optimization?

When data and traffic increase, a single database server can become overloaded.

```text
Users
  ↓
Application
  ↓
Single Database
  ↓
High Load → Slow Response / Crash
```

Common solutions:

- Scale-Up
- Replication
- Partitioning
- Sharding

---

## 2. Scale-Up (Vertical Scaling)

Increase the hardware capacity of the same server.

```text
Before → 4 CPU, 16 GB RAM
After  → 16 CPU, 64 GB RAM
```

### Advantages

- Simple
- No major application changes

### Disadvantages

- Expensive
- Hardware has limits
- Single point of failure

---

## 3. Replication

Create copies of a database to distribute read operations.

```text
             Application
                  |
          ┌───────┴───────┐
          ↓               ↓
       Primary         Replicas
       (Writes)         (Reads)
```

### Problem

Replicas may temporarily contain old data due to **replication lag**.

---

## 4. Partitioning

Divide a large dataset into smaller parts called **partitions**.

```text
Database
   |
   ├── Partition 1
   ├── Partition 2
   └── Partition 3
```

### Horizontal Partitioning

Divides **rows**.

```text
Partition 1 → Rows 1-1000
Partition 2 → Rows 1001-2000
```

### Vertical Partitioning

Divides **columns**.

```text
Table 1 → ID, Name, Age
Table 2 → ID, Address, Phone
```

### Common Types

- Range
- List
- Hash
- Composite

---

## 5. Partition Pruning

The database avoids partitions that cannot contain the required data.

```text
Orders
├── 2024
├── 2025
└── 2026 ← Query needs this
```

This can reduce the amount of data scanned.

---

## 6. Sharding

Sharding distributes data across multiple database servers called **shards**.

```text
              Application
                   |
             Routing Layer
                   |
        ┌──────────┼──────────┐
        ↓          ↓          ↓
     Shard 1    Shard 2    Shard 3
```

The **routing layer** determines which shard contains the required data.

---

## 7. Shard Key

A shard key determines where data is stored.

Example:

```text
user_id
   ↓
Routing Logic
   ↓
Shard Selection
```

A good shard key should distribute data and traffic evenly.

A poor shard key can create a **hotspot**:

```text
Shard 1 → 80M users
Shard 2 → 10M users
Shard 3 → 10M users
```

---

## 8. Partitioning vs Sharding

| Feature | Partitioning | Sharding |
|---|---|---|
| Purpose | Divide data | Distribute data |
| Nodes | May use one or multiple | Multiple nodes |
| Routing | Not necessarily required | Required |
| Main goal | Data management/performance | Horizontal scalability |
| Complexity | Lower | Higher |

### Easy Difference

```text
Partitioning
    ↓
Divide Data

Sharding
    ↓
Divide Data
    ↓
Distribute Across Multiple Servers
    ↓
Route Requests to Correct Server
```

---

## 9. Scale-Up vs Replication vs Partitioning vs Sharding

| Technique | Main Idea |
|---|---|
| Scale-Up | Make one server stronger |
| Replication | Create database copies |
| Partitioning | Divide large datasets |
| Sharding | Distribute data across servers |

---

## 10. Key Takeaways

1. **Scale-Up** → Increase server hardware.
2. **Replication** → Create database copies.
3. **Partitioning** → Divide large datasets.
4. **Horizontal partitioning** → Divide rows.
5. **Vertical partitioning** → Divide columns.
6. **Sharding** → Distribute data across multiple servers.
7. **Routing layer** → Finds the correct shard.
8. **Shard key** → Determines data placement.
9. Poor shard keys can create **hotspots**.
10. Partitioning and sharding can be used together.
