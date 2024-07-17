# ZOE to ILP reduction

## An introduction
The reduction of zero one equations to an integer linear programming problem can be done by converting the ZOE problem into a standard ILP form by adding some constraints.
In essence, ZOEs are ILP problems in disguise. \
All they need are integer constraints for each variable to be 0 or 1 and every equation can be split into two inequalities that when combined, generates an equation. \
For example, if we have $x_1 + x_2 = 1$, we can write it as a combination of inequalities as $x_1 + x_2 \le 1$ and $x_1 + x_2 > 1$.

### The Heuristic

ZOE and ILP problems are known to be NP hard because the solution space in the discrete integers is not convex. This means that there exists no algorithm that can solve all ILPs (or ZOEs) in polynomial time. That is to say no solution exists (yet) that is  better than simply brute forcing through all possibilities. \
One way to narrow down some of the possibilities is to split independent equations into groups and solving within each group.

This group independence can be calculated in polynomial time by first splitting each into a group of its own. Then we merge those groups with at least one variable in common.

-----

## Usage and output

The two .csv files correspond to situations where a solution exists and where the solution does not exist. When it doesn't, it means that we went through all possible variable assignments and none of the combinations satisfied the given set of equations.

To run the program you'd need python along with numpy and pandas installed. With the terminal active in the folder with these files, type in 
```console
python ZOE_to_ILP.py zoe_example.csv
```
and an output_file.txt shall be created. In it, the ZOE would be first represented as an ILP in the standard matrix vector format ($Ax=b$). Then, each group is printed as ZOEs with its corresponding solution. Lastly, the overall solution is merged and shown.

In case no solution exists, the standard format is shown along with the groupings (if any) and lastly a messege saying "For this ZOE no solution exists"

The .csv files can be modified by the user. In case the input format has errors (such as a float number instead of an integer or even a character, etc.) an error messege will be printed with the exact issue shown in the terminal.