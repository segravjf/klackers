# Simulating Klackers
This past holiday season, I had the opportunity to play a dice game with my extended family called Klackers (also informally known as "Shut the Box"). The game involves knocking down 9 wooden numbers from 1 to 9 based on the outcome of rolling either one or two dice continually until either all of the numbers are knocked down or you cannot knock any more numbers. In the former case, you "klack" and win!

![image](https://github.com/segravjf/klackers/assets/13812785/fc418f40-e34e-4503-94c5-f52d9135fa47)


For example, at the onset of a new game, if you roll a 7, you have several options for how to proceed: knock down the 7, knock down the 6 and 1, the 5 and 2, the 4 and 3, or even 1 and 2 and 4. After making your first knockdown selections, you continue with the hopes of clearing the rest of the numbers perfectly.

Like any dice game, there is a good deal of luck involved to land the precise sequences needed to perfectly knock down each number. But there's also a strategy to maximize your chance of winning.

## The problem
What is the optimal strategy for how to pick which numbers to knock down and increase your chances of "klacking"?

## The hypothesis
I hypothesized from my experience playing the game that it was most important to rid yourself of the highest numbers -- 7, 8, and 9 -- first. That way, you can still use the smaller multiples to sum up to the larger rolls, while also having the flexibility to survive a 3 or 4 if needed.

## The approach
I created a simulated klackers environment in a Python notebook and simulated 4 strategies: one where you seek to get rid of the highest numbers first, one where you seek to get rid of the lowest numbers first, one where you choose the middle-most option available, and one where you seek to get rid of the *most* numbers at once. 

For each strategy, I simulated 10,000 games, capturing the output to analyze.

## Results
Honestly, it wasn't even close. 

Removing the largest numbers available with each roll had by far the best strategy, klacking out in 7.8% of the trials. The second-best strategy, the midpoint strategy, only klacked out at a 2.8% clip, less than half the rate at which the max strategy paid out.

Fitting with the intuition of the strategy, the largest number strategy had a median remainder of only 11, compared with 19 for the midpoint, 24 for the most, and 25 for the lowest number strategy. While this is partially determined by mathematical certainty (larger numbers gone means less remainder to sum), the sheer gap was impressive to me. The distribution of remainders bears this out:
![image](https://github.com/segravjf/klackers/assets/13812785/cd5fbf3d-54db-4633-bf93-7266946275f6)

Even looking at the count of numbers not knocked over, you see a clear advantage for the highest numbers strategy:
![image](https://github.com/segravjf/klackers/assets/13812785/c3edf1b2-0adb-4cb1-9124-b828d5b7746e)

This will make next December even easier for me.

## Next time
While this was more of an academic exercise than anything (the intuition is pretty straightforward in this game), it was still interesting to me that you can expect up to an 8% win rate with a pure strategy like this. That being said, to make it a more fair fight, we could test this pure strategy against some more nuanced strategies:
* Switch strategies following certain milestones, such as after 9/8/7 are removed or if even or odd numbers dominate the board.
* Favor removing 2 or 3 instead of 1 for additional flexibility on evens/odds while still getting rid of less savory results.
* Add a dimension to make it helpful for gambling purposes, such as expected value given current gamestate

There's also room to improve the analysis itself, namely:
* Capture the number of rolls it takes and your conditional probability of winning given how many rolls you've gone so far.
* Better visualizations to capture the gamestate and decisionmaking



