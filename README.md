# Smart Traffic Management System

## Project Overview

The **Smart Traffic Management System** is a Python-based intelligent traffic signal simulation designed to improve traffic flow at a four-way intersection. The system dynamically adjusts green signal durations based on traffic density, prioritizes congested roads, and supports pedestrian priority to make traffic management more efficient.

Instead of using fixed traffic signal timings, this system applies a simple adaptive decision-making algorithm to determine which direction should receive the green signal.

## Key Features

- **Dynamic Traffic Density Detection:** Generates random vehicle counts (0–20) for each direction.
- **Traffic-Based Signal Timing:** Automatically adjusts green signal duration according to traffic density.
- **Priority-Based Lane Selection:** Selects the traffic group with the higher vehicle count.
- **Alternating Signal Control:** Prevents the same direction from continuously receiving priority.
- **Early Green Signal Switching:** Switches the green signal early when traffic congestion on the opposite side becomes significantly higher.
- **Pedestrian Priority:** Randomly simulates pedestrian requests and assigns a dedicated 15-second priority phase.
- **Yellow Signal Transition:** Includes a 3-second yellow phase before switching directions.
- **All-Yellow Safety Phase:** Includes a 2-second all-yellow transition before activating the next traffic group.
- **Console-Based Monitoring:** Displays vehicle counts, traffic density bars, signal status, operating mode, and countdown timers.

## Traffic Intersection Design

The system divides the four-way intersection into two traffic groups:

| Group | Directions |
|---|---|
| Group 1 | North and South |
| Group 2 | East and West |

Only one traffic group receives a green signal at a time, while the other group remains red.

## Traffic Signal Timing

The system determines green signal duration based on the total number of vehicles in the selected traffic group.

| Traffic Density | Vehicle Count | Green Duration |
|---|---:|---:|
| High Traffic | 25 or more | 60 seconds |
| Normal Traffic | 10–24 | 30 seconds |
| Low Traffic | Below 10 | 15 seconds |
| Pedestrian Priority | Pedestrian request | 15 seconds |

**Note:** The pedestrian priority mode overrides the normal traffic-based green duration.

## Early Switching Mechanism

The system continuously monitors traffic conditions during the green phase.

- Minimum green duration: 15 seconds.
- Opposite traffic threshold: 8 vehicles.
- If the opposite traffic group has more than 8 additional vehicles compared to the currently active group after the minimum green period, the system switches early.

This mechanism helps reduce unnecessary waiting time for heavily congested roads.

## Technologies Used

- **Programming Language:** Python
- **Libraries:**
  - `time` – Controls signal countdowns and transition delays.
  - `random` – Simulates vehicle density and pedestrian requests.
- **Programming Concepts:**
  - Object-Oriented Programming (OOP)
  - Classes and Objects
  - Conditional Statements
  - Loops
  - Lists and Dictionaries
  - Randomized Simulation
  - Dynamic Decision-Making

## Project Structure

```text
Smart-Traffic-Management-System/
│
├── main.py          # Main traffic management program
└── README.md        # Project documentation
```

## Installation and Setup

### 1. Install Python

Download and install Python 3 from:

https://www.python.org/downloads/

### 2. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### 3. Navigate to the Project Directory

```bash
cd Smart-Traffic-Management-System
```

### 4. Run the Program

```bash
python main.py
```

No external Python packages are required because the project uses built-in Python libraries.

## How to Use

1. Run the Python program.
2. The system generates random traffic density for all four directions.
3. It calculates the priority traffic group.
4. It assigns an appropriate green signal duration.
5. It checks for pedestrian priority.
6. It monitors opposite-side congestion during the green phase.
7. It executes yellow and all-yellow transition phases.
8. It repeats the process for the specified number of cycles.

By default, the simulation runs for five cycles.

To change the number of cycles:

```python
system = SmartTrafficSystem()
system.run(10)
```

## Sample Output

```text
CYCLE 1

Traffic Density:
North : 19 cars | GREEN
South :  9 cars | GREEN
East  : 12 cars | RED
West  :  1 cars | RED

Mode: High Traffic
Pedestrian: None

GREEN SIGNAL: ['North', 'South']

Green light countdown:
   60 sec remaining...
   59 sec remaining...
   ...

Switching to YELLOW
Yellow phase ended!

ALL LANES YELLOW
Switching sides now!
```

*Note: Actual vehicle counts and signal timings vary because traffic and pedestrian requests are randomly generated.*

## Limitations

- Traffic density is simulated using random numbers rather than real-time cameras or vehicle sensors.
- Pedestrian requests are randomly generated rather than collected from physical pedestrian buttons.
- The system operates through a console interface.
- It does not currently integrate with physical traffic lights or IoT devices.
- Traffic safety validation and real-world intersection constraints are outside the scope of this simulation.

## Future Improvements

The project can be extended with the following features:

1. Integrate computer vision using OpenCV to detect vehicles from live CCTV footage.
2. Use YOLO-based object detection for real-time vehicle counting.
3. Implement a graphical user interface (GUI) to visualize traffic signals.
4. Introduce machine learning to predict traffic congestion.
5. Integrate IoT sensors for real-time vehicle detection.
6. Develop a web-based traffic monitoring dashboard using Flask.
7. Add an emergency vehicle priority system for ambulances, fire services, and police vehicles.
8. Implement real pedestrian detection and crossing-time management.

## Project Objective

The primary objective of this project is to demonstrate how programming and intelligent decision-making algorithms can be applied to traffic management problems.

By dynamically adjusting traffic signal timings based on simulated vehicle density and pedestrian priority, the project demonstrates a basic approach toward developing a smarter and more adaptive traffic control system.

## Author

**Md Fokrul Akon**

Computer Science and Engineering  
Data Science Major

## License

This project is available for educational and research purposes.
