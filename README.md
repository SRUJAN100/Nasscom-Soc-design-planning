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


