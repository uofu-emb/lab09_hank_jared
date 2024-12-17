## Invariants
1. With your partner, write down a set of invariants your system should have, with a specific emphasis on safety invariants.
1. You should be able to identify specific invariant conditions, that if violated, represent a unsafe condition or safety hazard.
1. Also consider invariants that are assumptions made about the environment or the scenario.
1. Write your invariants in the form a logical predicate, i.e. a statement that must be true.

## Varying invariants
Answer the question: does there exist a sequence of events, such that an invariant is not longer true?

Yes. A **nb_approach** signal can be triggered. After this a **sb_approach** signal can be triggered. Now, after **elapsed** time is at a value of 10 the **lowered** signal will be triggered for the barrier. A **sb_depart** signal then is triggered and **raised** state is triggered. The problem is that **nb_depart** was never triggered and there is still a train on the track. This is a safety hazard.