# Addition (100 points)
## Writeup Author - slzzpp

---
### Task
My little brother is learning math, can you show him how to do some addition problems?

Attached files: [server.py](assets/addition/server.py)

---
### Solution
In order to solve this simple task, you need to figure out how the `for` loop works in Python with a negative range:
- In Python, the `range(start, stop)' function`generates a sequence of numbers from `start` to `stop-1'.
- If `stop` (in this case, `questions = -1`) is less than `start` (by default, `start` is 0 if not specified), then the loop will not run once.
- Therefore, a block of code inside the `for i in range(questions)' loop:`will not be executed at all.
So we just enter -1 (the number of questions) and the flag is in our pocket.
---
### Flag

```
n00bz{m4th_15nt_4ll_4b0ut_3qu4t10n5}
```
