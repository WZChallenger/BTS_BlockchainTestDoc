# BTS_BlockchainTestDoc

## Challenge 1 (10 min)
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

## Challenge 2 (10 min)
**Q:** What tools do you use on a day to day basis? Explain why they are important.

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

## Challenge 4 (35 min)
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

**A:**
```
function BuildStringFromMatrix(inMatrixElements, NumRows, NumColumns) {
  let direction = 0; // 0: horizontal, 1: vertical
  let horzDirection = 1; // 1: right, -1: left, 0: stay
  let vertDirection = 0; // 1: down, -1: up, 0: stay

  let output = []; // output array
  let i = 0; // current row
  let j = 0; // current col
  let left = 0,
    right = NumColumns - 1,
    top = 1,
    bottom = NumRows - 1;

  while (output.length < NumRows * NumColumns) {
    output.push(inMatrixElements[i * NumColumns + j]);

    if (direction == 0) {
      if (horzDirection == 1 && j == right) {
        horzDirection = 0;
        vertDirection = 1;
        direction = 1;
        right--;
      }
      if (horzDirection == -1 && j == left) {
        horzDirection = 0;
        vertDirection = -1;
        direction = 1;
        left++;
      }
    } else if (direction == 1) {
      if (vertDirection == 1 && i == bottom) {
        horzDirection = -1;
        vertDirection = 0;
        direction = 0;
        bottom--;
      }
      if (vertDirection == -1 && i == top) {
        horzDirection = 1;
        vertDirection = 0;
        direction = 0;
        top++;
      }
    }
    i += vertDirection;
    j += horzDirection;
  }

  return output;
}

const Matrix = [2, 3, 4, 8, 5, 7, 9, 12, 1, 0, 6, 10];
console.log(BuildStringFromMatrix(
  Matrix,
  3,
  4
));
```

Check the result on [here](https://codesandbox.io/s/bold-flower-zndyf7?file=/src/index.js:1366-1409).

## Challenge 5 (40 min)
**Q:** Setup a project and create a contract
### Summary
ETHPool provides a service where people can deposit ETH and they will receive weekly
rewards. Users must be able to take out their deposits along with their portion of rewards
at any time. New rewards are deposited manually into the pool by the ETHPool team
each week using a contract function.
### Requirements
- Only the team can deposit rewards.
- Deposited rewards go to the pool of users, not to individual users.
- Users should be able to withdraw their deposits along with their share of rewards
considering the time when they deposited.
### Example:
Let's say we have users ***A*** and ***B*** and team ***T***.<br>
***A*** deposits 100, and ***B*** deposits 300 for a total of 400 in the pool.<br>
Now ***A*** has 25% of the pool and ***B*** has 75%. When ***T*** deposits 200 rewards, ***A*** should be<br>
able to withdraw 150 and ***B*** able to withdraw 450 once the period ends.<br>
Here’s an example:<br>
***A*** deposits then ***T*** deposits then ***B*** deposits then ***A*** withdraws and finally ***B*** withdraws.<br>
***A*** should get their deposit + all the rewards.<br>
***B*** should only get their deposit because rewards were sent to the pool before they<br>
participated.<br>
***A*** and ***B*** should get their deposit + the corresponding rewards based on the time they have<br>
been in the pool before ***T*** deposited the reward.<br>

### Goal
Design and code a contract for ETHPool, take all the assumptions you need to move forward. Think about the most gas-efficient implementation you can.<br>
You can use any development tools you prefer: Hardhat, Truffle, Brownie, Solidity, Vyper.

### Useful resources:
- Solidity Docs: https://docs.soliditylang.org/en/v0.8.7
- Educational Resource: https://github.com/scaffold-eth/scaffold-eth

**A:** Check the source code on [here](https://github.com/WZChallenger/BTS_TestETHPoolSC).
<br>

To test:
```
npm test
```

## Challenge 6 (20 min)
**Q:** Deploy the contract to any Ethereum testnet of your preference. Keep record of the deployed address.

### Bonus:
- Add Radspec
- Verify the contract in Etherscan

**A:** Ropsten: [0xE71565Db15f68b4cf36d576e5F9Bc8eF0F56B30f](https://ropsten.etherscan.io/address/0xE71565Db15f68b4cf36d576e5F9Bc8eF0F56B30f#code).

## Challenge 7 (15 min)

**Q:** Create a script (or a Hardhat task) to query the total amount of ETH held in the contract
and any other thing you find interesting.<br>
You can use any library you prefer: Ethers.js, Web3.js, Web3.py, eth-brownie

**A:** Clone [BTS_TestETHPoolSC](https://ropsten.etherscan.io/address/0xE71565Db15f68b4cf36d576e5F9Bc8eF0F56B30f#code).
<br>
Copy .env.example to .env and make sure all the environment variables are set.
<br>
Make sure your account A, B, owner(deployer) has enough rETH.
<br>
Run interact task.
```
npm run interact-pool
```

## Challenge 8 (30 min + syncing time)

**Q:** Create a subgraph
<br>
Create a subgraph that index users of the contract from the first challenge into entities as
you see convenient. For example, it would be great to query all user deposits to the pool.
You can be creative and add other information that you find relevant.

**A:** Check the subgraph playround on [here](https://thegraph.com/hosted-service/subgraph/macharry89/ethpool?query=users).
<br>
[Here](https://github.com/WZChallenger/BTS_TestETHPoolSubgraph) is the subgraph source.

