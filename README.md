# Nasscom-Soc-design-planning Workshop (December 11-December 24)

- Day - 1 (inception of open source EDA, openlane and SKY130PDK)

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
- Day - 2 (Good floorplan Vs Bad floorplan and introduction to library cells)

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
- Day - 3 (Design library cell using magic layout and ngspice characterization)

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


