[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574103&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** email@example.com
**Name:** (Dien ten cua ban)

---

## Mo ta

Bai lab nay xay dung mot ETL (Extract - Transform - Load) Pipeline tu dong de xu ly du lieu san pham tu file JSON. Pipeline thuc hien cac buoc: doc du lieu, validate du lieu khong hop le (gia am, category rong), chuan hoa du lieu (Title Case, giam gia 10%), va luu ket qua ra file CSV. Ngoai ra, thi nghiem Stress Test so sanh chat luong phan hoi cua AI Agent khi dung du lieu sach va du lieu "rac".

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Buoc 1: Tao garbage data
python generate_garbage.py

# Buoc 2: Chay ETL pipeline de tao processed_data.csv
python solution.py

# Buoc 3: Chay Agent simulation so sanh Clean vs Garbage
python agent_simulation.py
```

### Chay Tests
```bash
pytest tests/
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script chinh
├── agent_simulation.py      # Gia lap AI Agent de stress test
├── generate_garbage.py      # Tao du lieu "rac" de thi nghiem
├── raw_data.json            # Du lieu dau vao (5 san pham)
├── processed_data.csv       # Output cua pipeline (sau khi chay solution.py)
├── experiment_report.md     # Bao cao thi nghiem Stress Test
├── tests/
│   └── test_autograder.py   # Bo test tu dong cua GitHub Classroom
└── README.md                # File nay
```

---

## Ket qua

- **Tong records dau vao:** 5
- **Records hop le (processed):** 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped):** 2
  - id=3 "Mystery Box": price = -10 (gia am, khong hop le)
  - id=4 "Phone": category rong (khong co danh muc)
- **Cot them vao:** `discounted_price` (giam 10%), `processed_at` (timestamp)
