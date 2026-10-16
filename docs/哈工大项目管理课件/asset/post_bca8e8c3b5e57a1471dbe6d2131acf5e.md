
# SMART Criteria

Milestones should be:
- **Specific**
- **Measurable**
- **Assignable**
- **Realistic**
- **Time-framed**

# Figure 6-7. Sample Tracking Gantt Chart

![](img/1db87b9b55fa1232e052e0dffad9e0c7_211_0.png)

# Critical Path Method (CPM)

- **CPM** is a network diagramming technique used to predict total project duration.
- A **critical path** for a project is the series of activities that determines the *earliest time* by which the project can be completed.
- The critical path is the *longest path* through the network diagram and has the least amount of slack or float.
- **Slack** or **float** is the amount of time an activity can be delayed without delaying a succeeding activity or the project finish date.

# Figure 6-8. Determining the Critical Path for Project X

![](img/1db87b9b55fa1232e052e0dffad9e0c7_214_0.png)

Note: Assume all durations are in days.

- Path 1: A-D-H-J    Length = 1+4+6+3 = 14 days
- Path 2: B-E-H-J    Length = 2+5+6+3 = 16 days
- Path 3: B-F-J      Length = 2+4+3 = 9 days
- Path 4: C-G-I-J    Length = 3+6+2+3 = 14 days

Since the critical path is the longest path through the network diagram, Path 2, B-E-H-J, is the critical path for Project X.

# Using Critical Path Analysis
to Make Schedule Trade-offs

- **Free slack or free float** is the amount of time an activity can be delayed without delaying the early start of any immediately following activities.
- **Total slack or total float** is the amount of time an activity can be delayed from its early start without delaying the planned project finish date.
- A **forward pass** through the network diagram determines the early start and finish dates.
- A **backward pass** determines the late start and finish dates.

# Figure 6-9. Calculating Early and Late Start and Finish Dates

Legend:
ES = early start
EF = early finish
LS = late start
LF = late finish

![](img/1db87b9b55fa1232e052e0dffad9e0c7_217_0.png)

# Table 6-1. Free and Total Float or Slack for Project X

| Task Name | Start | Finish | Late Start | Late Finish | Free Slack | Total Slack |
|---|---|---|---|---|---|---|
| A | 6/1/05 | 6/1/05 | 6/3/05 | 6/3/05 | 0d | 2d |
| B | 6/1/05 | 6/2/05 | 6/1/05 | 6/2/05 | 0d | 0d |
| C | 6/1/05 | 6/3/05 | 6/3/05 | 6/7/05 | 0d | 2d |
| D | 6/2/05 | 6/7/05 | 6/6/05 | 6/9/05 | 2d | 2d |
| E | 6/3/05 | 6/9/05 | 6/3/05 | 6/9/05 | 0d | 0d |
| F | 6/3/05 | 6/8/05 | 6/14/05 | 6/17/05 | 7d | 7d |
| G | 6/6/05 | 6/13/05 | 6/8/05 | 6/15/05 | 0d | 2d |
| H | 6/10/05 | 6/17/05 | 6/10/05 | 6/17/05 | 0d | 0d |
| I | 6/14/05 | 6/15/05 | 6/16/05 | 6/17/05 | 2d | 2d |
| J | 6/20/05 | 6/22/05 | 6/20/05 | 6/22/05 | 0d | 0d |

# Using the Critical Path to Shorten a Project Schedule

- Three main techniques for shortening schedules:
  - **Shortening** the duration of critical activities or tasks by adding more resources or changing their scope.
  - **Crashing** activities by obtaining the greatest amount of schedule compression for the least incremental cost.
  - **Fast tracking** activities by doing them in parallel or overlapping them.

# Many Horror Stories
Related to Project Schedules

- Creating realistic schedules and sticking to them is a key challenge of project management.
- Crashing and fast tracking often cause more problems, resulting in longer schedules.
- Organizational issues often cause schedule problems. See the “What Went Wrong?” example that describes the need to take more time to implement Customer Relationship Management (CRM) software so that users will accept it.

# Importance of Updating
Critical
Path Data

- It is important to update project schedule information to meet time goals for a project.
- The critical path may change as you enter actual start and finish dates.
- If you know the project completion date will slip, negotiate with the project sponsor.
