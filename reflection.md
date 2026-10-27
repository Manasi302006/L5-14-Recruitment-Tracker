# Lab 5: Static Code Analysis — Reflection

## 1. What did you learn from this lab?

I learned how static code analysis tools can identify problems in a Python program without requiring manual inspection of every line. Pylint helped me identify code-quality and naming issues, Flake8 highlighted formatting violations, and Bandit detected potentially unsafe coding practices. I also learned that code can run successfully while still containing security vulnerabilities and maintainability problems.

## 2. What was the most important issue you found, and why?

One of the most important issues was the use of dynamically constructed SQL queries. Building SQL statements using formatted strings can expose an application to SQL injection. Parameterized queries help prevent this by keeping user-provided values separate from SQL commands. I also learned that unsafe functions such as `eval()` can introduce security risks when input is treated as executable code.

## 3. How did you verify that your fixes worked?

I reran Pylint, Bandit, and Flake8 after modifying the program. The final Pylint score was 10.00/10, Bandit reported no identified issues, and Flake8 produced no violations. I also executed the Python program to confirm that its demonstration still worked after the changes. These checks helped me verify both code quality and basic functionality.

## 4. What did you learn about writing secure and maintainable code?

I learned that secure and maintainable code requires more than making a program run correctly. Developers should use parameterized database queries, avoid unsafe evaluation, handle exceptions appropriately, follow consistent naming and formatting conventions, and document functions clearly. Static analysis tools are useful throughout development because they help detect problems early and encourage better coding practices.
