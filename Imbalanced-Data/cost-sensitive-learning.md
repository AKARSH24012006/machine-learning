ost-sensitive learning does neither. You keep the exact same original imbalanced dataset, and you keep the exact same single model. What changes is: you tell the model that certain mistakes are more costly than others.
The core idea
Normally, when a model is learning, it treats all mistakes as equally bad. Getting a fraud case wrong "costs" the same as getting a normal transaction wrong, in the model's eyes — both are just "1 mistake."
But think about it in the real world: are these two mistakes actually equally bad?

False negative — the model says "not fraud" but it actually WAS fraud. Real money gets stolen, undetected.
False positive — the model says "fraud" but it was actually a normal transaction. Mildly annoying (maybe the customer's card gets flagged and they have to verify themselves), but nowhere near as damaging.

In the real world, missing actual fraud is usually way more costly than accidentally flagging a normal transaction. But by default, a standard model doesn't know that — it just tries to minimize the total number of mistakes, treating a missed fraud case and a false alarm as equally bad.
Cost-sensitive learning fixes this by explicitly telling the model: "Getting a minority-class example wrong is X times more costly than getting a majority-class example wrong — so weight your learning accordingly."
How does this actually change what the model does?
Remember, way back, we talked about how a model tries to minimize its overall mistakes across the dataset. Cost-sensitive learning changes the math behind "how bad is this mistake" — instead of every wrong prediction counting as "1 point of badness," you assign different penalty weights per class.
For example, you might say: "a missed fraud case counts as 10 points of badness, but a false fraud alarm only counts as 1 point of badness." Now, even though fraud cases are rare, the model has a very strong incentive to get them right, because messing one up hurts its score 10x more than messing up a normal transaction.
Simple analogy
Imagine a teacher grading a test where getting a safety-critical question wrong (like "what do you do if the fire alarm goes off?") costs you 10 points, but getting a trivia question wrong only costs you 1 point. Even if there are far fewer safety questions on the test than trivia questions, a smart student will make sure to prioritize studying the safety questions carefully, because messing those up hurts their grade way more.
How this is different from oversampling/undersampling (important distinction)

Oversampling/undersampling/SMOTE physically change how much data of each class the model sees.
Cost-sensitive learning doesn't touch the data at all — the model still sees the real, original, imbalanced 99,500/500 split. What changes is purely how much the model is penalized internally when it gets each class wrong.

Some people find cost-sensitive learning more elegant because you're not distorting or duplicating your real-world data at all — you're just being honest with the model about which mistakes actually matter more in the real world.
How does this look in practice (conceptually, before we see code)?
Most ML libraries (like scikit-learn) let you set something called class_weight when building a model. You can either:

Set it to "balanced" — the library automatically calculates weights inversely proportional to how rare each class is (rarer class = automatically weighted higher), or
Manually specify exact weights yourself, like {0: 1, 1: 10} meaning "class 1 mistakes count 10x more than class 0 mistakes."

The catch

You have to actually know (or reasonably estimate) how much worse one type of mistake is compared to the other. Sometimes this is obvious (missing cancer vs a false alarm), but sometimes it's genuinely hard to quantify precisely.
Setting the weight too aggressively can overcorrect — the model might start being too trigger-happy about predicting the minority class everywhere, causing a flood of false alarms.