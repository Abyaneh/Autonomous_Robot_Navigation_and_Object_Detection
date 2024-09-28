# Autonomous Robot Navigation and Object Detection

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Project Layers](#project-layers)
- [Technologies & Tools Used](#technologies--tools-used)
- [Video Demonstration](#video-demonstration)
- [How to Run the Project](#how-to-run-the-project)
- [Team Members](#team-members)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project showcases the development of a mobile robot capable of navigating autonomously using a camera-based positioning system. The robot is controlled by a PID controller and utilizes Artificial Potential Field pathfinding while detecting and classifying objects (rotten vs. healthy bananas) using **YOLO**. The aim is to create an efficient and intelligent robotic system that can operate in real-world environments.

[Back to Top](#table-of-contents)

## Features
- **Autonomous Navigation**: The robot can navigate through environments without human intervention, following predefined paths.
- **Real-Time Object Detection (My Contribution)**: Equipped with a YOLO model, the robot can identify and classify bananas as either rotten or healthy.
- **Camera-Based Positioning**: Utilizes a camera to determine the robot's position and orientation accurately.
- **PID Control System**: Employs a PID controller for precise movement and stability during navigation.
- **Obstacle Avoidance**: Implements Artificial Potential Field algorithms to avoid obstacles dynamically.

[Back to Top](#table-of-contents)

## Project Layers
1. **Monitoring Layer**: A Windows-based control panel application that displays the camera feed and the robot's current position and orientation.
2. **Image Processing Layer**: Processes raw images from a top-down camera to detect the centers of red, green, and blue circles, allowing for accurate position and orientation calculation.
3. **Pathfinding & Control**: Users can define paths on the control panel for the robot to follow. The Artificial Potential Field algorithm is used for obstacle avoidance, combined with a manually tuned PID controller for movement precision.
4. **Communication Layer**: The control panel acts as a TCP server while the robot functions as a TCP client, communicating over Wi-Fi. Control signals are sent to the robot’s motors in real-time using the socket API.
5. **Object Detection (My Contribution)**: I equipped the robot with a YOLO model trained to detect rotten vs. healthy bananas in real-time. The dataset was labeled using Roboflow, and the model was integrated with the robot’s camera for live detection.

[Back to Top](#table-of-contents)

## Technologies & Tools Used
- **Programming Languages**: Python, C++
- **Control Systems**: PID controller
- **Pathfinding**: Artificial Potential Field
- **Image Processing**: OpenCV
- **Deep Learning**: YOLO for object detection
- **Tools**: Roboflow, GitHub
- **Communication Protocol**: TCP/IP via socket API

[Back to Top](#table-of-contents)

## Videos and Photos from project

### Physical Structure
![photos1](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/Clipped_image_%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B9%DB%B2%DB%B6_%DB%B1%DB%B2%DB%B4%DB%B2%DB%B3%DB%B9.png)

### Circuitry
![photos2](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/Screenshot_%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B9%DB%B2%DB%B6_%DB%B1%DB%B2%DB%B4%DB%B3%DB%B5%DB%B9_LinkedIn.png)

### rotten and fresh banana detection
![photos3](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B7%DB%B0%DB%B9_%DB%B1%DB%B3%DB%B4%DB%B6%DB%B1%DB%B9.jpg)
## How to Run the Project
To run the project locally, follow the steps below:

1. Clone this repository:
    ```bash
    git clone https://github.com/Abyaneh/autonomous-robot-navigation.git
    ```
2. Change directory to the project folder:
    ```bash
    cd autonomous-robot-navigation
    ```
3. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```
4. **Run the Monitoring Layer**: Launch the control panel application to start monitoring and controlling the robot.
5. **Configure the Camera**: Make sure your camera is set up and connected properly to ensure the robot can process the video feed.
6. **Start Navigation**: Define a path on the control panel and watch the robot navigate autonomously while detecting objects.

[Back to Top](#table-of-contents)

## Team Members
- **Mohammad Maleki Abyaneh** (me)
- **Amin Elmi Ghiasi**
- **Arman Javan Sekhavat**
- **Mohammad Mohtashami**
- **Alireza Moradmand**
- **Alireza Padash**
![photos2](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/Clipped_image_%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B9%DB%B2%DB%B6_%DB%B1%DB%B3%DB%B4%DB%B7%DB%B3%DB%B3.png)

[Back to Top](#table-of-contents)

## Contributing
Contributions are welcome! To contribute:
1. Fork this repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit (`git commit -m 'Add a new feature'`).
4. Push to your branch (`git push origin feature-branch`).
5. Open a pull request for review.

[Back to Top](#table-of-contents)

## License
This project is licensed under the **MIT License**. For more details, see the `LICENSE` file.

[Back to Top](#table-of-contents)
