# Static Code Analysis — Issue Log

The following issues were identified in the original `recruitment_tracker.py` using Bandit, Pylint, and Flake8. The line numbers refer to the original version of the program.

| Issue | Type | Line(s) | Description | Fix Approach |
|-------|------|---------|-------------|--------------|
| SQL injection risk (B608) | Security — Medium | 8 | SQL query used an f-string to insert user-supplied values directly into the query, creating a potential SQL injection vulnerability. | Replaced string-based query construction with parameterized SQL queries using `?` placeholders. |
| Unsafe use of `eval()` (B307) | Security — Medium | 14 | `eval()` evaluated a string as Python code, potentially allowing arbitrary code execution. | Removed `eval()` and used an explicit salary limit instead of evaluating a string expression. |
| Broad exception handling (B110) | Security / Reliability — Low | 28–29 | A broad `except Exception` block silently ignored errors using `pass`, making failures difficult to detect and debug. | Removed the silent exception handler and added explicit error handling for missing applicants. |
| Missing docstrings | Code Quality | 1, 7, 12, 24, 31, 38, 42 | The module and several functions lacked docstrings explaining their purpose. | Added a module docstring and descriptive docstrings to functions. |
| Non-standard function naming | Code Quality | 7, 24, 31, 38 | Function names such as `addApplicant`, `updateStatus`, `exportReport`, and `countByStatus` did not follow Python's `snake_case` convention. | Renamed functions to `add_applicant`, `update_status`, `export_report`, and `count_by_status`. |
| Unused variable | Code Quality | 15 | The variable `total_seen` was assigned a value but never used. | Removed the unused variable. |
| Long lines | Style | 4, 8, 13, 26, 39 | Several lines exceeded the recommended line-length limit, reducing readability. | Split long statements across multiple lines and formatted SQL queries for readability. |
| Unsafe file-handling pattern | Code Quality | 32–33 | File handling did not use a context manager or specify an encoding. | Used `with open(...)` with explicit UTF-8 encoding and CSV handling. |

## Verification

After applying the fixes, the program was analysed again using Pylint, Bandit, and Flake8.

- **Pylint:** 10.00/10.
- **Bandit:** No issues identified.
- **Flake8:** No violations reported.

The program was also executed to verify that the recruitment demonstration continued to work.
