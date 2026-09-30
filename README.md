# Smart Attendance Management System

A real-time attendance management system using facial recognition and computer vision to automatically identify individuals and record their attendance.

The system captures live video through a webcam, detects and recognizes registered individuals, records attendance with timestamps, and generates a CSV attendance report that can be exported and sent to faculty.

## Overview

Traditional attendance methods such as manual roll calls and sign-in sheets can be time-consuming, error-prone, and inefficient for larger groups.

This project provides a contactless and automated attendance solution using facial recognition, computer vision, real-time video processing, YOLO-based person detection, automated CSV attendance logging, and attendance report export.

The system was developed using Python, OpenCV, face_recognition, and NumPy, with a focus on real-time processing and reducing manual intervention.

## Key Features

- Real-time face detection using a webcam
- Facial recognition of registered individuals
- 128-dimensional face encoding
- Automatic attendance marking
- Duplicate attendance prevention
- Timestamp-based attendance logging
- CSV attendance report generation
- Real-time attendance count
- Attendance report export
- Email-based attendance report delivery
- YOLO-based person detection
- Frame skipping for improved processing efficiency
- Handling of different facial angles and lighting conditions

## System Architecture

~~~text
                    Webcam Input
                         |
                         v
                  Video Capture
                     OpenCV
                         |
                         v
                   Face Detection
                         |
                         v
               Face Encoding & Matching
                         |
                  Match Found?
                   /          \
                 Yes           No
                  |             |
                  v             |
            Mark Present        |
                  |             |
                  v             |
          Record Name & Time    |
                  |             |
                  v             |
             CSV Logger         |
                  |             |
                  v             |
          Export / Email        |
             Attendance         |
               Report           |
                                |
                                v
                             Continue
~~~

## Methodology

The system consists of the following stages:

### 1. System Setup

A standard webcam is used to capture the live video stream. Python is used as the primary programming language.

### 2. Face Data Preparation

Images of registered individuals are collected and preprocessed.

Each image is processed using the `face_recognition` library to generate a unique 128-dimensional face encoding. These encodings are stored as known face data for later recognition.

### 3. Real-Time Face Recognition

The webcam continuously captures video frames.

For each frame, the system:

1. Captures the video frame.
2. Detects available faces.
3. Generates face encodings.
4. Compares detected encodings with registered face encodings.
5. Identifies the closest matching individual.

### 4. Attendance Logging

When a registered individual is successfully recognized, the system marks the individual as present and records their name and current timestamp in the attendance CSV file.

Duplicate attendance entries are avoided by maintaining a list of individuals who have already been recorded.

### 5. Performance Optimization

To reduce computational load, the system uses frame skipping and processes approximately one frame per second rather than analyzing every captured frame.

The system also handles:

- No face detected
- Multiple faces detected
- Variations in facial angles
- Variations in lighting conditions

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| OpenCV | Image processing and video capture |
| face_recognition | Face detection, encoding and recognition |
| NumPy | Numerical operations |
| CSV | Attendance data storage |
| YOLO | Person detection |
| Webcam | Real-time video input |

## Input

The system requires:

- Live video stream from a webcam
- Pre-registered images of known individuals
- Stored face encodings

## Output

The system generates an attendance CSV file containing:

- Name of recognized individual
- Date
- Time of attendance
- Total attendance count

Example:

~~~text
Name          Time       Date
--------------------------------
Anuj Ladkat   23:14:58   2024-11-14
Reddy Anna    23:17:12   2024-11-14
Varun Kolte   23:17:15   2024-11-14
Yuzra Khan    23:17:48   2024-11-14
~~~

## Workflow

~~~text
Register Individuals
        |
        v
Generate Face Encodings
        |
        v
Start Webcam
        |
        v
Detect Faces
        |
        v
Generate Face Encodings
        |
        v
Compare With Registered Faces
        |
        v
Identify Individual
        |
        v
Mark Attendance
        |
        v
Record Timestamp
        |
        v
Generate CSV Report
        |
        v
Export / Email Report
~~~

## Application Interface

The system includes a graphical interface that provides controls for:

- Start Camera
- Stop Camera
- Export CSV
- Send Email

The interface displays the current attendance status and provides access to the generated attendance report.

## Results

The experimental results reported in the accompanying research paper include:

- 95% face recognition rate on the pre-registered dataset
- Approximately 15 FPS average processing speed
- Real-time attendance recording
- Timestamp logging for recognized individuals
- Successful identification of groups of students
- More than 80% reduction in attendance-marking time compared with manual roll calls

These results are based on the dataset and experimental conditions used in the study.

## Future Improvements

Potential future improvements include:

- Multi-face detection and recognition
- Improved recognition under different lighting conditions
- Better handling of image-quality variations
- Further optimization of real-time performance
- Improved recognition accuracy
- Improved scalability for larger environments
- Integration of more advanced computer vision techniques

## Research Paper

This project is supported by the research paper:

**Enhanced Attendance Management with Face Recognition Technology**

### Authors

- Varun Kolte
- Anuj Ladkat
- Manoj Reddy

**Department of Computer Science and Engineering**  
**MIT ADT University, Pune, India**

The research paper presents the methodology, real-time face recognition pipeline, attendance logging process, system flowchart, GUI implementation, and experimental results.

## Contributors

| Name | Contribution |
|---|---|
| Varun Kolte | Project Contributor |
| Anuj Ladkat | Project Contributor |
| Manoj Reddy | Project Contributor |

## License

This project is intended for educational and research purposes.
