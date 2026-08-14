COAL Mini Project (x86 Assembly / Irvine32)

Console-based, menu-driven program written in MASM using the Irvine32 library. Follows the same overall pattern: fixed-size parallel arrays for storage, a linear search for lookups, simple input validation loops and a couple of procedures written specifically to show stack usage (parameter passing / nested calls) since that's usually a COAL requirement.

Smart Traffic System 

Keeps track of traffic junctions and their congestion levels.

Data stored per junction (max 10):

Junction ID
Vehicle count
Congestion level (1 = Low, 2 = Medium, 3 = High)
Emergency vehicle flag (0/1)
Waiting time

Menu options:

Add Junction — rejects duplicate IDs, validates congestion (1–3) and emergency flag (0/1)
Display Junctions (Sorted) — sorts all records by congestion level before printing (bubble sort, swaps all parallel arrays together so records stay consistent)
Search Junction — linear search by ID
Update Congestion — find junction, change its congestion value
Emergency Priority Check — lists every junction currently flagged as having an emergency vehicle, plus a running total of emergency alerts
Average Congestion — integer average across all stored junctions
Show Last 5 Events — a small circular log (size 5) that records the junction ID every time a junction is added or its congestion is updated
Categorize Congestion — buckets all junctions into Low / Medium / High and prints each group
Exit

Implementation notes:

LogEvent writes into a circular buffer (eventHead wraps back to 0 after index 4), so it only ever remembers the most recent 5 add/update events.
AddRecord calls StackDemoOuter, which itself calls StackDemoInner — this is just there to demonstrate a nested procedure call with registers pushed/popped correctly, it doesn't affect program logic.
Sorting and the emergency/average/categorize routines all reuse the same "loop over count using ESI as an index" pattern.# SmartTrafficSystem-COAL
