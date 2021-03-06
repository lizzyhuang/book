## Bayes' Rule

This section introduces how the Bayes' rule is applied to calculating conditional probability, and several real-life examples are demonstrated. Finally, we compare the Bayesian and frequentist definition of probability.

### Conditional Probabilities & Bayes' Rule {#sec:bayes-rule}

Consider Table \@ref(tab:2015gallupDating).
It shows the results of a poll among 1738 adult Americans. This table allows us to calculate probabilities.

\begin{table}

\caption{(\#tab:2015gallupDating)Results from a 2015 Gallup poll on the use of online dating sites by age group}
\centering
\begin{tabular}[t]{lrrrrr}
\toprule
  & 18-29 & 30-49 & 50-64 & 65+ & Total\\
\midrule
Used online dating site & 60 & 86 & 58 & 21 & 225\\
Did not use online dating site & 255 & 426 & 450 & 382 & 1513\\
Total & 316 & 512 & 508 & 403 & 1738\\
\bottomrule
\end{tabular}
\end{table}

For instance, the probability of an adult American using an online dating site can be calculated as
\begin{multline*}
	P(\text{using an online dating site}) = \\
	\frac{\text{Number that indicated they used an online dating site}}{\text{Total number of people in the poll}}
	= \frac{225}{1738} \approx 13\%.
\end{multline*}
This is the overall probability of using an online dating site. Say, we are now interested in the probability of using an online dating site if one falls in the age group 30-49. Similar to the above, we have
\begin{multline*}
	P(\text{using an online dating site} \mid \text{in age group 30-49}) = \\
	\frac{\text{Number in age group 30-49 that indicated they used an online dating site}}{\text{Total number in age group 30-49}}
	= \frac{86}{512} \approx 17\%.
\end{multline*}
Here, the pipe symbol `|' means *conditional on*. This is a *conditional probability* as one can consider it the probability of using an online dating site conditional on being in age group 30-49.

We can rewrite this conditional probability in terms of 'regular' probabilities by dividing both numerator and the denominator by the total number of people in the poll. That is,
\begin{multline*}
	P(\text{using an online dating site} \mid \text{in age group 30-49}) \\
\begin{split}
	&= \frac{\text{Number in age group 30-49 that indicated they used an online dating site}}{\text{Total number in age group 30-49}} \\
	&= \frac{\frac{\text{Number in age group 30-49 that indicated they used an online dating site}}{\text{Total number of people in the poll}}}{\frac{\text{Total number in age group 30-49}}{\text{Total number of people in the poll}}} \\
	&= \frac{P(\text{using an online dating site \& falling in age group 30-49})}{P(\text{Falling in age group 30-49})}.
\end{split}
\end{multline*}
It turns out this relationship holds true for any conditional probability and is known as Bayes' rule:

\BeginKnitrBlock{definition}\iffalse{-91-66-97-121-101-115-39-32-82-117-108-101-93-}\fi{}<div class="definition"><span class="definition" id="def:unnamed-chunk-1"><strong>(\#def:unnamed-chunk-1)  \iffalse (Bayes' Rule) \fi{} </strong></span>The conditional probability of the event $A$ conditional on the event $B$ is given by

\[
  P(A \mid B) = \frac{P(A \,\&\, B)}{P(B)}.
\]</div>\EndKnitrBlock{definition}


\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-2"><strong>(\#exm:unnamed-chunk-2) </strong></span>What is the probability that an 18-29 year old from Table \@ref(tab:2015gallupDating) uses online dating sites?

Note that the question asks a question about 18-29 year olds. Therefore, it conditions on being 18-29 years old.
Bayes' rule provides a way to compute this conditional probability:

\begin{multline*}
	P(\text{using an online dating site} \mid \text{in age group 18-29}) \\
\begin{split}
	&= \frac{P(\text{using an online dating site \& falling in age group 18-29})}{P(\text{Falling in age group 18-29})} \\
	&= \frac{\frac{\text{Number in age group 18-29 that indicated they used an online dating site}}{\text{Total number of people in the poll}}}{\frac{\text{Total number in age group 18-29}}{\text{Total number of people in the poll}}} \\
	&= \frac{\text{Number in age group 18-29 that indicated they used an online dating site}}{\text{Total number in age group 18-29}} = \frac{60}{315} \approx 19\%.
\end{split}
\end{multline*}</div>\EndKnitrBlock{example}

### Bayes' Rule and Diagnostic Testing {#sec:diagnostic-testing}

To better understand conditional probabilities and their importance, let us consider an example involving the human immunodeficiency virus (HIV). In the early 1980s, HIV had just been discovered and was rapidly expanding. There was major concern with the safety of the blood supply. Also, virtually no cure existed making an HIV diagnosis basically a death sentence, in addition to the stigma that was attached to the disease.

These made false positives and false negatives in HIV testing highly undesirable. A *false positive* is when a test returns postive while the truth is negative. That would for instance be that someone without HIV is wrongly diagnosed with HIV, wrongly telling that person they are going to die and casting the stigma on them. A *false negative* is when a test returns negative while the truth is positive. That is when someone with HIV undergoes an HIV test which wrongly comes back negative. The latter poses a threat to the blood supply if that person is about to donate blood.

[comment]: # (The following paragraph could be deleted: The next one does not use false positive/negative rate but rather true positive/negative rate.)

The probability of a false positive if the truth is negative is called the false positive rate. Similarly, the false negative rate is the probability of a false negative if the truth is positive. Note that both these rates are conditional probabilities: The false positive rate of an HIV test is the probability of a positive result *conditional on* the person tested having no HIV.

The HIV test we consider is an enzyme-linked immunosorbent assay, commonly known as an ELISA.
We would like to know the probability that someone (in the early 1980s) has HIV if ELISA tests positive. For this, we need the following information.
ELISA's true positive rate (one minus the false negative rate), also referred to as sensitivity, recall, or probability of detection, is estimated as
\[
  P(\text{ELISA is positive} \mid \text{Person tested has HIV}) = 93\% = 0.93.
\]
Its true negative rate (one minus the false positive rate), also referred to as specificity, is estimated as
\[
  P(\text{ELISA is negative} \mid \text{Person tested has no HIV}) = 99\% = 0.99.
\]
Also relevant to our question is the prevalence of HIV in the overall population, which is estimated to be 1.48 out of every 1000 American adults. We therefore assume
\begin{equation}
  P(\text{Person tested has HIV}) = \frac{1.48}{1000} = 0.00148.
  (\#eq:HIVpositive)
\end{equation}
Note that the above numbers are estimates. For our purposes, however, we will treat them as if they were exact.

Our goal is to compute the probability of HIV if ELISA is positive, that is $P(\text{Person tested has HIV} \mid \text{ELISA is positive})$. In none of the above numbers did we condition on the outcome of ELISA. Fortunately, Bayes' rule allows is to use the above numbers to compute the probability we seek. Bayes' rule states that

$$
  \begin{aligned}
  P(&\text{Person tested has HIV}  \mid \text{ELISA is positive}) \\
   & = \frac{P(\text{Person tested has HIV} \,\&\, \text{ELISA is positive})}{P(\text{ELISA is positive})}.
\end{aligned}  
(\#eq:HIVconditional)
$$

The can be derived as follows. For someone to test positive and be HIV positive, that person first needs to be HIV positive and then seconldy test positive. The probability of the first thing happening is $P(\text{HIV positive}) = 0.00148$. The probability of then testing positive is $P(\text{ELISA is positive} \mid \text{Person tested has HIV}) = 0.93$, the true positive rate. This yields for the numerator

\begin{multline}
  P(\text{Person tested has HIV} \,\&\, \text{ELISA is positive}) \\
  \begin{split}
  &= P(\text{Person tested has HIV}) P(\text{ELISA is positive} \mid \text{Person tested has HIV}) \\
  &= 0.00148 \cdot 0.93
  = 0.0013764.
  \end{split}
  (\#eq:HIVjoint)
\end{multline}

The first step in the above equation is implied by Bayes' rule: By multiplying the left- and right-hand side of Bayes' rule as presented in Section \@ref(sec:bayes-rule) by $P(B)$, we obtain
\[
  P(A \mid B) P(B) = P(A \,\&\, B).
\]

The denominator in \@ref(eq:HIVconditional) can be expanded as

\begin{multline*}
  P(\text{ELISA is positive}) \\
  \begin{split}
  &= P(\text{Person tested has HIV} \,\&\, \text{ELISA is positive}) + P(\text{Person tested has no HIV} \,\&\, \text{ELISA is positive}) \\
  &= 0.0013764 + 0.0099852 = 0.0113616
  \end{split}
\end{multline*}

where we used \@ref(eq:HIVjoint) and

\begin{multline*}
  P(\text{Person tested has no HIV} \,\&\, \text{ELISA is positive}) \\
  \begin{split}
  &= P(\text{Person tested has no HIV}) P(\text{ELISA is positive} \mid \text{Person tested has no HIV}) \\
  &= \left(1 - P(\text{Person tested has HIV})\right) \cdot \left(1 - P(\text{ELISA is negative} \mid \text{Person tested has no HIV})\right) \\
  &= \left(1 - 0.00148\right) \cdot \left(1 - 0.99\right) = 0.0099852.
  \end{split}
\end{multline*}

Putting this all together and inserting into \@ref(eq:HIVconditional) reveals
\begin{equation}
  P(\text{Person tested has HIV} \mid \text{ELISA is positive}) = \frac{0.0013764}{0.0113616} \approx 0.12.
  (\#eq:HIVresult)
\end{equation}
So even when the ELISA returns positive, the probability of having HIV is only 12%. An important reason why this number is so low is due to the prevalence of HIV. Before testing, one's probability of HIV was 0.148%, so the positive test changes that probability dramatically, but it is still below 50%. That is, it is more likely that one is HIV negative rather than positive after one positive ELISA test.

Questions like the one we just answered (What is the probability of a disease if a test returns positive?) are crucial to make medical diagnoses. As we saw, just the true positive and true negative rates of a test do not tell the full story, but also a disease's prevalence plays a role. Bayes' rule is a tool to synthesize such numbers into a more useful probability of having a disease after a test result.

If the an individual is at a higher risk for having HIV than a randomly sampled person from the population considered, how, if at all, would you expect $P(\text{Person tested has HIV} \mid \text{ELISA is positive})$ to change?

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-3"><strong>(\#exm:unnamed-chunk-3) </strong></span>What is the probability that someone who tests positive does not actually have HIV?</div>\EndKnitrBlock{example}

We found in \@ref(eq:HIVresult) that someone who tests positive has a $0.12$ probability of having HIV. That implies that the same person has a $1-0.12=0.88$ probability of not having HIV, despite testing positive.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-4"><strong>(\#exm:unnamed-chunk-4) </strong></span>If the an individual is at a higher risk for having HIV than a randomly sampled person from the population considered, how, if at all, would you expect $P(\text{Person tested has HIV} \mid \text{ELISA is positive})$ to change?</div>\EndKnitrBlock{example}

If the person has a priori a higher risk for HIV and tests positive, then the probability of having HIV must be higher than for someone not at increased risk who also tests positive. Therefore, $P(\text{Person tested has HIV} \mid \text{ELISA is positive}) > 0.12$ where $0.12$ comes from \@ref(eq:HIVresult).

One can derive this mathematically by plugging in a larger number in \@ref(eq:HIVpositive) than 0.00148, as that number represents the prior risk of HIV. Changing the calculations accordingly shows $P(\text{Person tested has HIV} \mid \text{ELISA is positive}) > 0.12$.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-5"><strong>(\#exm:unnamed-chunk-5) </strong></span>If the false positive rate of the test is higher than 1%, how, if at all, would you expect $P(\text{Person tested has HIV} \mid \text{ELISA is positive})$ to change?</div>\EndKnitrBlock{example}

If the false positive rate increases, the probability of a wrong positive result increases. That means that a positive test result is more likely to be wrong and thus less indicative of HIV. Therefore, the probability of HIV after a positive ELISA goes down such that $P(\text{Person tested has HIV} \mid \text{ELISA is positive}) < 0.12$.


### Bayes Updating

In the previous section, we saw that one positive ELISA test yields a probability of having HIV of 12%. To obtain a more convincing probability, one might want to do a second ELISA test after a first one comes up positive. What is the probability of being HIV positive of also the second ELISA test comes back positive?

To solve this problem, we will assume that the correctness of this second test is not influenced by the first ELISA, that is, the tests are independent from each other. This assumption probably does not hold true as it is plausible that if the first test was a false positive, it is more likely that the second one will be one as well. Nonetheless, we stick with the independence assumption for simplicity.

In the last section, we used $P(\text{Person tested has HIV}) = 0.00148$, see \@ref(eq:HIVpositive), to compute the probability of HIV after one positive test. If we repeat those steps but now with $P(\text{Person tested has HIV}) = 0.12$, the probability that a person with one positive test has HIV, we exactly obtain the probability of HIV after two positive tests. Repeating the maths from the previous section, involving Bayes' rule, gives

\begin{multline}
  P(\text{Person tested has HIV} \mid \text{Second ELISA is also positive}) \\
  \begin{split}
  &= \frac{P(\text{Person tested has HIV}) P(\text{Second ELISA is positive} \mid \text{Person tested has HIV})}{P(\text{Second ELISA is also positive})} \\
  &= \frac{0.12 \cdot 0.93}{
  \begin{split}
  &P(\text{Person tested has HIV}) P(\text{Second ELISA is positive} \mid \text{Has HIV}) \\
  &+ P(\text{Person tested has no HIV}) P(\text{Second ELISA is positive} \mid \text{Has no HIV})
  \end{split}
  } \\
  &= \frac{0.1116}{0.12 \cdot 0.93 + (1 - 0.12)\cdot (1 - 0.99)} \approx 0.93.
  \end{split}
  (\#eq:Bayes-updating)
\end{multline}

Since we are considering the same ELISA test, we used the same true positive and true negative rates as in Section \@ref(sec:diagnostic-testing).
We see that two positive tests makes it much more probable for someone to have HIV than when only one test comes up positive.

This process, of using Bayes' rule to update a probability based on an event affecting it, is called Bayes' updating. More generally, the what one tries to update can be considered 'prior' information, sometimes simply called the *prior*. The event providing information about this can also be data. Then, updating this prior using Bayes' rule gives the information conditional on the data, also known as the *posterior*, as in the information *after* having seen the data. Going from the prior to the posterior is Bayes updating.

The probability of HIV after one positive ELISA, 0.12, was the posterior in the previous section as it was an update of the overall prevalence of HIV, \@ref(eq:HIVpositive). However, in this section we answered a question where we used this posterior information as the prior. This process of using a posterior as prior in a new problem is natural in the Bayesian framework of updating knowledge based on the data.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-6"><strong>(\#exm:unnamed-chunk-6) </strong></span>What is the probability that one actually has HIV after testing positive 3 times on the ELISA? Again, assume that all three ELISAs are independent.</div>\EndKnitrBlock{example}

Analogous to what we did in this section, we can use Bayes' updating for this. However, now the prior is the probability of HIV after two positive ELISAs, that is $P(\text{Person tested has HIV}) = 0.93$. Analogous to \@ref(eq:Bayes-updating), the answer follows as

\begin{multline}
  P(\text{Person tested has HIV} \mid \text{Third ELISA is also positive}) \\
  \begin{split}
  &= \frac{P(\text{Person tested has HIV}) P(\text{Third ELISA is positive} \mid \text{Person tested has HIV})}{P(\text{Third ELISA is also positive})} \\
  &= \frac{0.93 \cdot 0.93}{\begin{split}
  &P(\text{Person tested has HIV}) P(\text{Third ELISA is positive} \mid \text{Has HIV}) \\
  + &P(\text{Person tested has no HIV}) P(\text{Third ELISA is positive} \mid \text{Has no HIV})
  \end{split}} \\
  &= \frac{0.8649}{0.93 \cdot 0.93 + (1 - 0.93)\cdot (1 - 0.99)} \approx 0.999.
  \end{split}
\end{multline}


### Bayesian vs. Frequentist Definitions of Probability

The frequentist definition of probability is based on observation of a large number of trials. The probability for an event $E$ to occur is $P(E)$, and assume we get $n_E$ successes out of $n$ trials. Then we have
\begin{equation}
P(E) = \lim_{n \rightarrow \infty} \dfrac{n_E}{n}.
\end{equation}

On the other hand, the Bayesian definition of probability $P(E)$ reflects our prior beliefs, so $P(E)$ can be any probability distribution, provided that it is consistent with all of our beliefs. (For example, we cannot believe that the probability of a coin landing heads is 0.7 and that the probability of getting tails is 0.8, because they are inconsistent.)

The two definitions result in different methods of inference. Using the frequentist approach, we describe the confidence level as the proportion of random samples from the same population that produced confidence intervals which contain the true population parameter. For example, if we generated 100 random samples from the population, and 95 of the samples contain the true parameter, then the confidence level is 95%. Note that each sample either contains the true parameter or does not, so the confidence level is NOT the probability that a given interval includes the true population parameter.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-7"><strong>(\#exm:unnamed-chunk-7) </strong></span>Based on a 2015 Pew Research poll on 1,500 adults: "We are 95% confident that 60% to 64% of Americans think the federal government does not do enough for middle class people.</div>\EndKnitrBlock{example}

The correct interpretation is: 95% of random samples of 1,500 adults will produce
confidence intervals that contain the true proportion of Americans who think the federal government does not do enough for middle class people.

Here are two common misconceptions:

* There is a 95% chance that this confidence interval includes the true population proportion.

* The true population proportion is in this interval 95% of the time.

The probability that a given confidence interval captures the true parameter is either zero or one. To a frequentist, the problem is that one never knows whether a specific interval contains the true value with probability zero or one.  So a frequentist says that "95% of similarly constructed intervals contain the true value".

The second (incorrect) statement sounds like the true proportion is a value that moves around that is sometimes in the given interval and sometimes not in it. Actually the true proportion is constant, it's the various intervals constructed based on new samples that are different.

The Bayesian alternative is the credible interval, which has a definition that is easier to interpret. Since a Bayesian is allowed to express uncertainty in terms of probability, a Bayesian credible interval is a range for which the Bayesian thinks that the probability of including the true value is, say, 0.95.  Thus a Bayesian can say that there is a 95% chance that the credible interval contains the true parameter value.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:unnamed-chunk-8"><strong>(\#exm:unnamed-chunk-8) </strong></span>The posterior distribution yields a 95% credible interval of 60% to 64% for the proportion of Americans who think the federal government does not do enough for middle class people.</div>\EndKnitrBlock{example}


We can say that there is a 95% probability that the proportion is between 60% and 64% because this is a **credible** interval, and more details will be introduced later in the course.
