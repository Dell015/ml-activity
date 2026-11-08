# 5-minute presentation script

Topic: Can a computer tell from a street photo if the street is dirty or clean? (Logistic Regression, Karela civic reports)

The matching PowerPoint is `Karela_ML_Presentation.pptx`. This script is also in its speaker notes, slide by slide.

Speakers: Randel (R) and Trishia (T). You can swap the parts, but both of you must speak, and each of you should be able to answer questions on any slide.

Timing: the script below is about 750 words, which is a little over 5 minutes at a normal speaking speed. Read it out loud once with a timer. If it runs long, cut the sentences marked (optional).

Use your own words. This is a draft to adapt, not to read word for word.

---

## Slide 1: The question (R, about 30 seconds)

Slide: title, your names, one street photo that is dirty and one that is clean.

> Good day. We are Randel Serafica and Trishia Joy Rirao. Our project asks a simple question that comes from our app, Karela: can a computer tell from a street photo whether the street is dirty or clean?
>
> In Karela, residents report places with photos. If a model can make a first guess, people do not have to check every photo by hand. We tested this idea with logistic regression.

## Slide 2: The data (T, about 45 seconds)

Slide: dataset name, "237 photos, labelled clean or dirty", chart `1_class_counts.png`.

> Our data is the Clean or Littered Road Classification dataset from Kaggle. It has 237 photos, each labelled clean or dirty, and it is marked CC0, which means public domain.
>
> We removed 8 repeated photos, so the same picture could not be in both training and testing. That left 229 photos, 111 clean and 118 dirty. The two groups are almost equal in size, so accuracy is a fair measure. (optional) The page does not say where the photos came from, and we come back to that later.

## Slide 3: Turning photos into numbers, and why logistic regression (R, about 45 seconds)

Slide: list of the 7 features, and "dirty = 1, clean = 0".

> A photo is not a table of numbers, so we measured each one. We shrank every photo to the same size and calculated seven numbers: brightness, colour strength, contrast, edge density, colour variety, share of green and share of grey.
>
> Edge density, for example, is the share of pixels that are very different from their neighbours. It is high when a scene is full of small objects, like a pile of rubbish.
>
> We chose logistic regression because our answer is yes or no, dirty or clean. It turns the numbers into a probability between 0 and 1, and we call the photo dirty at 0.5 or more. Linear regression predicts a number on a scale, so it does not fit this question.

## Slide 4: Edge density (R, about 15 seconds, continues from slide 3)

Slide: chart of edge density for clean and dirty photos, with the two medians (0.13 and 0.24).

> Here is what edge density looks like in our data. The middle clean photo is about 0.13 and the middle dirty photo is about 0.24, nearly double. A pile of rubbish is full of small objects, so it has many edges, and a smooth road has few.

## Slide 5: Results (T, about 60 seconds)

Slide: confusion matrix and the accuracy, precision, recall and F1 numbers.

> We trained on 183 photos and tested on 46 photos the model had never seen. Test accuracy was 82.6 percent. Always guessing the bigger class would give only 51.5 percent, so the model did learn something.
>
> In the confusion matrix, 21 dirty streets were found and 17 clean streets were passed. 5 clean streets were wrongly called dirty, and 3 dirty streets were missed. Precision was 0.81, recall 0.88 and F1 0.84.
>
> For Karela, recall matters most, because missing a dirty street means ignoring a real problem. If we lower the threshold to 0.3, recall rises to 0.96, but we get more false alarms.

## Slide 6: What mattered most (R, about 45 seconds)

Slide: the coefficient chart, and our hypothesis from Part 1 checked as right, not clear and a surprise.

> The strongest feature was edge density. When it goes up by one standard deviation, the odds of dirty go up about 7.7 times. The second was green share: more green makes the odds fall to about 0.37, so the street is more likely clean.
>
> Our hypothesis was partly right. We predicted that cluttered scenes would be dirty, and that was correct. We also predicted that grey roads would be clean, but grey was not a clear sign. Green share surprised us. We think it is because many of the clean photos are tree-lined roads.

## Slide 7: Limits (T, about 45 seconds)

Slide: the 76% to 87% range across five splits, and four short limits.

> We do not trust this model for real decisions. The test set is only 46 photos, so one split can swing the score. Five different splits gave between 76 and 87 percent.
>
> Many clean photos are empty highways, so the model may be learning open road versus a pile of rubbish. The dirty photos appear to come from other countries, not Tuguegarao. And our colour and edge numbers cannot see what is actually in the picture, so a market stall or fallen leaves could be called dirty.

## Slide 8: Lesson and next step (R, about 30 seconds)

Slide: one lesson sentence, and three next steps.

> Our main lesson is that a good score is not the same as a good model. Removing repeats, testing on unseen photos and being honest about weak data matter more than the number.
>
> For Karela, the next step is to collect photos from Tuguegarao with permission, blur faces and plates, use a model that looks at the actual objects, and have a person check the cases it is unsure about. Thank you. We are ready for questions.

(Optional, if the lecturer wants AI use stated aloud: "We used an AI assistant for parts of the code and the drafting. The details are in our report.")

---

## Questions you may be asked

1. **Why not Linear Regression?** Our answer is yes or no. A straight line can give values below 0 or above 1. Logistic regression uses the sigmoid curve to turn a score into a probability between 0 and 1.
2. **Why did you split the data?** To test on photos the model has never seen. Testing on training photos would give an unfairly high score.
3. **What does edge density mean?** The share of pixels that are very different from their neighbours. Rubbish piles have many small objects, so many edges.
4. **Why is 82.6 percent not enough to trust?** The test set has only 46 photos, the clean photos are easy (many are highways), and the photos do not come from Tuguegarao.
5. **What would you do with more time?** Collect and label photos from Tuguegarao, use a model that sees objects, blur faces and plates, and add a human check.
6. **What does the coefficient 2.047 mean?** When edge density goes up by one standard deviation, the log-odds of dirty rise by 2.047, which is about 7.7 times the odds, with the other features held constant.
7. **Why did you remove repeated photos?** If the same photo is in both training and testing, the model is tested on something it has already seen.
8. **Did you use AI?** Yes, and it is in our disclosure. We must still be able to explain every line, so be ready to explain sections 3 and 7 of the notebook.

## Before you present

- [ ] Practise once with a timer, and trim if it runs past 5 minutes.
- [ ] Decide who says which slide. Both of you must speak.
- [ ] Install the Excon font on the computer you present from (see the note in the chat), or export the deck to PDF.
- [ ] Check every number against your report.
