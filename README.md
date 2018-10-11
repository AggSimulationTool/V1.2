# AggSimulationTool v1.2
The AggSimulationTool has been implemented in Java to evaluate the following data-aggregation solutions: (i) Two-Tier Aggregation for Multi-target Applications (TTAMA); (ii) Data Aggregation for Multiple Groups (DAMiG) Minimum Spanning Tree (DAMiG-MST); (iii) DAMiG Shortest Path Tree (DAMiG-SPT); (iv) DAMiG selecting the parent with highest level of residual energy (DAMiG-MaxEnergy); and (v) Energy Efficient Spanning tRee (EESR).

#RUNNING THE JAR
- Firstly, you have to verify that java is running correctly in your computer.
- Simply, execute in terminal this command: ```java -jar agg.jar```
- In the GUI you can set your simulation.

![alt tag](https://github.com/AggSimulationTool/v1.2/blob/master/GUI1-ScreenShot.png)
![alt tag](https://github.com/AggSimulationTool/v1.2/blob/master/GUI2-ScreenShot.png)


#RUNNING FROM THE SOURCE CODE
## Installation
- This is a Java project that can be imported to Eclipse or Netbeans. To do so, you must follow the default procedure to import a Java project in Eclipse or Netbeans.

## Configuration Files
- The AggSimulationToolv1.2 has some configuration files that contain the basic settings for the simulation.
- These config. files should be stored in the directory named /settingFiles, which is located in the root dir. of the java project.
- The directories inside /settingFiles follow the following name convention: numberOFnodes+'-nodes'. For instance, '/settingFiles/11-nodes' should store the file simulation settings for the simulation of a network having 10 nodes (10 regular nodes).
- Each directory in '/settingFiles/' stores xml files following the name convention: numberOFgroups+'Groups.xml'. For instance, the file '1Groups.xml' stored in the path '/settingFiles/10-nodes/' should contain the setting for simulating a network compoused of 10 nodes and 1 group.
- Example of xml file setting (/settingFile/10-nodes/1Group.xml):

``` <simulation>
<Devices>
<!-- Int  -->
<NumberOfDevices>11</NumberOfDevices>
<!--  Standard Unit  -->
<Range>30</Range>
<!--  Heterogeneous or Homogeneous  -->
<InitialEnergyDistribution>Heterogeneous</InitialEnergyDistribution>
<!-- Amount of energy. Joules -->
<InitialEnergy>0.3</InitialEnergy>
<!-- The initialEnergy value will vary + and - the initialEnergyVariation-->
<InitialEnergyVariation>0</InitialEnergyVariation>
<!-- Connected Random, Grid  -->
<GeographicDistribution>Grid2</GeographicDistribution>
<!--  Distance between nodes -->
<nodesDistance>1</nodesDistance>
<!-- In this version all devices will be equipped with 1 same sensor -->
<!-- Temperature, Humidity, Gas, Water, Energy. -->
<Sensor>Temperature</Sensor>
<!-- kbps -->
<SensorRate>20</SensorRate>
</Devices>
<Gateway>
<!-- This program is not designed to have multiple Gateways. The Gateway is by default the device with index 0.  -->
<!-- Int. This version support only 1  -->
<NumberOfGW>1</NumberOfGW>
<!-- GW location: Corner (default) or center  -->
<GWlocation>Center</GWlocation>
</Gateway>
<MultipleDataRequests>
<!-- The number of DR that will be created -->
<NumberDataRequests>1</NumberDataRequests>
<!--  Subset selects randomly an set according to the size specified in the content -->
<!--  Next versions will implement ID, Data Type, Geographic, Energy Level and Random  -->
<QueriesType>Subset</QueriesType>
<!--  Group Formation algorithm. DFS (Deepth First Search) or square. Square is indicated for grid scenarios. -->
<GroupSelection>Square</GroupSelection>
<!-- Interaction mode between the DRs. This version implements minimize, but max can be implemented -->
<DataRequestOverlapping>Minimize</DataRequestOverlapping>
<!-- The DRs receives a random frequency every run or non-random -->
<DRFrequency>random</DRFrequency>
</MultipleDataRequests>
<InactiveNodes>
<!-- Control Data rate transmitted by inactive nodes. In kbps-->
<controlDataRate>1</controlDataRate>
<!-- Frequency of communication of inactive nodes (nodes that aren't member of any group). In seconds -->
<InactiveNodesFreq>10</InactiveNodesFreq>
</InactiveNodes>

<!--  If the sum of all subset devices is higher than the total number of devices, so there will be overlapping  -->
<DataRequest>
<!--  Char  -->
<DR1-ID>AA</DR1-ID>
<!--  Seconds  -->
<DR1-Frequency>1</DR1-Frequency>
<!--  Seconds  -->
<DR1-DelayTolerance>0.5</DR1-DelayTolerance>
<!--  Max, Min, Avg, Count, Merger  -->
<DR1-AggFunction>Max</DR1-AggFunction>
<DR1-QueryContent>10</DR1-QueryContent>
</DataRequest>
</simulation>
```
- Besides the xml files, it is necessary to set some configurations in the file: /src/code/Run.java.
- Set the number of nodes in the network. This number should be the same used on the xml files:
```
		int netSize=101;//Default size. Netsizes: 32, 64, 128, 256
```
- Set the path variable according to your system:
 ```
 		path = "/Users/user/Documents/Dropbox/EclipseWorkspace/SimulationToolv1.2/";
```
![alt tag](https://github.com/AggSimulationTool/v1.2/blob/master/AggSimulationTool-ScreenShot.png)
