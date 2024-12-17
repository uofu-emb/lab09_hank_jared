# Part 1
## Prelab
[Hank's FSM](hank_fsm_prelab.pdf)\
[Jared's FSM](jared_fsm_prelab.pdf)

# Part 2
## Invariants
1. System must have power at all times.
1. Trains can only go in one direction.
1. Only one train per track
1. Alarm must be on 10 seconds before barrier is lowered until 10 seconds after it is raised and always when a train is present
1. Alarm must be off otherwise
1. An arrival event must happen before a depature event.
1. Barrier must be down while train is present.

## Varying invariants
Answer the question: does there exist a sequence of events, such that an invariant is not longer true?

Yes. A **nb_approach** signal can be triggered. After this a **sb_approach** signal can be triggered. Now, after **elapsed** time is at a value of 10 the **lowered** signal will be triggered for the barrier. A **sb_depart** signal then is triggered and **raised** state is triggered. The problem is that **nb_depart** was never triggered and there is still a train on the track. This is a safety hazard.

## Prove it
[Updated FSM](updated_fsm.pdf)\
| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | ringing | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|
| 0      | 0         | 0        | 0                  | 0                  |        6       |         5      |    21        |    21        |    20   |               |
| 1      | 0         | 0        | 0                  | 1                  |                |                |              |              |         |       19      |
| 2      | 0         | 0        | 1                  | 0                  |                |                |              |              |         |       19      |
| 3      | 0         | 0        | 1                  | 1                  |                |                |              |              |         |       19      |
| 4      | 0         | 1        | 0                  | 0                  |       6        |          5     |      21      |      21      |   20    |               |
| 5      | 0         | 1        | 0                  | 1                  |                |                |              |              |         |       22      |
| 6      | 0         | 1        | 1                  | 0                  |                |                |              |              |         |       22      |
| 7      | 0         | 1        | 1                  | 1                  |                |                |              |              |         |       22      |
| 8      | 1         | 0        | 0                  | 0                  |                |                |              |              |         |       19      |
| 9      | 1         | 0        | 0                  | 1                  |                |                |              |              |         |       19      |
| 10     | 1         | 0        | 1                  | 0                  |                |                |              |              |         |       19      |
| 11     | 1         | 0        | 1                  | 1                  |                |                |              |              |         |        19     |
| 12     | 1         | 1        | 0                  | 0                  |                |                |              |              |         |      21/22    |
| 13     | 1         | 1        | 0                  | 1                  |        13      |        18      |      21      |       12     |         |               |
| 14     | 1         | 1        | 1                  | 0                  |        18      |        14      |      12      |       21     |         |               |
| 15     | 1         | 1        | 1                  | 1                  |        18      |        18      |      13      |       14     |         |               |

| number |     invariant     |
|--------|-------------------|
| 16     |       power       |
| 17     | single direction  |
| 18     | one train / track |
| 19     |     alarm on      |
| 20     |     alarm off     |
| 21     |  arrival bf dept  |
| 22     | barrier           |

## Reflection
No. Our FSM needed to be modified. Neither orginal FSM accounted for a train already being present. We modified a correct version to include this.