# Evaluating-Network-switch-Scheduling-algorithm

A Python/Jupyter Notebook project that simulates and compares packet scheduling algorithms used in **input-queued crossbar switches**.

This project evaluates how scheduling policies impact:

- Total service time
- Average packet delay
- Throughput
- Queue backlog
- Head-of-Line (HoL) blocking

---

# Algorithms Implemented

## 1. FIFO (First-In First-Out)

Each input port has one queue.

### Characteristics
- Simple and easy to implement
- Only the head packet can be transmitted
- Suffers from **Head-of-Line blocking**

### Observed Performance
- Highest delay
- Lowest throughput

---

## 2. Optimal VOQ (Virtual Output Queuing)

Each input port maintains separate queues for each output port.

### Characteristics
- Eliminates HoL blocking
- Finds maximum matching every slot
- Gives best possible scheduling result

### Observed Performance
- Highest throughput
- Best service efficiency

---

## 3. iSLIP

A practical iterative matching scheduler used in real switches.

### Characteristics
- Request → Grant → Accept phases
- Round-robin fairness using pointers
- Lower complexity than exhaustive optimal matching

### Observed Performance
- Much better than FIFO
- Near-optimal in practice

---

# Project Structure

```text
Evaluating-Network-switch-Scheduling-algorithm/
│── switch_simulation.ipynb
│── Results/
│   ├── switch_simulation_results.png
│   ├── FIFO_Packet_Timeline.png
│   └── iSLIP_Packet_Timeline.png
│── README.md
```

---

# Requirements

Install dependency:

```bash
pip install matplotlib
```

---

# How to Run

## Run in Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
switch_simulation.ipynb
```

Run all cells in order.

---

# Notebook Sections

1. Imports & Setup
2. Packet Class
3. Switch Classes
   - FIFOSwitch
   - OptimalVOQSwitch
   - iSLIPSwitch
4. Packet Loader
5. Simulation Runners
   - FIFO Runner
   - OptimalVOQ Runner
   - iSLIP Runner
7. Visualization Functions
8. Metrics Functions
9. Main Execution

---

# Results Generated

Saved inside:

```text
Results/
```

### Output Files

- `switch_simulation_results.png` → Comparison graphs
- `FIFO_Packet_Timeline.png` → FIFO packet schedule
- `iSLIP_Packet_Timeline.png` → iSLIP packet schedule

---

# Performance Metrics (Actual Output)

| Algorithm   | Average Delay | Throughput (packets/slot) |
|------------|--------------|---------------------------|
| FIFO       | 2.22         | 1.636                     |
| Optimal VOQ| —            | 2.571                     |
| iSLIP      | 1.06         | 2.250                     |

---

# Analysis

## FIFO
- Highest delay due to HoL blocking
- Lowest throughput
- Inefficient under contention

## Optimal VOQ
- Best throughput among all algorithms
- Fully utilizes switch fabric
- Computationally expensive for large systems

## iSLIP
- Delay reduced significantly vs FIFO
- Throughput close to optimal
- Practical and scalable solution

---

# Key Learning Outcomes

- FIFO queues can waste switch capacity
- VOQ removes Head-of-Line blocking
- Maximum matching improves utilization
- iSLIP balances performance and complexity

---

# Technologies Used

- Python
- Jupyter Notebook
- Matplotlib
- deque (queue simulation)

---

# Author

**Deepanshu Sharma**  
IIT Guwahati

---

# License

Educational / Academic Use
