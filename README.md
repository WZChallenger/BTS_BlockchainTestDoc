# BTS_BlockchainTestDoc

## Challenge 1
**Q:** You have been given 2 unusually durable PS5’s. You are in an office building that is
100 stories high. Using the fewest possible number of drops from windows in your office
building, determine the highest floor you can drop a PS5 from and have it survive. For
example, they might be able to take the drop from the 30th floor, but not the 31st. You
can break both PS5s in your search. State the worst case number of drops needed and
explain how you arrived at that answer. (5 min)

**A:** 32 times

Applied half-dividing method.<br>
First time, I try to drop on 50th floor.

- If the first PS5 is broken:<br>
  To keep the second PS5 as long as possible, I try to climb up from the 1st floor with the second PS5.
  So I won't try the half-dividing method (25th floor) at this moment.

- If the first PS5 is not broken:<br>
  To keep the second PS5 as long as possible, I try to climb up from the 51st floor with the second PS5.
  So I won't try the half-dividing method (25th floor) at this moment.

Absolutely the first PS5 will be broken because its limit is 30th floor.
At last,  after the 32nd attempt, I can confirm both PS5s are broken.

## Challenge 2
**Q:** What tools do you use on a day to day basis? Explain why they are important.  (10 min)

**A:**
  - Github - To explore a lot of open source, issues, code writing and project management, this is most important for me.
  - VSCode - To write code
  - Stackoverflow - To explore a lot of issues and solutions.
  - Slack, Google meeting, Microsoft Teams, Zoom and the other communication tools - To meet people.
  - MailBox - To check personal & global news.

## Challenge 3
**Q:** Imagine that you are interviewing candidates for this position. Write an example
question to be used during the interview process. Explain how this question tests the
candidate’s knowledge, and how this knowledge is representative of the type of problems
you would expect to tackle when working as a front-end developer.

**A:**

## Challenge 4
**Q:** In Javascript, **Without using built-in functions or imported libraries/modules,** write
a function with the following signature that, given a matrix of integers, returns a string
with the entries of that matrix appended in clockwise order. For instance, the 3x4 matrix
below:
Hint: Keep in mind there could be many different dimensions of a matrix passed in!

```
const Matrix = [2, 3, 4, 8,
                5, 7, 9, 12,
                1, 0, 6, 10]
would make the string "2, 3, 4, 8, 12, 10, 6, 0, 1, 5, 7, 9".
```