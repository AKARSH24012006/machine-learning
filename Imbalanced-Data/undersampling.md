What is undersampling?
Going back to the fraud example: 99,500 normal transactions, 500 fraud transactions.
Undersampling means: throw away some of the majority class data until both classes are roughly equal in size.
So instead of training on all 99,500 normal + 500 fraud, you might randomly pick just 500 normal transactions (out of the 99,500) and keep all 500 fraud ones. Now your training data is 500 normal + 500 fraud — perfectly balanced, 50/50.
Why would this help?
Remember the core problem: the model was ignoring fraud because it was such a tiny sliver of the data, so ignoring it barely hurt its overall score. If you shrink the majority class down to match the minority class, the model can no longer "cheat" by ignoring the minority — both classes now matter equally to its overall accuracy, so it's forced to actually learn what distinguishes them.
Simple analogy
Imagine you're trying to teach someone to tell apart pictures of cats and dogs, but you show them 995 cat photos and only 5 dog photos. They'll get really good at recognizing cats, and basically never learn what a dog looks like, because dogs are such a rare blip in their training. If instead you show them 5 cat photos and 5 dog photos, they're forced to pay real attention to what makes each one distinct.
The catch (and it's a real one)
Undersampling has an obvious downside: you're throwing away data. In our example, you went from having 99,500 normal transaction examples down to just 500. That's a massive amount of potentially useful information thrown in the trash. If those discarded normal transactions contained important patterns (like rare-but-legitimate spending behaviors that could easily be confused with fraud), the model never gets to see them, and it might now make more mistakes on the majority class than it used to.
This is the fundamental tradeoff of undersampling: you fix the imbalance, but you also shrink and potentially cripple your overall dataset — especially painful when your total dataset isn't huge to begin with.
When is undersampling actually a good idea?

When you have a genuinely huge amount of majority-class data — so much that even after undersampling, you still have plenty left to learn from (e.g., millions of normal transactions — throwing away most of them still leaves plenty).
When training time/computational cost is a real constraint, since a smaller dataset trains faster.

When is it a bad idea?

When your dataset is small to begin with (like our earlier Iris example, only 150 rows total) — undersampling could leave you with barely any data to train on at all.