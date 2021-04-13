## Avoid These Mistakes While Training Your AI

If you want your artificial intelligence (AI) system to perform better, you ought to teach it better, and how do you verify if you have trained it well? By testing it better!

A sophisticated AI system usually follows a 2 stage learning mechanism, whereas a simple AI system may have only one formative stage. The 2 stages in which AI learns are:

- Training
- Feedback

Meticulous teaching is the fundamental requirement for having an excellent performance consistently. However, there are a few mistakes to which traditional (and contemporary) data analytics or statistical methods are susceptible. Collective calling for such an issue is often known as garbage in, garbage out.

---

## Avoid These Mistakes

### 1. Not Having Enough Data to Train

How much data does one need to train an AI system effectively? Well, it depends!

You may want to use standard sampling methods in the collection of required data and may wish to use standard sample size calculators as used in standard statistical analysis tools. However, due to the nature of machine learning algorithms, the amount of data is often insufficient. You would most likely need more than what a standard sample size calculation formula tells you.

You may also use your domain expertise to reasonably assess how much data is enough to exhibit a full cycle of your business problem. It should cover all the possible seasonality and variations.

![lessdata.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1618036600945/LDq3ODMLO.jpeg)

If you feel that the data is not enough, which may be a rare scenario in the current Big Data world, don't rush and wait until you get enough of it.

### 2. Not Cleaning and Validating the Dataset

Too much data is of no use if it is of poor quality. It could mean one or more of the following three things:

#### - Data Has Noise

There is too much conflicting and misleading information. Confounding variables or parameters are present, and the essential variables are missing. Cleaning this type of data needs additional data points because the current set is unusable and hence not enough.

#### - It is Dirty Data

Several values are missing, or the data has inconsistencies, errors, and a mix of numerical or categorical values in the same column. This type of data needs careful manual cleaning by subject matter experts and may often need re-validation. Depending on resource availability, you may find it easier to obtain additional data instead of cleaning dirty data.

#### - Inadequate or Spare Data

This is a scenario where a few data points have actual values, and a significant part of the dataset if full of nulls or zeros. The type of issues present within the dataset is often not clear from the dataset itself, which is why it is recommended to do exploratory analysis and visualisation to be applied at the outset.

Doing this first not only gives you a level of confidence in data quality but also tells you if there is something amiss.

![validated.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1618036626771/x9Xexyuq8.jpeg)

The validation of the dataset is essential to proceed and you should never miss it.

### 3. Not Having Enough Spread in Data

Having a large amount of data is not always a good thing unless it can represent all the possible use cases or scenarios. If the data is missing variety, it can lead to problems in future - you increase the chances of losing on low-frequency high-risk scenarios.

![spreaddata.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618036647321/v-3Ty32JR.png)

Since Machine Learning is an inductive process, your base model can only cover what it has seen in the data. So, if you miss on edge cases, these will not be supported by your model. It merely means your AI will fail when that scenario occurs. This is the only and the most crucial reason why your training data should have enough spread to represent the real population.

### 4. Ignoring Near-Misses and Overrides

During initial training, it is hard to identify near-misses and disregarded data points. However, in a continuous learning loop with feedback, it becomes highly essential to pay close attention to near-misses and human or machine overrides.

If the model has missed to correctly predict or calculate any output just by a bit and thereby the decision has changed, it would be a near miss.

The same applies when a human operator is supervising the AI systems' output and can decide to override it. You must treat human operator override as a special-case scenario, and feed it back to the training model.

![nearmiss.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1618036673271/ZgldlPCjj.jpeg)

Each of these scenarios either highlights inadequacies in the base model or provides new situations that never existed before. Ignoring overrides can degrade the model performances over time.

### 5. Conflating Correlation and Causation

In statistics, we often say, "Correlation does not imply Causation". It usually refers to the inability to legitimately deduce a cause and effect relationship between input and output. The resulting conclusion still may not be incorrect or false, but the failure to establish this relationship is often an indicator of the lurking problem.

Determining causality based on correlation can be very tricky and can potentially lead to contradictory conclusions. It would be much better to be able to prove that there truly is a causal relationship.

![causalcorr.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618036698368/DNeAyQv_0.png)

During initial training and model building, soon after you find a correlation, don't conclude too quickly. Take time to find other underlying factors, find hidden factors, and verify if these are correct and then only conclude.

---

## What is Happening?

As technology is improving day by day, it is placing powerful tools in the hands of people who do not understand how these work. It is creating significant business as well as societal risks.

Developers and data scientists are increasingly getting detached from an understanding of the intricacies of the tools they are using and the systems they're creating.

The AI system means a black box is, becoming a commonly accepted rhetoric, and the only sure-fire way to trust this black box is - training it meticulously and testing it rigorously!

---

Well, that's it from me!

It was an excerpt from an awesome article by **Anand Tamboli** in *OSFY November 2020 Edition*.

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Need inspiration or a different perspective on the Python projects or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏