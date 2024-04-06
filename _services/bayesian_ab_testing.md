---
title: Bayesian A/B <br> Testing
handle: bayesian_ab_testing
icon: book-half
layout: service
header_image: /melt_shared_web_res/images/headers/pins.jpg
blurb: No more p-values, null-hypotheses, type one and type two errors. Junk the confusing language of statistical testing for straightforward probabilities.
status: published
linked_services: [bayesian_modelling, mentoring, training]
clients: [lyst]
display_score: S04
---

### What is Bayesian A/B testing?

Bayesian A/B testing is a statistical method used to compare different versions of a website, app, or product by analyzing data collected from experiments. It differs from classical A/B testing because it is based on a Bayesian interpretation of probability rather than the traditional frequentist interpretation. However, the results we get back from Bayesian A/B testing are a lot more user-friendly. If your organisation is struggling to get to grips with A/B testing then a Bayesian approach may be the answer.


### Why is it better than classical A/B testing?

Three very good reasons:

1. **Clarity**: Frequentist statistics comes with a barrel load of jargon and counterintuitive concepts: p-values, confidence intervals, null hypotheses, power, minimum detectible effect, type one and type two errors. Bayesian statistics by contrast produces something very simple that anyone can understand - the probability that variant A is better than variant B. Even better these probabilities can be transformed directly into the terms of the business decision. For example, the probability that variant A will be more profitable than variant B. This one change cuts through difficulties you might be having in explaining results to the business.
2. **Ease of use**: Bayesian A/B testing allows for so-called "peeking", i.e. seeing how the test is doing - something which is frowned upon (for good reason) in classical A/B testing. This means a test can be stopped early if the results are already good enough to make the call.
3. **Smaller sample sizes**: In some circumstances, we can reduce the sample sizes needed by incorporating prior knowledge or beliefs about the variations being tested.


### How does it work?

In Bayesian A/B testing, prior beliefs about the effectiveness of different variations are represented using probability distributions. As data from the experiment is collected, these prior distributions are updated using Bayes' theorem to obtain posterior distributions which reflect the updated beliefs about the true effectiveness of each variation. These posterior distributions can then be used to make inferences, such as estimating the probability that one variation is better than another or calculating the expected value of different metrics.

### How do we get started?

Whether you are just starting out in A/B testing and are anxious to do it right, or whether you are already down the path of classical A/B testing and are feeling the pain, Coppelia can help you set up Bayesian A/B testing. We have:

- Pre-built notebook templates and python packages to make life easier for your analysts and data scientists 
- A fully mapped out business process for Bayesian A/B testing, with standardised inputs and outputs
- Training and mentoring for data scientists and business stakeholders