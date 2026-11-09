# 5-minute presentation script (simple words)

Topic: Can a computer tell from a street photo if the street is dirty or clean? (Logistic Regression, Karela civic reports)

The matching PowerPoint is `Karela_ML_Presentation.pptx`. This script is also in its speaker notes, slide by slide.

Speakers: Randel (R) and Trishia (T). You can swap the parts, but both of you must speak, and each of you should be able to answer questions on any slide.

Timing: about 720 words, which is close to 5 minutes. Read it aloud once with a timer. If it runs long, cut the sentences marked (optional).

Tip: say it the way you would explain it to a classmate. Change any sentence that does not sound like you.

---

## Slide 1: The question (R, about 30 seconds)

> Hello. We are Randel and Trishia. We asked one question: can a computer look at a photo of a street and tell if it is dirty or clean?
>
> This comes from our app, Karela. We need machine learning in our thesis, so we used this activity to test it on our research. People send photos to report dirty places. If a computer can make a first guess, nobody has to check every photo by hand. We tested this idea with a simple method called logistic regression.

## Slide 2: The data (T, about 45 seconds)

> We used a free dataset from Kaggle. It has 237 street photos. Each photo is marked clean or dirty. Anyone can use it, because it is public domain.
>
> Some photos appeared twice. We removed 8 of them, so the computer is never tested on a photo it has already seen. That left 229 photos: 111 clean and 118 dirty. The two groups are almost the same size, so the score is fair.
>
> (optional) The page does not tell us where the photos came from. We will come back to this.

## Slide 3: Photos into numbers, and why logistic regression (R, about 45 seconds)

> A computer cannot read a photo the way we do. So we turned each photo into 7 numbers. They are: how bright it is, how strong the colors are, contrast, edge density, how many different colors there are, how much green, and how much grey.
>
> Edge density means how many sharp lines and small details are in the photo. A pile of trash has many small things, so it has a lot of edges.
>
> We used logistic regression because our answer is only yes or no: dirty or clean. It gives a number from 0 to 1. That is the chance that the street is dirty. If the chance is 0.5 or higher, we say dirty. Linear regression gives a number on a scale, so it does not fit here.

## Slide 4: Edge density (R, about 15 seconds)

> This chart shows edge density. The middle clean photo is about 0.13. The middle dirty photo is about 0.24, almost double. Dirty streets have more small things, so they have more edges.

## Slide 5: Results (T, about 60 seconds)

> We taught the computer with 183 photos. Then we tested it on 46 new photos that it had never seen. It was right 82.6 percent of the time. If it only guessed the bigger group, it would be right 51.5 percent of the time. So it really learned something.
>
> Look at the four boxes. It found 21 dirty streets and passed 17 clean streets. It called 5 clean streets dirty by mistake. And it missed 3 dirty streets.
>
> Two more scores. Precision is 0.81. This means that when it says dirty, it is right about 81 percent of the time. Recall is 0.88. This means it finds 88 percent of the really dirty streets.
>
> For Karela, recall is the most important one. If we miss a dirty street, a real problem gets ignored. If we lower the cutoff to 0.3, it finds 96 percent of the dirty streets, but it also gives more false alarms.

## Slide 6: What mattered most (R, about 45 seconds)

> Which numbers helped the most? Edge density was number one. Each step up in edge density makes the odds of dirty about 7.7 times bigger. Green was number two. More green means the street is more likely clean.
>
> Before testing, we guessed that busy photos are dirty. That was right. We also guessed that grey roads are clean, but grey was not a clear sign. The green result surprised us. We think many of the clean photos show roads with trees.

## Slide 7: Limits (T, about 45 seconds)

> We do not trust this model yet. We tested it on only 46 photos, so the score can go up or down by luck. When we tried five different splits of the photos, the score went from 76 to 87 percent.
>
> Many clean photos are empty highways. So the computer may be learning "empty road or pile of trash", not "clean or dirty". The dirty photos seem to come from other countries, not from Tuguegarao.
>
> The computer only sees colors and edges. It cannot see what is in the photo. So fallen leaves, or a busy market, could look dirty to it.

## Slide 8: Lesson and next step (R, about 30 seconds)

> Here is what we have learned: a good score does not mean a good model. Removing repeated photos, testing on new photos, and being honest about weak data matter more than the number.
>
> Now that we have tried it, our next step in our research is to use photos from Tuguegarao, taken with permission, with faces and plates blurred. We also want a model that can see the real objects, and a person should check the photos that the computer is not sure about. Thank you for listening.

(optional, if your lecturer wants it said aloud) "We used an AI assistant to help with the code and the writing. The details are in our report."

---

## Questions you may be asked, with simple answers

1. **Why not linear regression?** Our answer is yes or no. Linear regression can give numbers below 0 or above 1, which makes no sense for a chance. Logistic regression keeps the answer between 0 and 1.
2. **Why did you split the photos into two groups?** One group teaches the computer. The other group is only for testing. If we test with the same photos it learned from, the score looks better than it really is.
3. **What is edge density?** It is the share of the photo that has sharp lines and small details. A pile of trash has many small things, so it has many edges.
4. **Why is 82.6 percent not good enough?** We tested on only 46 photos, many clean photos are easy (like empty highways), and the photos are not from Tuguegarao.
5. **What would you do with more time?** Take and label photos from Tuguegarao, use a model that can see real objects, blur faces and plates, and have a person check the unsure ones.
6. **What does the number 2.05 for edge density mean?** It shows that edge density is the biggest push toward "dirty". In simple terms, each step up in edge density makes the odds of dirty about 7.7 times bigger, when the other numbers stay the same.
7. **Why did you remove repeated photos?** If the same photo is in both groups, the computer is tested on something it has already seen, and the score is not honest.
8. **What is precision, and what is recall?** Precision: when the computer says dirty, how often is it right? Recall: out of all the really dirty streets, how many did it find?
9. **Did you use AI?** Yes, and it is written in our report. We must be able to explain the code, so be ready to explain how a photo turns into numbers (section 3 of the notebook) and how the model is trained and tested (section 7).

## Before you present

- [ ] Practise once with a timer, and cut the (optional) parts if it runs long.
- [ ] Decide who says which slide. Both of you must speak.
- [ ] Install the Excon font on the computer you present from, or export the deck to PDF first.
- [ ] Check every number against your report.
