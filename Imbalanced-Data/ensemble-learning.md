You've actually already used an ensemble model without maybe realizing the general concept — Random Forest! A Random Forest isn't one decision tree, it's many trees voting together. That's the core idea of ensemble learning: combine multiple models together, and let them vote/average, rather than relying on just one model's opinion.
The general intuition: one model might make mistakes based on quirks it happened to learn, but if you combine many different models, their individual mistakes tend to cancel out, while the patterns they agree on tend to be genuinely real. Like asking 10 doctors for a diagnosis instead of just 1 — you're less likely to be misled by one doctor's individual blind spot.
So how does this specifically help with imbalanced data?
Here's the key idea: instead of changing the data (like undersampling/oversampling/SMOTE did), you can change how you build and combine models, so that the ensemble as a whole becomes more sensitive to the minority class.
There are two popular ways this gets done:
1. Balanced bagging (a twist on Random Forest's approach)
Normally, in a Random Forest, each individual tree is trained on a random sample of the full (imbalanced) dataset — meaning each tree still sees mostly majority-class examples, same imbalance problem as before, just repeated across many trees.
Balanced bagging changes this: each individual tree gets trained on a balanced random sample instead — meaning for every tree, you deliberately undersample the majority class down to match the minority class for that specific tree's training data.
So imagine building 100 trees. Each one of those 100 trees sees a different random 500 normal + 500 fraud sample (roughly balanced), rather than all seeing the same skewed 99,500/500 mix.
Why is this smarter than plain undersampling? Because with plain undersampling, you throw away most of the majority class once, permanently, and every part of your process only ever sees that one reduced dataset. With balanced bagging, each tree gets its own random undersampled subset — so across all 100 trees, you've actually touched a huge variety of different majority-class examples collectively, even though each individual tree only saw a small slice. You get the "forced balance" benefit of undersampling, without permanently discarding most of your majority data from the process as a whole.
2. Boosting-based approaches (like AdaBoost variants adapted for imbalance)
Boosting is a different ensemble style: instead of training many trees independently and averaging their votes (like Random Forest does), boosting trains models one after another, in sequence, where each new model specifically focuses on fixing the mistakes of the previous ones.
For imbalanced data, this naturally helps a bit even in its plain form: if early models keep getting minority-class examples wrong (because they're rare and easy to overlook), boosting's mechanism automatically gives more weight/attention to those specific mistaken examples in the next round — forcing subsequent models to pay closer attention specifically to the cases that keep getting misclassified, which very often are the minority-class examples.
There are also specialized versions built specifically for imbalance (like RUSBoost, which combines random undersampling with boosting) — but the core intuition is the same: sequentially correct for whichever mistakes are being made, and minority-class mistakes tend to get prioritized naturally because they're the ones that keep tripping the model up.
Why is this approach appealing compared to undersampling/oversampling/SMOTE?

You don't have to permanently alter or throw away your original dataset.
You get the diversity benefit of ensembles (many models catching each other's blind spots).
Techniques like balanced bagging combine the benefit of undersampling (forcing balance) while minimizing its downside (permanently losing data), since different trees see different undersampled subsets.

The catch

More computationally expensive — you're training many models instead of one.
Still not a guaranteed fix — if the minority class is extremely rare or the classes are very hard to distinguish, ensembles help but don't work miracles.