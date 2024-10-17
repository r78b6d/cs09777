java c
Project: Energy Hub Planning
1 Brief Introduction
In slides 05-Multi-energy systems_part 1, we learned three modeling and planning methods: Standardized Matrix Modeling of the Energy Hub, Standardized Layered Model for the Energy Hub, and the Energy Bus Model.
Now, we will plan an energy hub from scratch for a building cluster to satisfy its electricity, heat, and cooling demands. We will choose the type of installed device, run the simulated operation, and find an optimal planning result for the energy hub. The optimal planning result should minimize the total annual investment cost and operational cost and satisfy all kinds of constraints throughout the year.
In this project, we will use a multi-energy system simulation platform. to evaluate the performance of your planning results. The website ishttps://7011energyhub.ap.cpolar.io/
It is recommended that you use the Moodle forum to discuss any questions about this project with other students! If necessary, TAs will answer questions on the forum. To promote more public discussions, it is not recommended to directly send emails about your questions to TAs or the teacher.
2 Planning Scenarios and Parameters
2.1 Considered Demand Scenarios
The multi-energy system is modeled by the Energy Bus Model as follows:

To consider users’ various energy demands throughout the year, four typical weeks are selected to represent the demands in four seasons respectively:

You can download the electricity, heat, and cooling load profiles and electricity and gas price profiles from
Moodle. The units for the electricity, heat, and cooling load profiles are all MW. The unit for electricity price is HKD/MWh.
Note that the unit for the gas price profiles is HKD/m3 . If necessary, you can turn it into HKD/MWh by the following equation:
Released energy when burning 1m3  gas = 36000kJ  = 10kWh = 100/1 MWh
2.2 Supply-and-Demand Balance
The users’ energy demand in the t-th hour of the s-th typical week is noted asLs(j),t, where j denotes the type of energy carrier (E.a. electricity, gas, heating, cooling) . The supply-and-demand balance in the Energy Bus Model is formulated as follows:
Is(j),t  + psj,t,gen − psj,t,con   = Ls(j),t − ss(j),t
Is(j),t  is the importing power in the t-th hour of the s-th typical week (The system can import electricity and gas from outside). psj,t,gen  and psj,t,con  represent the total generation and consumption power of devices respectively. If your planned energy hub fails to supply any kind of load at sometime, the shedding load is noted as ss(j),t .
To satisfy users’ demands, the local multi-energy system operator can import electricity and gas from the outside and convert the imported energy into other energy sectors.
2.3 Operation Cost
The operation cost Cop  consists of importing price and shedding load penalty:
Cop  = Cop,elec  + Cop,gas  +  Csℎed
Cop,elec  represents the cost of importing electricity from the grid:

where cs(e),t(l)ec  is the electricity price in the t-th hour of the s-th typical week; Is(e),t(l)ec   is the importing electricity
power.
Similarly, Cop,gas  represents the cost of importing gas:

If your planned energy hub fails to supply any kind of load at sometime, a penalty for shedding load Csℎed  will be added to the total cost:

where M = 10,000,000HKD/MWh, a very high value. In a reasonable energy hub plan, no load should be shed.
2.4 Optional Devices and Investment Cost
You can choose devices from the following table to construct your energy hub. The capacity of one device means the maximum input power for the device.The capacity of each constructed device must bean integer multiple of the base capacity.  For example, if you want to build an internal combustion engine, you can only choose 8MW, 16MW, or other integer multiple of  8MW for its capacity. Choosing 8.5MW for the internal combustion engine is forbidden in this project.
As for storage, the input and output power capacity is the same. The capacity of each constructed storag代 写Project: Energy Hub PlanningPython
代做程序编程语言e must also bean integer multiple of the base capacity. For example, if you want to build a hot water sensible
thermal storage, you can only choose 8MW/40MWh, 16MW/80MWh, or other integer multiple of
8MW/40MWh for its capacity. Choosing 8MW/40MWhas the capacity for the storage means that the maximum input and output power is 8MW and the maximum stored energy is 40MWh.
Some devices have different types such as CHP A or CHP B. The kinds of input and output energy are the same, but they have different technical parameters.
2.4.1 Optional Devices Table

2.4.2 Operation Equations for Each Device CHP, Internal Combustion Engine
These devices have one kind of input energy and two kinds of output energy. We note the input gas power at
the t-th hour of the s-th typical week aspsg,tas  the output electricity aspse,t(lec) , and the output heat power as
psℎ,t(eat) . Then the operation equations for them are:
pse,t(lec)  = ηelecpsg,tas   psℎ,t(eat)  = ηℎeatpsg,tas
where ηelec  and ηℎeat  are the electricity and heating efficiency respectively.
Other Energy Converters
Other energy converters have one kind of input energy and one kind of output energy. The energy conversion equation is:
pso,t(utput)  = ηpsi,t(n)put
Storage
The transition equations for stored energy of each storage is:
Es,t  = Es,t−1  + ps(i),t(n)η − pso,t(ut)/η
where Es,t  is the stored energy at the t-th hour of the s-th typical week; η is the charging and discharging efficiency; ps(i),t(n)  and pso,t(ut)  are the corresponding charging and discharging power for the storage.
To ensure the stored energy does not diminish after the operation of one day, the platform. assumes the storage is in a weekly cycle, namely:
Es,t = 0  = Es,t =168
Note that the stored energy does not need to be consistent between two consecutive typical weeks, namely we do not require Es,t =0  = Es+1,t =0 .
2.4.3 Investment Cost
The total annual investment cost c cap  is calculated as:

where cicap  is the annual investment cost of the i-th device:

where r is the interest rate (In this project, r=4%). yi   is the service lifetime for the i-th device.c(̅)i  is the
input/stored energy capacity of the device. (The explanation of this formulation can be found in
https://en.wikipedia.org/wiki/Present_value)
2.5 Objective Function
The objective function consists of two parts, namely the total annual investment cost and operational cost:

Because only four typical weeks instead of the whole year are considered in the simulated operation, there is a coefficient before the operation cost. In this project, please try your best to minimize this objective function.

3 Procedures for Submitting Your Project
1.     Based on the energy conversion efficiency, cost, service life, and other information of different energy conversion equipment, you need to use the learned knowledge to select equipment and determine
the number of equipment in the energy hub. The planning method is not limited, including programming optimization methods or observing and giving a planning result.
2.    After determining the number of devices and the connection relationship between devices, you should use the simulation platform. to simulate and obtain the results of the simulation run.
3.    After you get the simulation results, your best performance (the minimal value of the objective function in all the projects you have submitted to the platform) will be recorded and used as a  reference when grading.
4.     Finally, write a report based on the overall planning process, and finally upload the report to Moodle.  The report must include how you derived your construction plan, your optimal planning results, and a screenshot showing the simulated operation results. The performance of your planning results
accounts for 50% of the score for the project, and the report accounts for another 50%. There is no format requirement for this report and it needs to be under 5 pages.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
