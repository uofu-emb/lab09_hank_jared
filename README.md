# Part 1
## Prelab
[Hank's FSM](hank_fsm_prelab.pdf)\
[Jared's FSM](jared_fsm_prelab.pdf)

## Invariants
1. With your partner, write down a set of invariants your system should have, with a specific emphasis on safety invariants.
1. You should be able to identify specific invariant conditions, that if violated, represent a unsafe condition or safety hazard.
1. Also consider invariants that are assumptions made about the environment or the scenario.
1. Write your invariants in the form a logical predicate, i.e. a statement that must be true.

## Varying invariants
Answer the question: does there exist a sequence of events, such that an invariant is not longer true?

Yes. A **nb_approach** signal can be triggered. After this a **sb_approach** signal can be triggered. Now, after **elapsed** time is at a value of 10 the **lowered** signal will be triggered for the barrier. A **sb_depart** signal then is triggered and **raised** state is triggered. The problem is that **nb_depart** was never triggered and there is still a train on the track. This is a safety hazard.

## Prove it
| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | ringing | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|
| 0      | 0         | 0        | 0                  | 0                  |                |                |              |              |         |               |
| 1      | 0         | 0        | 0                  | 1                  |                |                |              |              |         |               |
| 2      | 0         | 0        | 1                  | 0                  |                |                |              |              |         |               |
| 3      | 0         | 0        | 1                  | 1                  |                |                |              |              |         |               |
| 4      | 0         | 1        | 0                  | 0                  |                |                |              |              |         |               |
| 5      | 0         | 1        | 0                  | 1                  |                |                |              |              |         |               |
| 6      | 0         | 1        | 1                  | 0                  |                |                |              |              |         |               |
| 7      | 0         | 1        | 1                  | 1                  |                |                |              |              |         |               |
| 8      | 1         | 0        | 0                  | 0                  |                |                |              |              |         |               |
| 9      | 1         | 0        | 0                  | 1                  |                |                |              |              |         |               |
| 10     | 1         | 0        | 1                  | 0                  |                |                |              |              |         |               |
| 11     | 1         | 0        | 1                  | 1                  |                |                |              |              |         |               |
| 12     | 1         | 1        | 0                  | 0                  |                |                |              |              |         |               |
| 13     | 1         | 1        | 0                  | 1                  |                |                |              |              |         |               |
| 14     | 1         | 1        | 1                  | 0                  |                |                |              |              |         |               |
| 15     | 1         | 1        | 1                  | 1                  |                |                |              |              |         |               |

| number | invariant |
|--------|-----------|
| 16     |           |