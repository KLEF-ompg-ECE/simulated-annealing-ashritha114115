# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** _________Y.ASHRITHA VATHSALA__________________  
**Student ID    :** __________2310040114_________________  
**Date Submitted:** ___________16/3/2026________________  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
The count_clashes() function measures how many exam conflicts occur in the timetable. 
A clash happens when students have two exams scheduled in the same time slot. 
A perfect timetable has 0 clashes, meaning no student has overlapping exams.
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
The generate_neighbor() function creates a slightly modified version of the current timetable. 
It usually changes the time slot of one subject randomly. 
This small change allows the algorithm to explore new timetable possibilities while keeping most of the schedule the same.
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
The condition checks whether the new solution should be accepted or rejected. 
If the new timetable has fewer clashes (better solution), it is always accepted. 
If it is worse, Simulated Annealing may still accept it with a certain probability to avoid getting stuck in local optimal solutions.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379 |
| Clashes at iteration 1 |12 |
| Final best clashes | 3|
| Did SA reach 0 clashes? (Yes / No) |No |

**Copy the printed timetable output here:**
```
[ PASTE TIMETABLE OUTPUT HERE ]
Final Timetable
------------------------------------------
Slot 1: Geography
Slot 2: Chemistry, English
Slot 3: History, Computer Science, Economics
Slot 4: Biology, Statistics
Slot 5: Mathematics, Physics
------------------------------------------
Total clashes : 3
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
The graph shows that the number of clashes decreases rapidly during the early iterations. 
Most of the improvement happens in the first few hundred iterations as the algorithm explores better timetables. 
After reaching around 3 clashes, the curve flattens, indicating that the algorithm stabilizes and finds a near-optimal timetable.
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |   8           |      1379            |     NO               |
| 0.95        |   3           |      1379            |      NO                 |
| 0.995       |   3           |      1379           |        NO               |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
When the cooling rate is very low (0.80), the temperature decreases quickly and the algorithm stops exploring early. This results in a poorer solution with more clashes. 
With a moderate cooling rate (0.95), the algorithm explores longer and finds a better timetable with fewer clashes. 
With a very slow cooling rate (0.995), the search process is more gradual, allowing the algorithm to explore more solutions and reach a stable result similar to the baseline.
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
The cooling rates 0.95 and 0.995 gave the best results with 3 final clashes. 
A slower cooling rate allows the algorithm to explore more possible timetables before settling on a final solution. 
This improves the chances of finding a better schedule with fewer clashes.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3 | The algorithm gradually reduces clashes and converges to a near-optimal timetable.|
| 2 — Cooling rate | cooling_rate = 0.95|3 |Moderate cooling allows better exploration and produces good results. |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
From these experiments, I learned that the cooling rate plays an important role in the performance of the Simulated Annealing algorithm. If the cooling rate is too fast, the algorithm stops exploring early and may produce poor solutions. A slower cooling rate allows the algorithm to explore more possible solutions and improve the timetable gradually. Simulated Annealing is useful for solving optimization problems because it can escape local optimal solutions and search for better results.
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
