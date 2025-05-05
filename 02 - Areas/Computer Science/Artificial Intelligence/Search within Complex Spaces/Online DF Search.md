- **Online DF-Search** allows for real-time exploration but has inefficiencies in some cases, like revisiting nodes or taking unnecessary paths.
- Using **iterative deepening** helps avoid these inefficiencies by gradually expanding search depth.
- The algorithm relies on **reversible actions** to backtrack and explore other paths.

```c
function ONLINE_DFS-AGENT(s')
//return an action
input: s', a percept identifying current state
static: result, a table initially empty
        unexplored, a table that lists for each visited state, the action not yet tried
        unbacktracked, a table that lists for each visited state, the backtrack not yet tried
        s,a, the previous state and action, initially null
if GOAL-TEST(s') then return stop
if s' is a new state then unexplored[s'] ← ACTIONS(s')
if s is not null then do
    result[a,s] ← s'
    add s to the front of unbackedtracked[s']  //Only if not already in results, to avoid cycling.
if unexplored[s'] is empty then
    if unbacktracked[s'] is empty then return stop
    else a ← an action b such that result[b, s']=POP(unbacktracked[s'])
else a ← POP(unexplored[s'])
s ← s'
return a
```
___
Tags : #ai #programming 