# Google-Foobar-Public

## __My Attempts on Google's secret hiring challenge__

![IMG](/welcome.png)


Foobar is Google's secret hiring platform that usually pops up while searching some technical stuff on Google, For instance searching ArrayList java popped it for me.
As Soon as you trigger the Foobar challenge , you'll see the current page open up like a tunnel and you'll be greated with a message like "You seem to speak our language, up for a challenge?" and then you can accept it and the game begins!

**The portal consists of 5 Levels, Questions from Data Structures and Algorithm.
Level 1 has 1 question , level 2 - 2 Questions , level 3 - 3 Questions , level 4 - 2 questions and level 5 - 1 question.**

There are various sets of questions that people recieve, the difficulty of questions is almost same in all sets.
So further, i'll be discussing my Question set for The Google foobar.


## LEVEL 1 
Level one is a cakewalk for anyone with little touch of Data structures, Note : Questions are story based , in level 1 keeping the story aside, basically i was given 2 lists and had to find the element which was not present in both list (There was only 1 uncommon element) , there are numerous ways to this - like using hashmap to store keys of first list and then second list and if element is not found in the hashmap return it, or you can take XOR of all elements and the one that remains is the answer.

## LEVEL 2
### Challenge 1 - Gearing Up for Destruction
So here's the question:
```
Gearing Up for Destruction
==========================

As Commander Lambda's personal assistant, you've been assigned the task of configuring the LAMBCHOP doomsday device's axial orientation
gears. It should be pretty simple - just add gears to create the appropriate rotation ratio. But the problem is, due to the layout of the LAMBCHOP and
the complicated system of beams and pipes supporting it, the pegs that will support the gears are fixed in place.

The LAMBCHOP's engineers have given you lists identifying the placement of groups of pegs along various support beams. You need to place a gear on
each peg (otherwise the gears will collide with unoccupied pegs). The engineers have plenty of gears in all different sizes stocked up, so you can
choose gears of any size, from a radius of 1 on up. Your goal is to build a system where the last gear rotates at twice the rate (in revolutions per
minute, or rpm) of the first gear, no matter the direction. Each gear (except the last) touches and turns the gear on the next peg to the right.

Given a list of distinct positive integers named pegs representing the location of each peg along the support beam, write a function answer(pegs) which,
if there is a solution, returns a list of two positive integers a and b representing the numerator and denominator of the first gear's radius in its
simplest form in order to achieve the goal above, such that radius = a/b. The ratio a/b should be greater than or equal to 1. Not all support
configurations will necessarily be capable of creating the proper rotation ratio, so if the task is impossible, the function answer(pegs) should return
the list [-1, -1].

For example, if the pegs are placed at [4, 30, 50], then the first gear could have a radius of 12, the second gear could have a radius of 14, and the
last one a radius of 6. Thus, the last gear would rotate twice as fast as the first one. In this case, pegs would be [4, 30, 50] and answer(pegs) should
return [12, 1].

The list pegs will be given sorted in ascending order and will contain at least 2 and no more than 20 distinct positive integers, all between 1 and
10000 inclusive.

Languages
=========

To provide a Python solution, edit solution.py
To provide a Java solution, edit solution.java

Test cases
==========

Inputs:
    (int list) pegs = [4, 30, 50]
Output:
    (int list) [12, 1]

Inputs:
    (int list) pegs = [4, 17, 50]
Output:
    (int list) [-1, -1]

Use verify [file] to test your solution and see how it does. When you are finished editing your code, use submit [file] to submit your answer. If your
solution passes the test cases, it will be removed from your home folder.
```

Now this question can be solved using gauss elemination method of solving equations but that would be an overkill, the thing here is that the radius of the first peg that we want is a fraction,the denominator can be either 1 or 3 , im not showing the math here. You can run 2 loops , one which checks if the denominator is 1 ***(start from the first peg's radius , the second pegs radius will be Distance between 2 pegs - radius of first peg) , now the the radius of third peg will be distance bw peg 2 and 3 - radius of second peg and so on, when we reach the last peg the radius should be twice the first peg , if its so, we have our solution)*** we also have to check for denominator 3 **(Think about it!)** and return if there is an answer.


### Challenge 2 - Hey, I Already did that
Question:
```
Hey, I Already Did That!
Commander Lambda uses an automated algorithm to assign minions randomly to tasks, in order to keep her minions on their toes. But you've noticed a flaw in the algorithm - it eventually loops back on itself, so that instead of assigning new minions as it iterates, it gets stuck in a cycle of values so that the same minions end up doing the same tasks over and over again. You think proving this to Commander Lambda will help you make a case for your next promotion.

You have worked out that the algorithm has the following process:

Start with a random minion ID n, which is a nonnegative integer of length k in base b

Define x and y as integers of length k. x has the digits of n in descending order, and y has the digits of n in ascending order

Define z = x - y. Add leading zeros to z to maintain length k if necessary

Assign n = z to get the next minion ID, and go back to step 2

For example, given minion ID n = 1211, k = 4, b = 10, then x = 2111, y = 1112 and z = 2111 - 1112 = 0999. Then the next minion ID will be n = 0999 and the algorithm iterates again: x = 9990, y = 0999 and z = 9990 - 0999 = 8991, and so on.

Depending on the values of n, k (derived from n), and b, at some point the algorithm reaches a cycle, such as by reaching a constant value. For example, starting with n = 210022, k = 6, b = 3, the algorithm will reach the cycle of values [210111, 122221, 102212] and it will stay in this cycle no matter how many times it continues iterating. Starting with n = 1211, the routine will reach the integer 6174, and since 7641 - 1467 is 6174, it will stay as that value no matter how many times it iterates.

Given a minion ID as a string n representing a nonnegative integer of length k in base b, where 2 <= k <= 9 and 2 <= b <= 10, write a function answer(n, b) which returns the length of the ending cycle of the algorithm above starting with n. For instance, in the example above, answer(210022, 3) would return 3, since iterating on 102212 would return to 210111 when done in base 3. If the algorithm reaches a constant, such as 0, then the length is 1.

Languages
To provide a Python solution, edit solution.py To provide a Java solution, edit solution.java

Test cases
Inputs: (string) n = "1211" (int) b = 10 Output: (int) 1

Inputs: (string) n = "210022" (int) b = 3 Output: (int) 3

```

This is a fairly Simple question and the bruteforce method works well, just generate a K-Base subtractor i,e a function that takes the base , number 1 and number 2 and substract it and return it , store the returned value in a hashmap with the id as value , now if the value repeats return current id - hashmap(returned_element).key ;


## LEVEL 3
### Challenge 1 - Bomb baby

Question:
```
"""
Bomb, Baby!
===========

You're so close to destroying the LAMBCHOP doomsday device you can taste it! But in order to do so, you need to deploy special self-replicating bombs designed for you by the brightest scientists on Bunny Planet. There are two types: Mach bombs (M) and Facula bombs (F). The bombs, once released into the LAMBCHOP's inner workings, will automatically deploy to all the strategic points you've identified and destroy them at the same time. 

But there's a few catches. First, the bombs self-replicate via one of two distinct processes: 
Every Mach bomb retrieves a sync unit from a Facula bomb; for every Mach bomb, a Facula bomb is created;
Every Facula bomb spontaneously creates a Mach bomb.

For example, if you had 3 Mach bombs and 2 Facula bombs, they could either produce 3 Mach bombs and 5 Facula bombs, or 5 Mach bombs and 2 Facula bombs. The replication process can be changed each cycle. 

Second, you need to ensure that you have exactly the right number of Mach and Facula bombs to destroy the LAMBCHOP device. Too few, and the device might survive. Too many, and you might overload the mass capacitors and create a singularity at the heart of the space station - not good! 

And finally, you were only able to smuggle one of each type of bomb - one Mach, one Facula - aboard the ship when you arrived, so that's all you have to start with. (Thus it may be impossible to deploy the bombs to destroy the LAMBCHOP, but that's not going to stop you from trying!) 

You need to know how many replication cycles (generations) it will take to generate the correct amount of bombs to destroy the LAMBCHOP. Write a function answer(M, F) where M and F are the number of Mach and Facula bombs needed. Return the fewest number of generations (as a string) that need to pass before you'll have the exact number of bombs necessary to destroy the LAMBCHOP, or the string "impossible" if this can't be done! M and F will be string representations of positive integers no larger than 10^50. For example, if M = "2" and F = "1", one generation would need to pass, so the answer would be "1". However, if M = "2" and F = "4", it would not be possible.

Test cases
==========

Inputs:
    (string) M = "2"
    (string) F = "1"
Output:
    (string) "1"

Inputs:
    (string) M = "4"
    (string) F = "7"
Output:
    (string) "4"
"""

```

Yeah, so Key To Bomb Baby lies in the fact that, From whatever M and F we are Given , Can we reach a state M =1 & F =1, that is the initial stage.  
So what we do it if M > F we so M = M-F. and  if F>M we do F = F-M.  
Example:  
M = 4 , F = 7;  
Step 1: F = F - M --> F = 7 - 4 --> Now M = 4 and F = 3;  
Step 2: M = M - F --> M = 4 -3 --> Now M = 1 and F = 3;  
step 3 : F = F - M --> F = 3 -1 --> Now M = 1 and F = 2 ;  
Step 4 : F = F -M --> F = 2 -1 --> Now M =1 and F =1 , so we have reached the state (1,1) that is the combination is possible. so we return the number of steps that take this process.  
But the problem is this process will give us TLE according to the constraints , so a quick optimization will be to check the number of time the smaller number divides the bigger number completely , Lets say M = 1 and F = 4 we know that thiss process will take4 steps , then why to do it 4 times and increase the complexity? if we are maintaining variable steps for counting,then we can directly do steps= steps + F/M , and decrese F by F/M (floor value) i.e F = F-F/M ; and then continue the process.  
Also a quick observation if the GCD of the numbers is not equal to 1 , there can be no solution.  
Hope that helps!

### Challenge 2 - DOOMSDAY FUEL
This is where is got me! like i must have tried 5 different fresh approaches and each of the failed at some point,This is called Doomsday fuel. In this question we have different states of an ore, we are given a matrix that shows how many times 1 state goes to another , you can basically look it as an adjecency matrix of a graph , that'll help you grow in the question.
A better post to explain this is ![DOOMSDAY FUEL] (https://github.com/ivanseed/google-foobar-help/blob/master/challenges/doomsday_fuel/doomsday_fuel.md)

### Challenge 3 - Fuel Injection
```
Fuel Injection Perfection
Commander Lambda has asked for your help to refine the automatic quantum antimatter fuel injection system for her LAMBCHOP doomsday device. It's a great chance for you to get a closer look at the LAMBCHOP - and maybe sneak in a bit of sabotage while you're at it - so you took the job gladly.

Quantum antimatter fuel comes in small pellets, which is convenient since the many moving parts of the LAMBCHOP each need to be fed fuel one pellet at a time. However, minions dump pellets in bulk into the fuel intake. You need to figure out the most efficient way to sort and shift the pellets down to a single pellet at a time.

The fuel control mechanisms have three operations:

Add one fuel pellet
Remove one fuel pellet
Divide the entire group of fuel pellets by 2 (due to the destructive energy released when a quantum antimatter pellet is cut in half, the safety controls will only allow this to happen if there is an even number of pellets)
Write a function called answer(n) which takes a positive integer as a string and returns the minimum number of operations needed to transform the number of pellets to 1. The fuel intake control panel can only display a number up to 309 digits long, so there won't ever be more pellets than you can express in that many digits.

For example:

answer(4) returns 2: 4 -> 2 -> 1  
answer(15) returns 5: 15 -> 16 -> 8 -> 4 -> 2 -> 1
Languages
To provide a Python solution, edit solution.py To provide a Java solution, edit solution.java

Test cases
Inputs:

(string) n = "4"
Output:

(int) 2
Inputs:

(string) n = "15"
Output:

(int) 5
Use verify [file] to test your solution and see how it does. When you are finished editing your code, use submit [file] to submit your answer. If your solution passes the test cases, it will be removed from your home folder.

```
So this is a typical dynamic programming programing question, we are given a number X and either we can add 1 to the number, we can substract 1 , or we can divide the number by two, so use a dp array to store the states that have already been processed. if a number %2 ==0 straight away divide it by 2 . if not then choose the minimum of minsteps(number +1) , minsteps(number - 1). Also if you are doing in Java , use Big integer.

## LEVEL 4
### Challenge 1
Question:
```
Running with Bunnies
====================

You and your rescued bunny prisoners need to get out of this collapsing death trap of a space station - and fast! Unfortunately, some of the bunnies have been weakened by their long imprisonment and can't run very fast. Their friends are trying to help them, but this escape would go a lot faster if you also pitched in. The defensive bulkhead doors have begun to close, and if you don't make it through in time, you'll be trapped! You need to grab as many bunnies as you can and get through the bulkheads before they close. 

The time it takes to move from your starting point to all of the bunnies and to the bulkhead will be given to you in a square matrix of integers. Each row will tell you the time it takes to get to the start, first bunny, second bunny, ..., last bunny, and the bulkhead in that order. The order of the rows follows the same pattern (start, each bunny, bulkhead). The bunnies can jump into your arms, so picking them up is instantaneous, and arriving at the bulkhead at the same time as it seals still allows for a successful, if dramatic, escape. (Don't worry, any bunnies you don't pick up will be able to escape with you since they no longer have to carry the ones you did pick up.) You can revisit different spots if you wish, and moving to the bulkhead doesn't mean you have to immediately leave - you can move to and from the bulkhead to pick up additional bunnies if time permits.

In addition to spending time traveling between bunnies, some paths interact with the space station's security checkpoints and add time back to the clock. Adding time to the clock will delay the closing of the bulkhead doors, and if the time goes back up to 0 or a positive number after the doors have already closed, it triggers the bulkhead to reopen. Therefore, it might be possible to walk in a circle and keep gaining time: that is, each time a path is traversed, the same amount of time is used or added.

Write a function of the form answer(times, time_limit) to calculate the most bunnies you can pick up and which bunnies they are, while still escaping through the bulkhead before the doors close for good. If there are multiple sets of bunnies of the same size, return the set of bunnies with the lowest prisoner IDs (as indexes) in sorted order. The bunnies are represented as a sorted list by prisoner ID, with the first bunny being 0. There are at most 5 bunnies, and time_limit is a non-negative integer that is at most 999.

For instance, in the case of
[
  [0, 2, 2, 2, -1],  # 0 = Start
  [9, 0, 2, 2, -1],  # 1 = Bunny 0
  [9, 3, 0, 2, -1],  # 2 = Bunny 1
  [9, 3, 2, 0, -1],  # 3 = Bunny 2
  [9, 3, 2, 2,  0],  # 4 = Bulkhead
]
and a time limit of 1, the five inner array rows designate the starting point, bunny 0, bunny 1, bunny 2, and the bulkhead door exit respectively. You could take the path:

Start End Delta Time Status
    -   0     -    1 Bulkhead initially open
    0   4    -1    2
    4   2     2    0
    2   4    -1    1
    4   3     2   -1 Bulkhead closes
    3   4    -1    0 Bulkhead reopens; you and the bunnies exit

With this solution, you would pick up bunnies 1 and 2. This is the best combination for this space station hallway, so the answer is [1, 2].

Languages
=========

To provide a Python solution, edit solution.py
To provide a Java solution, edit solution.java

Test cases
==========

Inputs:
    (int) times = [
                    [0, 1, 1, 1, 1], 
                    [1, 0, 1, 1, 1], 
                    [1, 1, 0, 1, 1], 
                    [1, 1, 1, 0, 1], 
                    [1, 1, 1, 1, 0]
                  ]
    (int) time_limit = 3
Output:
    (int list) [0, 1]

Inputs:
    (int) times = [
                    [0, 2, 2, 2, -1], 
                    [9, 0, 2, 2, -1], 
                    [9, 3, 0, 2, -1], 
                    [9, 3, 2, 0, -1], 
                    [9, 3, 2, 2, 0]
                  ]
    (int) time_limit = 1
Output:
    (int list) [1, 2]

Use verify [file] to test your solution and see how it does. When you are finished editing your code, use submit [file] to submit your answer. If your solution passes the test cases, it will be removed from your home folder.
```
...to be continued
