# Chapter 3 - Probability

## Outcome
- **Definition:** A possible result of a random experiment.

## Sample Space (S)
- **Definition:** The set of all possible outcomes of a random experiment.
- **Notation:** $$ S \text{ or } \Omega $$

## Event (E)
- **Definition:** A subset of the sample space. Any collection of outcomes.
- **Notation:** $$ E \subset S $$

## Probability Axioms
1. **Non-negativity:** $$ P(E) \geq 0 $$ for any event $$ E $$.
2. **Additivity:** If $$ E_1, E_2, \ldots $$ are disjoint events, then $$ P\left(\bigcup_{i=1}^{\infty} E_i\right) = \sum_{i=1}^{\infty} P(E_i) $$.
3. **Normalization:** $$ P(S) = 1 $$, where $$ S $$ is the sample space.

## Probability as Sets, Booleans
- **Intersection (AND):** $$ P(A \cap B) $$ is the probability of both events A and B occurring.
- **Union (OR):** $$ P(A \cup B) $$ is the probability of either event A or B occurring.
- **Complement (NOT):** $$ P(A^C) $$ is the probability of event A not occurring.

## Disjoint Events
- **Definition:** Events that cannot occur simultaneously.
- **Notation:** $$ A \cap B = \emptyset $$
- **Property:** For disjoint events $$ A $$ and $$ B $$, $$ P(A \cup B) = P(A) + P(B) $$.

## Computing Probability Using Complement
- **Formula:** $$ P(A^C) = 1 - P(A) $$
- **Usage:** Useful when it's easier to calculate the probability of the complement event.

## Computing Probability Using Union
- **Formula for Two Events:** $$ P(A \cup B) = P(A) + P(B) - P(A \cap B) $$

## Conditional Probability
- **Definition:** The probability of event A given that event B has occurred.
- **Formula:** $$ P(A|B) = \frac{P(A \cap B)}{P(B)} $$, provided that $$ P(B) > 0 $$.

## Bayes Rule
- **Formula:** $$ P(A|B) = \frac{P(B|A)P(A)}{P(B)} $$
- **Application:** Allows us to update the probability estimate for A in light of the evidence B.

## Law of Total Probability
- Considering a partition of S into $$ B_1, B_2, \ldots, B_n $$ and any event A:
- **Formula:** $$ P(A) = \sum_{i=1}^{n} P(A|B_i)P(B_i) $$

## Independence
- **Definition:** Two events A and B are independent if the occurrence of A does not affect the probability of B, and vice versa.
- **Condition:** $$ P(A \cap B) = P(A)P(B) $$
- **Implication:** $$ P(A|B) = P(A) $$ and $$ P(B|A) = P(B) $$
