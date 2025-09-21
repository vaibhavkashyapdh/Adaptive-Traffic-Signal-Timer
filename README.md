# Adaptive-Traffic-Signal-Timer

![Image](https://github.com/user-attachments/assets/6953950e-2646-4c91-a8e4-1de270cf2618)

This project focuses on developing an adaptive traffic signal system that uses real-time traffic density data to optimize green light timings at intersections. It addresses the inefficiencies of static traffic light systems by dynamically adjusting signal times to reduce congestion and vehicle idle time. The project demonstrates proficiency in computer vision, machine learning, and system simulation.

### **Key Objectives**

- **Vehicle Detection:** Detect and classify different types of vehicles (cars, bikes, heavy vehicles, rickshaws) in real time using CCTV images.
- **Traffic Density Calculation:** Calculate traffic density for each lane based on the number of detected vehicles.
- **Adaptive Signal Switching:** Develop an algorithm that uses traffic density and other factors to dynamically set green signal times, while also updating red signal times for other lanes.
- **System Simulation:** Create a simulation to visualize the system's effectiveness and compare it against traditional static signal timers.

### **Methodology**

- **Vehicle Detection Module:** A custom **YOLO** (You Only Look Once) model was trained for vehicle detection. The training dataset was prepared by scraping and manually labeling images. The YOLO model's configuration was updated to detect four specific vehicle classes: cars, bikes, buses/trucks, and rickshaws. The trained model was integrated with the OpenCV library for vehicle detection.
- **Signal Switching Algorithm:** The algorithm receives vehicle detection data in JSON format. It calculates the green light time for each signal using a specific formula:
    
    GST=NoOfLanes+1∑(NoOfVehiclesvehicleClass∗AverageTimevehicleClass)
    
    . This time is constrained by minimum and maximum values to prevent any one lane from being "starved" of a green light. The system runs on separate threads to ensure seamless, lag-free timer assignment.
    
- **Simulation Module:** A simulation was built from scratch using Pygame to model a 4-way intersection. It displays a real-time countdown for each signal and tracks the number of vehicles that have crossed. Vehicle generation is randomized to mimic real-world traffic, and the simulation accounts for vehicle movement, speed, and reactions to traffic signals.

### **Key Findings**

- The adaptive system effectively calculates and adjusts green light durations based on real-time traffic density. For example, in a low-traffic scenario, the system could set a green light for 10 seconds, whereas a static system might waste time with a fixed 30-second interval.
- By dynamically allocating green time, the system can significantly improve traffic flow and reduce congestion at busy intersections.
- The use of multi-threading for detection and timer management prevents lag and ensures a smooth, responsive system.

### **Future Work**

- Expand the vehicle detection model to include more classes and improve accuracy.
- Incorporate additional factors into the signal switching algorithm, such as pedestrian crossing times or emergency vehicle prioritization.
- Develop a more sophisticated simulation environment that can model complex urban traffic networks beyond a single intersection.
- Explore cloud-based deployment for real-world application and scalability.
