# Nasscom-Soc-design-planning Workshop (December 11-December 24)

# Day - 1 (inception of open source EDA, openlane and SKY130PDK)

This repository houses materials, resources, and examples from the Digital VLSI System-on-Chip (SoC) Design and Implementation Workshop. The workshop is designed to familiarize participants with the principles of digital VLSI circuit design, as well as the key stages of SoC development, including architecture, simulation, and real-world implementation. Emphasis is placed on hands-on learning and industry-relevant techniques for creating high-performance SoCs.  

Here are the steps to invoke openlane software in terminal

```
cd ~/Desptop/work/tools 
ls -ltr
cd openlane_working_dir
ls -ltr
cd openlane
ls -ltr
docker
```
![start 1](https://github.com/user-attachments/assets/159afd16-021a-4412-8ad5-20838fac99d1) 

```
./flow.tcl -interactive
```
To get require package 
```
package require openlane 0.9
```
To prepare design 
```
prep -design picorv32a
```

![start 2](https://github.com/user-attachments/assets/80bd4038-f671-4612-a1ee-743ffd3bfcf8)  
![start 4](https://github.com/user-attachments/assets/7f5212c8-818a-4093-b27a-5f9c63d283c0) 

calculation of Flop Ratio 

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```

![ff count 1](https://github.com/user-attachments/assets/2c0fc8c6-6ba7-4515-a644-bf27a5ebd150)

![ff count 2](https://github.com/user-attachments/assets/1f42b0c8-c09c-49c2-ab21-885e08ccead0)


By observing the stat report = The no.of D flip-flops are 1613  & The Total no.of cells in  the current folder is 14876, hence flop ratio becomes
  
```math
Flop\ Ratio = \frac{1613}{14876} = 0.1084
```
To find the percentage 
 = 0.1084 x 100 = 10.84%

#
# Day - 2 (Good floorplan Vs Bad floorplan and introduction to library cells)

- Utilization Factor 
The effectiveness of space utilization within the chip's core is gauged by the Utilization Factor (U.F.). It is the proportion between the area of the core (the designated functional area on the chip) and the area occupied by the netlist (logical design components like gates, flip-flops, etc.). More efficient use of the given core space is indicated by a greater utilization factor. 
- formula 
```math
utilization\ factor = \frac{area\ occupied\ by\ netlist}{total\ area\ of\ the\ core}
```
- Apect Ratio The die's height (length) divided by its breadth is known as the aspect ratio. It can influence component placement and routing and offers information about the chip die's shape.
- formula
```math
Aspect\ Ratio = \frac{height\ the\ core}{width\ of\ the\ core}
``` 
```
run_floorplan
```
![run floor plan](https://github.com/user-attachments/assets/6a42050b-8beb-4d54-ad8a-58752011b312)

```
ls -ltr
cd design
cd picorv32a
ls -ltr
cd runs
ls -ltr
```
![floor plan](https://github.com/user-attachments/assets/93f50d73-de7b-4e67-b16d-eda4eb528d2f)

Layout view 
![cell view](https://github.com/user-attachments/assets/eb5e1b60-6a65-496e-9fee-142014cfb404)

#
# Day - 3 (Design library cell using magic layout and ngspice characterization)

- cloning git repo to openlane
```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

- Extracting sky130A.tech and include it in the vsdstdcelldesign
```
cp sky130A.tech /home/vsduser/Desktop/work/tools/openloane_working_dir/openlane/vsdstdcelldesign/
```
![to copy files to git hub](https://github.com/user-attachments/assets/ebc96255-4038-4cd1-8b25-b23bb450cb82) 

- copied file in vsdstdcelldesign

![copied file to git hub](https://github.com/user-attachments/assets/48ca472e-3da3-485e-975b-c329dd5ea22f) 

- To see the layout design
```
magic -T sky130A.tech sky130_inv.mag &
```
![layout 1](https://github.com/user-attachments/assets/fc3ec11d-6c0f-4974-88be-75098efd50c3)

![circuit naming](https://github.com/user-attachments/assets/606a5df6-f074-4a75-9080-8f4332c14087)

#
# Day - 4 (pre-layout timing analysis and importance of good clock tree)

- The Impact of Glitches

Errors in functionality:


Errors in computation or operation may result from glitches that allow wrong values to flow across the circuit.
Power Loss:

Every glitch results in needless switching activity, raising the circuit's dynamic power consumption.
Timing Infractions:

Unpredictable behavior may arise from setup or hold violations caused by bugs that spread to timed parts.
Skew in Cross-Talk Delta Delay



- Clock tree synthesis:
  In physical design, Clock Tree Synthesis (CTS) is a procedure that builds a clock tree network to uniformly distribute the clock signal across the system.
Principal Goals:


Reduce Skew: Make sure that the clock arrival times at various endpoints deviate as little as possible.
Optimize Delay: For improved performance, cut down on clock path delays.
Balanced Power: Maintain timing requirements while ensuring power efficiency.
In CTS, the H-Tree Algorithm:

One popular clock tree synthesis algorithm is H-tree.
It establishes a network with symmetric clock distribution to reduce:
Clock Skew: Consistent clock arrival times are guaranteed by equal path lengths.
Delay Variations: Timing irregularities are lessened with a balanced framework.
An "H" is formed at each level of the hierarchy by the H-tree structure, which hierarchically splits the clock network into smaller parts. 

![Screenshot 2024-12-24 223317](https://github.com/user-attachments/assets/89d1a31f-87dd-4874-9e27-5522723f790a)

![Screenshot 2024-12-24 223352](https://github.com/user-attachments/assets/ffb8ad9d-c86e-4bd4-b967-86f2807b2bf7)

![Screenshot 2024-12-24 222948](https://github.com/user-attachments/assets/d8c2dfea-da35-41d0-ad1e-84aeecd7f5ee) 

![Screenshot 2024-12-24 223102](https://github.com/user-attachments/assets/7256ba1e-c625-44a3-8e4b-71e14510ff92) 

![Screenshot 2024-12-24 222747](https://github.com/user-attachments/assets/35756fa0-884d-4e49-8224-58f462abfef3) 

![Screenshot 2024-12-24 222859](https://github.com/user-attachments/assets/9374448f-9e66-40b3-96c7-5cf91df5fcfc) 

#
# Day - 5 (final steps for RTL2GDS using tritonRoute and openSTA)

- Definition: By figuring out the routes for signal interconnects across metal layers, routing joins every cell in a design based on a netlist.


Important Routing Steps:
Worldwide Routing:
determines the approximate pathways for each net after dividing the chip into sections.
The precise metal rails and vias for interconnects are specified in the detailed routing.
Lee's Algorithm is the main algorithm.



In routing, the shortest path between two locations in a grid is found using a breadth-first search technique.
Steps: Expand the search in a wavefront pattern after starting at the source.
Mark cells that are farther apart till you reach your target.
To discover the shortest route, go back.
TritonRoute is the routing tool.
Developed to deal with contemporary VLSI designs, TritonRoute is an open-source tool for precise routing.



Features: Manages intricate routing situations.
carries out Design Rule Checks (DRCs) to guarantee manufacturing feasibility.

Benefits of Routing


guarantees that all cells have the right signal connections.
reduces power usage and connectivity latency.
In physical design, routing is an essential process that guarantees the design's functionality, efficiency, and manufacturing viability.

![Screenshot 2024-12-24 232130](https://github.com/user-attachments/assets/f74f426d-d613-4474-bf18-5265d3fa6186)

![Screenshot 2024-12-24 231811](https://github.com/user-attachments/assets/839f1ae2-ac6d-4833-969c-a95ed090b671) 

- To impact and optimize the routing of signals between different components on the chip, preprocessor route guides are a set of predetermined guidelines or paths used throughout the routing process in IC (Integrated Circuit) design. By lowering congestion, guaranteeing effective use of routing resources, and following design guidelines, these instructions assist in guiding the router tool (such as TritonRoute) in a way that can enhance the routing process.

Steering clear of congested locations is one approach to avoid congestion.
Wire Length Optimization: Cutting signal path lengths to improve performance.

Making Sure of the Design Rule Compliance: Adhering to the specifications for layer, width, and spacing.
Simplifying Routing: Increasing the speed and ease of difficult routing processes.

![Screenshot 2024-12-24 231900](https://github.com/user-attachments/assets/37ab6051-0b79-4acc-88b0-2c22d6945b23)

- Interlayer sequential panel routing and intralayer parallel panel routing

- Parallel Routing Within Layers

enables the parallel routing of several signals inside a single metal layer.
needs to be spaced carefully to prevent shorts or crosstalk.
Sequential Routing in Interlayers

uses vias to route signals across several metal layers.
increases complexity yet offers greater flexibility.
Both approaches maximize IC layout in terms of both performance and space.

![Screenshot 2024-12-24 231938](https://github.com/user-attachments/assets/9af6318c-846f-4143-b497-2afc45596b0d) 

- algorithm for routing topology

![Screenshot 2024-12-24 232024](https://github.com/user-attachments/assets/d53740e4-7901-4c92-abc4-9fae69f71d9d) 





