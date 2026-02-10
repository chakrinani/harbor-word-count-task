# Harbor Word Count Task

This repository contains a Harbor **data-processing task** created as part of the **New Hire Assignment: Create a Harbor Task**.

The task reads a text file, counts the number of words, and writes the result to an output file.  
It has been validated using both **Oracle** and **NOP** agents with correct results.

---

## System Requirements

- Windows 10 / 11  
- Docker Desktop installed  
  - WSL 2 engine enabled  
  - Ubuntu enabled in Docker Desktop → WSL Integration  
- WSL 2 (Ubuntu)  
- Git installed  

Before starting, make sure **Docker Desktop is running** and shows **Engine running**.

---

## Step 1: Clone the Repository

Open **Windows PowerShell** and run:

```bash
git clone https://github.com/chakrinani/harbor-word-count-task.git
cd harbor-word-count-task
````

If the folder already exists, just enter it:

```bash
cd harbor-word-count-task
```

---

## Step 2: Enter Ubuntu (WSL)

From PowerShell, start Ubuntu:

```bash
wsl -d Ubuntu
```

Move to the project directory inside WSL:

```bash
cd /mnt/c/Users/HP/harbor-word-count-task
```

---

## Step 3: Verify Project Structure

Run:

```bash
ls
```

Expected output:

```text
README.md
harbor_tasks
jobs
screenshots
```

---

## Step 4: Fix Execution Permissions (One Time)

Run the following commands once:

```bash
chmod +x harbor_tasks/word-count/solution/solve.sh
chmod +x harbor_tasks/word-count/tests/test.sh
```

---

## Step 5: Verify Docker Inside WSL

Run:

```bash
docker --version
```

Docker version should be printed without any error.

---

## Step 6: Run Oracle Validation

Run the Oracle agent:

```bash
uv run harbor run \
  --agent oracle \
  --path harbor_tasks/word-count \
  --job-name oracle-test
```

### Expected Output (Key Results)

* Trials: 1
* Errors: 0
* Mean score: **1.000**

---

## Step 7: Run NOP Validation

Run the NOP agent:

```bash
uv run harbor run \
  --agent nop \
  --path harbor_tasks/word-count \
  --job-name nop-test
```

### Expected Output (Key Results)

* Trials: 1
* Errors: 0
* Mean score: **0.000**

---

## Validation Summary

| Agent  | Score |
| ------ | ----- |
| Oracle | 1.0   |
| NOP    | 0.0   |

These results confirm:

* The task is implemented correctly
* The solution is not hard-coded
* The task follows Harbor guidelines

---


