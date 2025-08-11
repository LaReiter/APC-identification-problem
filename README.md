# Age-Period-Cohort-Identification-Problem---A-visualization

We simulate a climatic signal under different conditions, and different incorporation mechanisms for individual narwhals, and show how the component of age and year becomes unidentifiable.

The simulation experiment is based on real data from 16 narwhals. 

We the use estimated time of birth and death of each individual, and simulate different uptake mechanisms of some (arbitrary) element in the arctic water. This is done under 5 scenarios:

1. Individual narwhals desposit elements in their tusk at a constant rate (independent of age). Climate signal is linearly decreasing.
2. Individual narwhals desposit elements in their tusk at a constant rate (independent of age). Climate signal is linearly increasing.
3. Individual narwhals desposit elements in their tusk at a exponential decreasing fashion as a function of age. Climate signal is linearly increasing.
4. Individual narwhals desposit elements in their tusk at a constant rate (independent of age). Climate signal is periodic.
5. Individual narwhals desposit elements in their tusk at a constant rate (independent of age). Climate signal has a breakpoint and two distinct levels.

To model illness and stress (known to promote higher accumulation of elements in bone structure), we have added gamma noise to the uptake of the individuals. For the climate signal, gaussian noise was added.

Based on these situations (1 through 5), we show the Identification Problem in a Age-Period-Cohort (APC) context: It is hard to distinguish the component of age with the component of (calendar) year. In our simulation, we see that observed signals of situation 3 reflects the age component, whereas the other situations reproduce the envionmental (climate) component.
