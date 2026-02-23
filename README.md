# Item Search Multiagent Simulator
In this proyect we have developed a simulator with three agents that try to get as much items as possible while avoiding as much traps as possible. This project was done by Raffaele Rizzuti and Carlos Fernández Cabrero.

### Requirements
- Java SE 5 or higherS
- Java Development Kit (JDK)
- Jade


### Extract
First, extract the zip file containing both the java files and the class files.

### Script
If you don't mind about the details of the classes and how to execute, within the extracted files there is a "execution.bat" file. To execute it, open the just-extracted directory and click over it. It assumes that the user has jade in the %CLASSPATH%, otherwise the execution will fail.

This script assumes a dynamic environment with 10 traps, 5 items, uses BFS as search algorithm and with a commitment of 1.

### Detailed Execution
For a detailed execution, or to use alternatives to BFS, the following information explains how the simulator works:

#### Default Simulator parameters
The Simulator class "SimulatorAgent.java" has a series of parameters that can be modified to alter the behaviour of the simulation:

1. StaticDynamic: StaticDynamic has two possible values, 1 (default) or dynamic/random map generation, and 0 or static map geneartion.
2. MapSize: MapSize is a parameter that is only usec when StaticDynamic's value is 1. It it the parameter that sets the size of the randomly generated map. Default value = 10.
3. NumItems: NumItems is a parameter that indicates the amount of items that must be on the map at any time. Its default value is 5.
4. NumTraps: NumTraps is a parameter that indicates the amount of traps that must be on the map at any time. Its default value is 10.
5. NumParticipants: the number of participants that must join the simulation for it to start. The default value is 1, but 2 and 3 are also common values to use multiple agents and compare them. The SimulatorAgent doesn't count for this variable.
6. NumSimRounds: the number of rounds the simulation must do. The default value is 1000.
7. NumStepsMapReDist: the number of rounds that the simulation waits before reorganizing the map. The default value is 10.

#### Default Agent parameters
The three kinds of agent, DFSAgent.java, BfsAgent.java and MyRandomAgent.java, have a parameter "commitment". It is set by default to 1, tho it can be changed to affect the behaviour of the agents. Another common value is 20.

#### Recompilation
If any of the aforementioned parameters is modified, to ensure that the changes are applied over the compiled files:
1. Open a command line in the directory containing the .java files
2. Execute the following command to recompile:
`javac -cp "[path to your jade.jar]" *.java`

#### Execution
For this practice, it is assumed that you have your jade.jar within the %CLASSPATH% environment variable. Afterwards, to execute the project follow the following steps:

1. Open a command line in the directory containing the .java files
2. Execute the following command to use the project:
`java jade.Boot -agents Simulator:SimulatorAgent;NameOfAgent:ClassOfSaidAgent`

Where Simulator is mandatory as it is (because the other agents try to detect it by name). The other agents can have whatever NameOfAgent the user wants. The three ClassOfSaidAgent availables are "DFSAgent", "BfsAgent" and "MyRandomAgent".

Please, remember that in order to use the simulator with multiple agents (without taking into account the simulator) the parameter of SimulatorAgent.java "numParticipants" must be adjusted to the amount of agents you want to use.

Some default executions of the simulator are the following:

`java jade.Boot -agents Simulator:SimulatorAgent;BFS:BfsAgent` (for numParticipants = 1)
`java jade.Boot -agents Simulator:SimulatorAgent;Random:MyRandomAgent;DFS:DFSAgent;BFS:BfsAgent` (for numParticipants = 3)