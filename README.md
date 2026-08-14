Smart Traffic System (COAL_OEL_1.asm)

A menu-driven console program that manages traffic junction records using parallel arrays (max 10 junctions), written in x86 assembly with the Irvine32 library.

Data stored per junction: Junction ID, vehicle count, congestion level (1=Low, 2=Medium, 3=High), emergency vehicle flag (0/1), waiting time.

Menu options:

Add Junction — checks for duplicate IDs, validates congestion (1–3) and emergency flag (0/1) before accepting them
Display Junctions (Sorted) — bubble-sorts all records by congestion level (swapping all five parallel arrays together) before printing
Search Junction — linear search by ID
Update Congestion — finds a junction and changes its congestion value
Emergency Priority Check — lists every junction currently flagged for an emergency vehicle, plus a running total
Average Congestion — integer average across all junctions
Show Last 5 Events — a small circular log (size 5) that records the junction ID whenever a junction is added or updated
Categorize Congestion — groups junctions into Low / Medium / High
Exit

Implementation notes:

LogEvent writes into a circular buffer — eventHead wraps back to 0 after index 4, so only the most recent 5 add/update events are kept.
AddRecord calls StackDemoOuter, which calls StackDemoInner, purely to show a nested procedure call with registers pushed and popped correctly. It doesn't change program behavior.
Sorting, emergency check, average, and categorize all reuse the same "loop count times using ESI as the index" pattern.

Requirements: MASM + Irvine32, built as a 32-bit console project, includes Irvine32.inc, ends with END main.

Limitations: max 10 records with no resizing, nothing persists between runs, and ReadInt handles the actual numeric parsing — only the range of values (like congestion 1–3) gets validated by the program.
