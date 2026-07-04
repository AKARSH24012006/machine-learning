What does SMOTE stand for?
Synthetic Minority Oversampling TEchnique. That's a mouthful, but the key word is "synthetic" — instead of just copy-pasting existing minority examples (like plain oversampling did), SMOTE creates brand new, artificial examples that are similar to, but not identical to, the real ones.
The core idea, in plain terms
Remember plain oversampling's problem: showing the model the exact same 500 fraud cases repeatedly makes it memorize those 500 specific cases rather than learning the general pattern of fraud.
SMOTE's fix: instead of repeating the same fraud examples, invent new, believable fraud examples that sit "between" real ones.
How does it actually create a new example? (the mechanism, in plain language)
Here's the intuition, step by step:

Pick a real minority-class example (say, Fraud Case A).
Look at its "nearest neighbors" — other minority-class examples (other fraud cases) that are most similar to it, based on their measurements/features.
Pick one of those neighbors (say, Fraud Case B).
Create a brand new, synthetic data point that lies somewhere in between Fraud Case A and Fraud Case B — not identical to either one, but a believable blend of the two.

A concrete, simplified analogy
Imagine two real fraud cases described just by one number each — say, "transaction amount":

Fraud Case A: $850
Fraud Case B: $950

Plain oversampling would just copy $850 and $950 over and over.
SMOTE instead says: "These two are neighbors, so let me invent a new synthetic fraud case somewhere between them" — like $891, or $920, or $875. These are new values that never literally appeared in your original data, but they're realistic, since they sit right in the natural range between two real fraud cases.
(Real data has many measurements at once — not just one number like this example — but the same "find a point between two similar real examples" idea applies across all of them simultaneously.)
Why is this better than plain oversampling?
Because now the model isn't staring at the exact same 500 data points repeatedly — it's seeing a much richer, more varied cloud of plausible fraud examples that fill in the gaps between real ones. This makes it much harder for the model to simply "memorize" specific transactions, and pushes it toward learning the actual shape or pattern of what fraud generally looks like in the data — which is exactly what we want.
Simple visual way to think about it
Imagine minority-class points as a few scattered dots on a page. Plain oversampling just makes those same dots "heavier" (stacking copies on top of each other). SMOTE instead draws lines connecting nearby dots and places new dots along those lines — filling in the empty space between real examples, rather than piling more weight onto the exact same spots.
SMOTE's own caveats (it's good, but not magic)

SMOTE assumes that "the space between two similar minority examples" is also a believable, realistic example. This is often true, but not always — sometimes it can create synthetic points that don't actually make real-world sense (like a "blended" fraud case that mixes properties in a way that could never happen in reality).
SMOTE can also occasionally create synthetic points that stray too close to majority-class territory, especially if minority and majority points are heavily mixed together in the data (this causes what's sometimes called class overlap) — making the boundary between classes blurrier, not clearer.
SMOTE is generally considered a solid improvement over plain oversampling, and it's one of the most widely-used imbalance techniques in practice — but it's not a guaranteed fix, and results should always be checked, not assumed.