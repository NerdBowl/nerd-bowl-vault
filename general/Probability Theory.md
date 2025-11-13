
Events
- Experiment: Any action whose outcome is subject to uncertainty.
- Sample space $S$: The set of all outcomes of an experiment.
	- Discrete if there are a finite or countably infinite number of outcomes.
	- Continuous if there is an uncountable number of outcomes.
- Event $A$: collection of outcomes, $A \subseteq S$. 
	- Simple if only one outcome, compound otherwise.
	- We say $A$ occurs, when an outcome belongs to $A$. 
- Two events are **mutually exclusive** if $A \cap B = \emptyset$.
- Events $A_1, A_2, \ldots$ are said to be mutually exclusive if they are pairwise mutually exclusive, i.e., if $A_i \cap A_j = \emptyset$ whenever $i \neq j$.

Probability
- **Axioms of probability**: Let $S$ be a sample space of an experiment. A probability set function is a function that assigns a real value $P(A)$ to every event $A \subseteq S$ and satisfies the following three properties:
	1. $P(A) \ge 0$ for any event $A$
	2. $P(S) = 1$
	3. For any countable collection $A_1, A_2, A_3, \dots$ of mutually exclusive events: $$P\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} P(A_i)$$
- Definition: The **conditional probability** of an event $A$, given the event $B$, is defined by: $$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$
- Two events $A$ and $B$ are **independent** if $P(A \cap B) = P(A) \cdot P(B)$.
- Events $A_1, \dots, A_n$ are mutually independent if for every $k = 2, 3, \dots, n$ and for every subset $\{i_1, \dots, i_k\}$ of $\{1, 2, \dots, n\}$ :$$P\left(\bigcap_{j=1}^{k} A_{i_j}\right) = \prod_{j=1}^{k} P(A_{i_j})$$
