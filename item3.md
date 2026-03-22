**Item 3** in the sources, titled **"Never Expect Python to Detect Errors at Compile Time,"** explains that Python's design prioritizes runtime flexibility over strict compile-time checks. This means that many errors that would be caught by the compilers of other languages will only surface in Python when the specific line of code is executed.

### What the Compiler Does Catch
Before execution, the Python interpreter parses source code into abstract syntax trees and checks for **obvious structural errors**. These typically result in a `SyntaxError`, such as:
*   **Poorly constructed statements:** For example, an `if` statement missing a colon.
*   **Invalid literals:** For example, a poorly formatted imaginary number like `1.3j5`.

### What is Deferred to Runtime
Due to the **highly dynamic nature of Python**, the interpreter cannot definitively know if certain expressions are errors until they are actually evaluated. Problems that are not flagged until execution include:

*   **Unbound Variables:** Using a variable before it has been assigned a value. Because Python allows dynamic assignment to local and global variables, the interpreter cannot assume a reference is "bad" until it attempts to access it.
*   **Math Errors:** Errors like division by zero are only caught at runtime because the meaning of operators (like `/`) can vary based on the specific types and values involved.
*   **Undefined Methods:** Calling a method that does not exist on an object is not statically detected.

### How to Mitigate These Risks
Because the language itself provides minimal protection before execution, the sources recommend several practices to ensure code correctness:

1.  **Use Linters and Static Analysis:** Community tools like **`pylint`** and **`flake8`** can catch many common errors before you run your program.
2.  **Type Checking:** Use the **`typing` built-in module** and static analysis tools to identify potential bugs through type annotations.
3.  **Runtime Assumptions:** Verify your assumptions within the code using **`assert`** or by raising exceptions for missed expectations.
4.  **Automated Testing:** Since errors are encountered at runtime, maintaining a suite of **automated tests** (both unit and integration tests) is essential to verify your code's behavior.

Would you like me to explain Item 4, which discusses why you should write helper functions instead of using complex single-line expressions?