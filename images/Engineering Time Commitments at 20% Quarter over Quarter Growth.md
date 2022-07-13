# Predicting Operations Workload Increase

The following thought experiment attempts to show what can happen to an SRE team experiencing rapid growth of their service, but putting no effort into operational improvements / toil reduction.

## Assumptions

1. No staff turnover – nobody joins, nobody leaves. This is for simplicity.
2. No effort is undertaken to reduce toil / improve operational workload at any point. This is a core part of the thought experiment.
3. Work can be viewed as belonging to three distinct categories:
   * Operational work which does not scale up with service growth (remains _static_ with regards to it).
   * Operational work that scales _linearly_ with service growth.
      This is the type of work where toil reduction opportunities appear, as one of the attribute of toil from [Google's definition of it](https://sre.google/sre-book/eliminating-toil/) is that it scales (at least) linearly with service growth.
   * Development work with zero impact on operational efficiency (which follows from second assumption).

## Calculation

Assuming initial system size in the first quarter of the first year (Y1Q1) is 1.0 with a quarter over quarter growth of 20% and an initial split of Ops (static), Ops (linear) and Dev work of 5%, 35% and 60% respectively, we can calculate that:
1. "Static" operational work will remain 5% of the total workload, since by definition it's independent of system size.
2. Linearly scaling operational work will experience a 20% quarter over growth rate matching the overall system growth.
3. Development work will keep shrinking to fill out the remaining available engineering time, since keeping the service operational takes priority over developing new features and no additional staff has been hired per initial assumptions.

This can be represented in the form of a table:

|              | Y1Q1 | Y1Q2 | Y1Q3 | Y1Q4 | Y2Q1 | Y2Q2 |
| ------------ | ---- | ---- | ---- | ---- | ---- | ---- |
| System Size  | 1.00 | 1.20 | 1.44 | 1.73 | 2.07 | 2.49 |
| Ops (static) | 5%   | 5%   | 5%   | 5%   | 5%   | 5%   |
| Ops (linear) | 35%  | 42%  | 50%  | 60%  | 73%  | 87%  |
| Dev          | 60%  | 53%  | 45%  | 35%  | 22%  | 8%   |

Which in turn becomes this chart:

![Engineering Time Commitments at 20% Quarter over Quarter Growth](Engineering%20Time%20Commitments%20at%2020%25%20Quarter%20over%20Quarter%20Growth.png)
