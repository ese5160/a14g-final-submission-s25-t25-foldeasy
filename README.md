[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AlBFWSQg)
# a14g-final-submission

    * Team Number: 25
    * Team Name: FoldEasy
    * Team Members: Chirag Satapathy, Sanskriti Binani
    * Github Repository URL: https://github.com/ese5160/a14g-final-submission-s25-t25-foldeasy
    * Description of test hardware: SAMW25 XPlained Board, HP Omen, Atomizer, Light Sensor, IR Sensor, SG92 Servo Motors, Water Level Sensor

## 1. Video Presentation

## 2. Project Summary

### Device Description

FOLDEASY is an IoT-based automated clothes folding machine designed to simplify everyday laundry tasks. The system uses the SAMW25 microcontroller with WINC1500 Wi-Fi connectivity to control servo motors, sensors, and a fragrance misting system. Our goal was to create a compact, efficient solution that addresses the time-consuming nature of manual clothes folding.

### Inspiration

The inspiration for FOLDEASY came from the challenges faced by busy students and professionals who struggle to find time for routine household chores. As engineering students ourselves, we wanted to apply embedded systems technology to create a practical solution that would save time and effort. 

The frustration of dealing with wrinkled, poorly folded clothes motivated us to develop a system that would consistently produce neatly folded garments while adding a fresh scent.

### Device Functionality

FOLDEASY offers several key functionalities that make it a comprehensive solution for automated clothes folding:

- **Automated Clothes Detection:** Using light sensors, the system detects when clothes are placed on the folding platform and initiates the folding sequence within 200ms.

- **Precision Folding:** Servo motors controlled via PWM signals move folding arms with precise angles (0°-180°) to execute predefined folding patterns for different clothing types (shirts, t-shirts, pants).

- **Fragrance Application:** An atomization disc activates for 3 seconds after folding to release a light fragrance mist, leaving clothes smelling fresh.

- **Dual Control Modes:**

    - **Automatic Mode:** The system detects clothes and completes the folding process automatically
    - **Manual Mode:** Users can control individual folding steps through a mobile interface

- **Remote Monitoring:** Wi-Fi connectivity enables users to control the device and receive status updates every 30 seconds through a Node-RED dashboard.

- **Water Level Monitoring:** A sensor detects mist levels in the fragrance container, alerting users when a refill is needed.
OTAFU Support: Over-the-Air Firmware Updates allow for remote software improvements without physical access.

- **OTAFU Support:** Over-the-Air Firmware Updates allow for remote software improvements without physical access.

### Challenges

Our journey developing FOLDEASY presented several significant challenges:

- **PCB Manufacturing Issues:** Of the three PCBs we designed, only one functioned correctly. This limited our testing capabilities and required us to adapt our implementation strategy.

- **Power Architecture Limitations:** We designed the power system for 2.2A capacity, but manufacturing defects limited output to only 1.5A. This prevented our servo motors from operating at full capacity, requiring us to optimize our folding sequences to work within these constraints.

- **RTOS Optimization:** Defining appropriate stack sizes for each task proved challenging. We needed to carefully balance memory usage while ensuring critical tasks had sufficient resources.

- **Signal Integrity:** Maintaining clean signals between components, especially for the servo motors and sensors, required careful PCB design and component placement to minimize interference.

- **Debugging Complexity:** With multiple concurrent tasks in the RTOS environment, tracking down timing and synchronization issues between subsystems required developing sophisticated debugging techniques.

### Prototype Learning

Building the FOLDEASY prototype taught us valuable lessons about embedded systems development:

- **Incremental Testing:** We learned to test individual components thoroughly before integration, which saved significant debugging time.

- **Power Requirements:** Understanding the real-world power needs of actuators like servo motors proved critical - theoretical calculations weren't sufficient.

- **RTOS Task Management:** We gained practical experience in prioritizing tasks and managing shared resources to prevent deadlocks and race conditions.

- **Sensor Calibration:** Environmental factors significantly impacted sensor readings, requiring dynamic calibration routines for reliable operation.

### Next Steps

Moving forward, we plan to enhance FOLDEASY with the following improvements:

- **Refined PCB Design:** Address manufacturing issues and optimize the power distribution system to achieve the intended 2.2A capacity.
- **Machine Learning Integration:** Implement a computer vision system to automatically detect garment types and select the optimal folding pattern.
- **Energy Efficiency:** Reduce power consumption through optimized motor control algorithms and sleep modes when inactive.
- **Enhanced User Interface:** Develop a dedicated mobile application with more detailed control options and usage statistics.
- **Predictive Maintenance:** Add monitoring for servo motor health and performance to predict maintenance needs before failures occur.

### Takeaways from ESE 5160

The ESE 5160 course provided us with invaluable knowledge and skills that transformed our understanding of embedded systems development. Through hands-on experience with PCB design, we mastered the entire process from initial schematic capture to final manufacturing considerations, giving us the confidence to create custom hardware solutions for complex problems. The integration of Node-RED into our project workflow enabled us to rapidly develop intuitive IoT dashboards and user interfaces with minimal development overhead, significantly enhancing the usability of our embedded system.

Throughout the course, we refined our debugging methodologies, learning to systematically approach complex embedded systems issues through tools like protocol analyzers and implementing efficient data structures such as circular buffers. Our practical work with signal integrity challenges taught us to identify and mitigate potential issues through proper PCB layout techniques and strategic component selection. Perhaps most significantly, our deep dive into RTOS architecture using FreeRTOS provided us with a framework for designing reliable, performant multi-tasking systems, allowing us to properly structure embedded applications for real-world deployment scenarios.


## 3. Hardware & Software Requirements

### Hardware Requirements Specification (HRS)

| ID | Requirement | Description | Pass |
| --- | --- | --- | --- |
| HRS 01 | Microcontroller | The system shall use the SAMW25 microcontroller, providing Wi-Fi connectivity with WINC1500 and processing power to control all tasks. | ✓ |
| HRS 02 | Servo Motors | The system shall use servo motors for precise folding arm control, with a range of motion from 0° to 180°. | ✓ |
| HRS 03 | IR Sensors | The device shall use IR sensors for object detection, with a range of 10 cm to 1 meter, to count number of clothes folded. | ✓ |
| HRS 04 | Wi-Fi Connectivity | The device shall have Wi-Fi connectivity via the SAMW25 microcontroller, enabling remote control and monitoring. | ✓ |
| HRS 05 | Atomization Disc | A atomization disc shall be used to release fragrance mist after the folding process is completed. | ✓ |
| HRS 06 | Power Supply | The system shall be powered by a rechargeable 3.7V Li-ion battery, ensuring portability and energy efficiency. | ✓ |
| HRS 07 | OTAFU Support | The device shall support Over-the-Air Firmware Updates (OTAFU) to allow easy remote updates without requiring physical access. | ✓ |
| HRS 08 | Water Level Sensor | The system shall include a water level sensor to detect the mist level inside the fragrance container. The sensor will help determine when the container needs to be refilled. | ✓ |
| HRS 09 | Folding Style Modes | The system shall provide various folding modes, such as three-fold for shirts, two-fold for t-shirts, and a different fold for pants/jeans. | ✓ |
| HRS 10 | Light Sensor | The device shall use Light sensors for clothes detection when placed on the clothes folding machine. | ✓ |

### Software Requirements Specification (SRS)

| ID | Requirement | Description | Pass |
| --- | --- | --- | --- |
| SRS 01 | Clothes Detection | The system shall detect clothes using light sensor, triggering the folding process within approximately 200 ms after detection. | ✓ |
| SRS 02 | Servo Motor Control | The system shall control servo motors using PWM to move the folding arms based on predefined folding actions. | ✓ |
| SRS 03 | Fragrance Activation | The atomization disc shall be activated for 3 seconds after folding to release a fragrance mist. | ✓ |
| SRS 04 | Control Modes | The system shall support Manual and Automatic modes for user interaction. Manual mode allows the user to directly control the system, while automatic mode detects clothes and starts the folding process automatically. | ✓ |
| SRS 05 | Wi-Fi Communication | The system shall allow remote control via Wi-Fi, with status updates every 30 seconds sent to the user's mobile device. | ✓ |
| SRS 06 | RTOS for Real-Time Operation | The system shall run on an RTOS, ensuring real-time task management for tasks like motor control, sensor reading, and Wi-Fi communication. | ✓ |
| SRS 07 | OTAFU | The system shall support Over-the-Air Firmware Updates (OTAFU), allowing firmware to be updated remotely. | ✓ |
| SRS 08 | Water Level Monitoring | The system shall monitor the water level sensor to detect the mist level inside the fragrance container. When the water level is too low, the system shall notify the user to refill. | ✓ |

## 4. Project Photos & Screenshots

## Codebase

- A link to your final embedded C firmware codebases
- A link to your Node-RED dashboard code
- Links to any other software required for the functionality of your device

