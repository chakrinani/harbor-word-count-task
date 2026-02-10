# Harbor Word Count Task

This repository contains a **Harbor task** created as part of the *New Hire Assignment: Create a Harbor Task*.  
The task performs a simple **word count** operation on a given input file and is fully compliant with Harbor’s task creation guidelines.

The task has been validated successfully using both **Oracle** and **NOP** agents.

---

## Task Description

- **Task Name:** word-count  
- **Category:** data-processing  
- **Difficulty:** Easy  

### What the task does
1. Reads an input text file provided inside the container.
2. Counts the number of words in the file.
3. Writes the result to an output file.
4. Validates the output using automated tests.

The task is designed to ensure:
- Correct computation of results.
- No hard-coded outputs.
- Proper isolation between environment, solution, and tests.

---

## Repository Structure

```

harbor_tasks/word-count/
├── task.toml
├── instruction.md
├── environment/
│   ├── Dockerfile
│   └── input.txt
├── solution/
│   └── solve.sh
└── tests/
├── test.sh
└── test_outputs.py

````

### File Details

- **task.toml**  
  Contains task metadata such as difficulty, category, resource limits, and timeouts.

- **instruction.md**  
  Describes the task instructions for the agent, including input and output file paths.

- **environment/Dockerfile**  
  Defines the Docker environment used to run the task.  
  Only required input files are copied into the container, following Harbor restrictions.

- **environment/input.txt**  
  Sample input text file used for the word count operation.

- **solution/solve.sh**  
  Reference solution that reads the input file, computes the word count, and writes the result to the output file.

- **tests/test.sh**  
  Test runner script that sets up the testing environment using `uvx` and executes the tests.

- **tests/test_outputs.py**  
  Python test cases that verify:
  - Output file existence.
  - Correctness of the word count result.

---

## Prerequisites

Ensure the following tools are installed:

- Docker Desktop (with WSL 2 integration enabled on Windows)
- WSL 2 (Ubuntu)
- `uv` (Astral)

Verify installations:
```bash
docker --version
uv --version
````

---

## How to Run the Task

Navigate to the repository root directory and run the following commands.

### Oracle Validation (Expected Result: 1.0)

```bash
uv run harbor run --agent oracle --path harbor_tasks/word-count --job-name oracle-test
```

This confirms that the reference solution produces the correct output.

---

### NOP Validation (Expected Result: 0.0)

```bash
uv run harbor run --agent nop --path harbor_tasks/word-count --job-name nop-test
```

This confirms that the task does not pass without a valid solution.

---

## Validation Results

| Agent  | Result |
| ------ | ------ |
| Oracle | 1.0 ✅  |
| NOP    | 0.0 ✅  |

Both validations passing confirms that the task meets all Harbor requirements.

---

## Compliance Checklist

* Uses absolute paths inside the container (`/app/...`)
* Includes required resource fields (`memory_mb`, `storage_mb`) in `task.toml`
* Dockerfile does not copy `solution/` or `tests/`
* Tests are executed using `uvx`, not `pip`
* Output is computed dynamically (no hard-coded values)
* Oracle and NOP validations pass successfully

---

## Status

✅ **Assignment completed successfully**
The task is fully validated and ready for submission.

```
```
