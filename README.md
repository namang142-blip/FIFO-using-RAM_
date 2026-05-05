# FIFO-using-RAM_
# 📦 Synchronous FIFO (4×4) – Verilog

## 📌 Overview

This project implements a **Synchronous FIFO (First-In-First-Out)** buffer in Verilog.

* **Data Width:** 4-bit
* **Depth:** 4 entries
* **Clock Domain:** Single clock (synchronous)

The FIFO stores data in order and outputs it in the same order.

---

## ⚙️ Design

### 🔹 Components

* **Memory:** `reg [3:0] mem [0:3]`
* **Write Pointer (`wr_ptr`)**
* **Read Pointer (`rd_ptr`)**
* **Control Logic:** write/read enable + status flags

---

### 🔹 Operations

**Write:**

* Condition → `wr_en = 1` and `full = 0`
* Action → store data, increment `wr_ptr`

**Read:**

* Condition → `rd_en = 1` and `empty = 0`
* Action → output data, increment `rd_ptr`

---

### 🔹 Status Flags

* **Empty:**

```verilog
empty = (wr_ptr == rd_ptr);
```

* **Full:**

```verilog
full = ((wr_ptr + 1) == rd_ptr);
```

> One slot is intentionally unused to avoid ambiguity between full and empty


## 📊 Expected Behavior

* Data is read in the same order as written
* No write occurs when FIFO is full
* No read occurs when FIFO is empty
* Pointers wrap around (circular behavior)

---

## 🎯 Key Concepts

* Circular buffer implementation
* Pointer-based memory access
* Full/Empty detection using pointer comparison
* Synchronous design using clock edge

---

## 📌 Conclusion

This project demonstrates a **basic synchronous FIFO design** with correct handling of:

* Data flow
* Pointer logic
* Edge conditions (full/empty)

---
