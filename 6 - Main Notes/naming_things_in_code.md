
2026-07-19

Tags: [[Software Engineering (SWE)]]
# Naming Things in Code
This was meant to be a fun note to write, but nonetheless naming is often an afterthought that can build up as technical debt.

**Code**
1. Consistently use your naming convention
2. Typically avoid single letter variables, although I do think there can a case to be made for single character variables in order to show that a variable isn't important.
3. Don't abbreviate variables. Autocomplete allows for easy typing, and the added context is very valuable
4. Avoid spaces and special characters
5. Putting units in functions can avoid ambiguity, for example `sleep(int delay)` vs `sleep(int delaySeconds)` or `sleep(int delayMiliseconds)`. It is also better to use types when possible so that assumptions are even more explicit.
6.  it doesn't help to put words like `Base` in a class name, and if it is particularly hard to name a parent class then the children likely need more specific names
7. `Utils` classes shouldn't exist in your code, if you find yourself making one then you likely need to refactor your code


**Files**
1. Never put spaces in your filename, ideally underscores or camel case. Hyphens `-`, can sometimes be interpreted as subtraction operators but usually are safe
2. Avoid non alphanumeric characters, it can be risky to use these
3. Be descriptively concise, for example `inverntory.csv` and `user_manual.txt` are good
4. letter casing often matters, often `Hello` and `Hello` are different but sometimes they aren't. When in doubt use lowercase only.
5. Dates should *always* be in year-month-day so that sorting happens chronologically, furthermore days and months should be written with a zero (`2026`-`02`-`08`) so that names are even more consistent.
6. Be Consistent

# References
- 