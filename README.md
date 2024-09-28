# Autonomous Robot Navigation and Object Detection

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Project Layers](#project-layers)
- [Explain more about the image Processing Layer](#explain-more-about-the-image-Processing-Layer)
- [My dataset](#my-dataset)
- [Technologies & Tools Used](#technologies--tools-used)
- [Video Demonstration](#video-demonstration)
- [How to Run the Project](#how-to-run-the-project)
- [Team Members](#team-members)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project showcases the development of a mobile robot capable of navigating autonomously using a camera-based positioning system. The robot is controlled by a PID controller and utilizes Artificial Potential Field pathfinding while detecting and classifying objects (rotten vs. fresh bananas) using **YOLO**. The aim is to create an efficient and intelligent robotic system that can operate in real-world environments.

[Back to Top](#table-of-contents)

## Features
- **Autonomous Navigation**: The robot can navigate through environments without human intervention, following predefined paths.
- **Real-Time Object Detection (My Contribution)**: Equipped with a YOLO model, the robot can identify and classify bananas as either rotten or fresh.
- **Camera-Based Positioning**: Utilizes a camera to determine the robot's position and orientation accurately.
- **PID Control System**: Employs a PID controller for precise movement and stability during navigation.
- **Obstacle Avoidance**: Implements Artificial Potential Field algorithms to avoid obstacles dynamically.

[Back to Top](#table-of-contents)

## Project Layers
1. **Monitoring Layer**: A Windows-based control panel application that displays the camera feed and the robot's current position and orientation.
2. **Image Processing Layer**: Processes raw images from a top-down camera to detect the centers of red, green, and blue circles, allowing for accurate position and orientation calculation.
3. **Pathfinding & Control**: Users can define paths on the control panel for the robot to follow. The Artificial Potential Field algorithm is used for obstacle avoidance, combined with a manually tuned PID controller for movement precision.
4. **Communication Layer**: The control panel acts as a TCP server while the robot functions as a TCP client, communicating over Wi-Fi. Control signals are sent to the robot’s motors in real-time using the socket API.
5. **Object Detection (My Contribution)**: I equipped the robot with a YOLO model trained to detect rotten vs. fresh bananas in real-time. The dataset was labeled using Roboflow, and the model was integrated with the robot’s camera for live detection.

[Back to Top](#table-of-contents)

## Explain more about the image Processing Layer

### Real-Time Object Detection (My Contribution)
One of the core components of this project is the real-time object detection system, specifically designed to distinguish between rotten and fresh bananas. This feature plays a vital role in the autonomous navigation of the robot, allowing it to recognize and classify objects in its environment effectively. Below are the details of this system, including the methodologies, tools, and results.

#### 1. Dataset Preparation and Labeling
The first step in creating an object detection model is collecting and labeling data. For this task, we used Roboflow, a popular tool for image annotation and dataset management. I performed the following tasks:

Image Collection: Captured a large dataset of banana images, ensuring variety in lighting conditions, angles, and banana states (rotten vs. fresh).
Annotation: Manually labeled the bananas using bounding boxes and appropriate class labels (i.e., "rotten" and "fresh").
Data Augmentation: Applied image augmentation techniques such as flipping, rotation, and brightness adjustments to increase the dataset’s diversity and improve model robustness.
#### 2. Training the YOLO Model
To achieve real-time object detection, we selected YOLO (You Only Look Once) as our model, due to its efficiency and accuracy in detecting objects in real-time. The key steps involved in training were:

Model Selection: Chose a pre-trained YOLOv5 model to fine-tune for our specific task. YOLO’s architecture allows for fast detection, which is crucial for real-time applications like ours.
Training Process:
Fine-tuned the model on the labeled banana dataset, running several epochs until optimal accuracy and loss metrics were achieved.
Used a custom training script to monitor the training process, adjust learning rates, and evaluate the model's performance after each epoch.
Implemented early stopping to avoid overfitting, ensuring that the model performs well on unseen data.
Validation: After training, the model was validated on a separate test set to assess its ability to accurately distinguish between rotten and fresh bananas.
#### 3. Real-Time Integration with the Robot
Once the YOLO model was trained, it was integrated into the robot’s vision system. The following steps describe this integration:

Camera Feed Processing: The robot’s camera continuously streams real-time video to the processing unit, which passes each frame through the YOLO model.
Object Detection Pipeline:
Preprocessing: Each video frame is resized and normalized before being fed into the model to ensure consistent detection accuracy.
Inference: The YOLO model detects objects (bananas) in real-time, outputting bounding boxes, class labels (rotten/fresh), and confidence scores.
Post-processing: Non-maximum suppression (NMS) was applied to eliminate duplicate detections and refine the bounding boxes for a cleaner result.
Visualization: The detected bananas are highlighted with bounding boxes in the robot's camera feed, and their classification (rotten/fresh) is displayed on the control panel.
Decision-Making: Based on the classification results, the robot can adjust its path or perform specific tasks, such as avoiding rotten bananas.
#### 4. Performance and Results
The real-time object detection system was tested extensively in various scenarios, including different lighting conditions and varying distances. The key results were:

Detection Speed: The YOLO model provided real-time detection with minimal latency, allowing the robot to make immediate decisions based on the objects detected.
Accuracy: The model achieved an accuracy rate of over 70%( you can increase this rate with more epochs, use other methods, or more data) in distinguishing between rotten and fresh bananas, even in challenging environments.
Scalability: The system is scalable to other types of objects by simply retraining the YOLO model on a different dataset, making it adaptable to various industrial applications.
#### 5. Technologies & Tools Used
YOLOv8: For real-time object detection and classification.
Roboflow: For dataset annotation, augmentation, and management.
Python: The primary programming language used for model training and integration.
OpenCV: For image processing and handling the camera feed.
PyTorch: For training the YOLO model.
TCP/IP: Communication protocol used to send detection data from the robot to the control panel.
Visual Example
Below is a sample image showing the real-time detection of bananas, where the robot successfully identifies rotten and fresh bananas:

Next Steps and Future Improvements
Multi-class Detection: In future iterations, the system can be extended to detect and classify additional objects or anomalies beyond bananas.
Model Optimization: Further optimization of the YOLO model, potentially exploring lightweight versions like YOLOv8 for faster inference on embedded systems.
Robustness Testing: More extensive testing in diverse environmental conditions (e.g., low light, obstructions) to ensure the system’s reliability.
Back to Top


## My dataset

you can download my dataset from this [link](https://www.kaggle.com/sriramr/fruits-fresh-and-rotten-for-classification)


## Technologies & Tools Used
- **Programming Languages**: Python, C++
- **Control Systems**: PID controller
- **Pathfinding**: Artificial Potential Field
- **Image Processing**: OpenCV
- **Deep Learning**: YOLO for object detection
- **Tools**: Roboflow, GitHub
- **Communication Protocol**: TCP/IP via socket API

[Back to Top](#table-of-contents)

## Videos and Photos from the project

### Physical Structure
![photos1](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/Clipped_image_%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B9%DB%B2%DB%B6_%DB%B1%DB%B2%DB%B4%DB%B2%DB%B3%DB%B9.png)

### Circuitry
![photos2](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/Screenshot_%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B9%DB%B2%DB%B6_%DB%B1%DB%B2%DB%B4%DB%B3%DB%B5%DB%B9_LinkedIn.png)

### Rotten and fresh banana detection
![photos3](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/VideoCapture_%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B9%DB%B2%DB%B8-%DB%B2%DB%B2%DB%B0%DB%B0%DB%B4%DB%B2.jpg)

![photos4](https://github.com/Abyaneh/rotten_and_fresh/blob/main/photos%20%20from%20group%20project/%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B7%DB%B0%DB%B9_%DB%B1%DB%B3%DB%B4%DB%B6%DB%B1%DB%B9.jpg)

[Video from rotten and fresh banana detection](https://github.com/Abyaneh/rotten_and_fresh/blob/main/%DB%B2%DB%B0%DB%B2%DB%B4%DB%B0%DB%B7%DB%B0%DB%B9_%DB%B1%DB%B3%DB%B4%DB%B8%DB%B2%DB%B8.mp4)


### Hint
you can see [another video in my colab](https://drive.google.com/file/d/1IpKdUAs_cS0MrwI0nmURji8K6AuAG6XX/view?usp=drive_link)

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
