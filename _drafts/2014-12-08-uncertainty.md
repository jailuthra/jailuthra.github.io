---
layout: post
title: "Uncertainty is in the map, not in the territory"
tags: [math]
---
{% include JB/setup %}

In my mathematics pre-board exam (which I gave today), there was an
interesting question on
[Bayes' Theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem).
The same question was asked in the previous year's board exam in Delhi.
I'll be discussing that question here.

**Ques) Assume that the chances of a patient having a heart attack is 40%.
It is also assumed that a meditation and yoga course reduces the risk of
heart attack by 30% and prescription of a certain drug reduces its chances
by 25%. At a time a patient can choose any one of the two options with
equal probabilities. It is given that after going through one of the two
options the patient selected at random suffers a heart attack. Find the
probability that the patient followed a course of meditation and yoga.**

There is nothing wrong with the problem statement; the error I want to discuss
comes in play while solving it.
The error goes unnoticed because we arrive at the right final answer;
that is what we are taught to do, right?

```
Let us define the following events:  
H: The patient suffers a heart attack  
Y: The patient follows a course of Yoga/Meditation  
D: The patient takes the certain drug  

Then,  
P(H) = 40%  
P(Y) = P(D) = 1/2 (Patient chooses one of the options with equal probabilites)

P(H|Y) = Probability that patient suffers a heart attack, given that he
         followed a course of Yoga/Meditation
       = (100%-30%) X 40%
       = 28%

P(H|D) = Probability that patient suffers a heart attack, given that he
         takes the certain drug
       = (100%-25%) X 40%
       = 30%

We need to find the probability that the patient had followed a course of
Yoga/Meditiation given that he suffers a heart attack.
That would be P(Y|H)

Bayes' Theorem to the rescue,

               P(H|Y).P(Y)
P(Y|H) = -------------------------
         P(H|Y).P(Y) + P(H|D).P(D)

              28% X 1/2
       = ---------------------
         28% X 1/2 + 30% X 1/2

       = 14/29

So, 14/29 is the final answer

```

The final answer is correct. But some steps in this solution aren't
correct. Still this is the widely circulated solution and is being
taught in schools and getting published in various practice papers
found in help books.

Did you notice that I didn't use the simple form of Bayes' Theorem
in the solution?
If you've been studying under CBSE using the NCERT's Math Book, chances are
you didn't notice.

```
The simple form of Bayes' Theorem:

         P(B|A).P(A)
P(A|B) = -----------        
            P(B)

The solution uses an alternative form, which is derived using Law of total
probability:
(https://en.wikipedia.org/wiki/Law_of_total_probability)

P(B) = summation(P(B|Ai).P(Ai))
where {Ai: i = 1,2,3,...} is a partition of the sample space

For example A and A' (complement of A) are a partition of the sample space
because either A will happen (x)or A' will, both can't happen simultaneously.
And together they cover up the entire sample space
P(A) + P(A') = 1

Therefore using Law of total probabilites, we can write
P(B) = P(B|A).P(A) + P(B|A').P(A')

In the solution, if we had applied the simple form we would write:

          P(H|Y).P(Y)
P(Y|H) = -------------
             P(H)

Because Y and D parition the sample space into two parts, i.e. the patient
can only choose one of the two options for reducing the risk of heart
attack, and has to choose at least one.

We expanded P(H) using Law of total probabilites:
P(H) = P(H|Y).P(Y) + P(H|D).P(D)
     = 28% X 1/2 + 30% X 1/2
     = 29%

But we already know P(H) to be 40%
```

How did this happen? How can **P(H)** have two different values? Is Law of
total probability wrong? Nope. It works just fine. It is we who did
something wrong here.

In the solution we define H as  
**H: The patient suffers a heart attack**

We can't deny that **P(H)** = 40%, because that is given in the problem
statement.

We defined the probability that patient suffers a heart attack, given
that he took a course of Yoga/Medication as **P(Y|H)**

The total probability of **P(H)** we get doesn't match up because we haven't taken
a little piece of extra information into account:   
_The patient needs to choose one of the two options. He can't say that I
choose none of the two preventive measures **Y** and **D**_

The value of 29% we're equating to **P(H)** is not **P(H)**,
it is **P(X)** where X is the event
**X: The patient suffers a heart attack after choosing one of the two
preventive measures**

40% is the _raw probability_ (for lack of a better word) of any patient
having a heart attack irrespective of going through any of the preventive measures.
But once we're given the extra information that the patient has gone through one
preventive measure from Y and D, we assign a lower probability of 29%, that the
patient will suffer a heart attack

Sample space on which H (with probability 40%) is defined is a superset of
the sample space which is partitioned by D and Y. That's because there's no
information given whether the patients with 40% chance of heart attack went
through a preventive measure. So the biggest misstep in our previous
solution was to apply Law of total probability on P(H).

That's why we need an event X, which is completely partitioned by D and Y
so that we can apply Law of total probability.

The confusion arises because P(X|Y) and P(X|D) are computed using P(H).
Because the question states that the chance of a heart attack is reduced by
"30%" or "25%" by following Y or D.

The correct solution would be

```
Redefining our events
H: The patient suffers a heart attack
X: The patient suffers a heart attack after going through
   one of the two preventive measures
Y: The patient follows a course of Yoga/Meditation  
D: The patient takes the certain drug

P(X|Y) = Probability that patient suffers a heart attack, given that he
         went through a preventive measure, which was a course of Yoga/Meditation
       = 28%

P(X|D) = Probability that patient suffers a heart attack, given that he
         went through a preventive measure, which was taking a certain drug
       = 30%

And we need to find P(Y|X)
P(Y|X) = Probability that a patient went through a course of Yoga/Meditation,
         given that he suffers a heart attack (even after going through one of
         the preventive measures)

We use Law of total probability to find

P(X) = P(X|Y).P(Y) + P(X|D).P(D)
     = 29%

Then using Bayes' Theorem

P(Y|X) = 14/29
```
As you can see, getting some extra information about an event affects the
probability of it. To quote Eliezer Yudkowsky, [Probability is in the mind]
(http://lesswrong.com/lw/oj/probability_is_in_the_mind/).

If we have a device that can detect whether a person will have a heart
attack in near future, probability of that person having a heart attack
will be either 1 or 0 depending on what the device tells.
The event of having a heart attack isn't inherently random. The probability
we assign is a number representing *our lack of information*

When we toss a coin, if we are able to measure the exact value of force,
the position where we apply it, the initial position of the coin extremely
precisely; we can predict the outcome of the toss that is,
P(heads) will be either 1 or 0.

Our currently assigned probabilities of 1/2 and 1/2 to the event of getting
tails and heads are *our lack of information* and not because of some
spooky randomness inside the coin.

**Uncertainity isn't in the territory, it's in the map**

Therefore, when we get some extra information about an event with some
prior probability, this information can affect the probability of the
event. This is what Bayes' Theorem is all about.
