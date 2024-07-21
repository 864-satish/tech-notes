# 📖 PostgreSQL Core Concepts

This document provides an in-depth understanding of PostgreSQL's core concepts, including how data is stored, how indexing works, the data structures used, buffer cache, count-and-sweep algorithm, transactions, row locking, and views.

## B+ Tree Working

### What is a B+ Tree?
ref: [Understanding B-Trees: The Data Structure Behind Modern Databases](https://youtu.be/K1a2Bk8NrYQ?si=2R3uPWwRPHG88VNw)

A B+ Tree is a self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and search operations. It is an extension of a B-Tree, where all values are found at the leaf level, and internal nodes only store keys and pointers to child nodes.

### How It Works

1. **Insertion**:
   - Start at the root and find the appropriate leaf node where the value should be inserted.
   - Insert the value into the leaf node. If the leaf node exceeds its capacity, split it and propagate the split upwards.

2. **Deletion**:
   - Find the leaf node containing the value.
   - Remove the value. If the leaf node has fewer entries than the minimum required, merge or redistribute entries to maintain balance.

3. **Search**:
   - Start at the root and traverse down the tree, following the pointers until the leaf node is reached.

## Data Storage in PostgreSQL

PostgreSQL stores data in tablespaces, which are collections of files on disk. Each table and index is stored in a separate file within a tablespace.

### Tablespace
A tablespace in PostgreSQL is a storage location on disk where the data files for database objects are stored. It provides a way to control the physical storage of data and can help manage disk usage and improve performance.

### Creating a Tablespace

You can create a tablespace using the `CREATE TABLESPACE` command. For example:
```sql
CREATE TABLESPACE my_tablespace LOCATION '/path/to/directory';
```

```sql
CREATE TABLE my_table (
    id SERIAL PRIMARY KEY,
    data TEXT
) TABLESPACE my_tablespace;

CREATE INDEX my_index ON my_table (data) TABLESPACE my_tablespace;

```

### Storage Layout

- **Tables**: Data is stored in heap files, which are collections of fixed-size pages (usually 8 KB).
- **Indexes**: Index data is stored in separate files, typically using B+ Tree structures.

## Indexing in PostgreSQL

Indexes are used to speed up data retrieval operations. PostgreSQL supports several types of indexes:

### Types of Indexes

1. **B-Tree Index**: Default index type, suitable for most queries.
2. **Hash Index**: Useful for equality comparisons.
3. **GIN (Generalized Inverted Index)**: Used for indexing composite data types.
4. **GiST (Generalized Search Tree)**: Supports complex queries.
5. **SP-GiST (Space-Partitioned Generalized Search Tree)**: Supports dynamic partitioning.
6. **BRIN (Block Range INdex)**: Efficient for large tables with naturally ordered data.

### Data Structures Used

- **B+ Trees**: Used for B-Tree indexes.
- **Hash Tables**: Used for Hash indexes.
- **Inverted Indexes**: Used for GIN indexes.
- **Custom Trees**: Used for GiST and SP-GiST indexes.

## Buffer Cache & Count-and-Sweep Algorithm

- The buffer cache is a memory area used to store frequently accessed data pages to improve performance. When a page is read from disk, it is stored in the buffer cache. Subsequent reads can then be served from memory, reducing disk I/O.

- The count-and-sweep algorithm is used for memory management, particularly for reclaiming memory used by dead tuples (deleted or updated rows that are no longer visible to any transaction).

### How It Works

1. **Count**: Track the number of references to each tuple.
2. **Sweep**: Periodically scan the table to remove tuples with zero references, freeing up space.

## Transactions in PostgreSQL

Transactions are a fundamental concept in PostgreSQL, ensuring data integrity and consistency.

### Key Concepts

- **ACID Properties**: Transactions guarantee Atomicity, Consistency, Isolation, and Durability.
- **BEGIN, COMMIT, ROLLBACK**: Start a transaction with `BEGIN`, save changes with `COMMIT`, or revert changes with `ROLLBACK`.

## Row Locking

Row locking prevents concurrent transactions from interfering with each other by locking rows that are being modified.

### Types of Row Locks

- **Shared Lock (S)**: Multiple transactions can hold a shared lock on the same row, allowing reads but not writes.
- **Exclusive Lock (X)**: Only one transaction can hold an exclusive lock on a row, preventing other transactions from reading or writing.

## Views in PostgreSQL

Views are virtual tables that provide a way to simplify complex queries.

### Temporary Views

Temporary views exist only for the duration of a session and are automatically dropped when the session ends.

### Materialized Views

Materialized views store the result of a query physically and can be refreshed periodically to reflect changes in the underlying tables.

### Creating Views

- **Temporary View**:
  ```sql
  CREATE TEMP VIEW temp_view AS
  SELECT * FROM employees WHERE department = 'Sales';
  ```

