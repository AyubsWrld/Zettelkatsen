**Learning Real-Time A*** (**LRTA***) is an **online search algorithm** that incrementally improves its heuristic estimates while exploring an unknown environment, making real-time decisions by updating the heuristic values of visited states to guide future moves more efficiently.

```c
function LRTA*-AGENT(s')
//returns an action
input: s', a percept identifying current state
static: result, a table indexed by action and state, initially empty
        H, a table of cost estimates indexed by state, initially empty
        s,a, the previous state and action, initially null
if GOAL-TEST(s') then return stop
if s' is a new state (not in H) then H[s'] ← h(s')
unless s is null
    result[a,s] ← s'
    H[s] ← MIN_LRTA*-COST(s,b,result[b,s],H)
           b ∈ ACTIONS(s)
a ← an action b in ACTIONS(s') that minimizes LRTA*-COST(s',b,result[b,s'],H)
s ← s'
return a
```

___
Tags : #ai #programming 