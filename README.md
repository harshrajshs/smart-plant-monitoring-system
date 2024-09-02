# GreenSense: Smart Plant Monitoring System

## Overview
The **GreenSense** is a system designed to collect, process, and analyze data from sensors connected to an ESP32 microcontroller. The collected data includes soil composition information and leaf images. This data is transmitted to a server using the MQTT protocol, where it undergoes processing by a machine learning model. The processed results are then shared with the client via SMTP email. Additionally, all data and results are stored in a MongoDB database for further analysis and reference.

## Pipeline
![Screenshot (345)](https://github.com/A-Shubhi/DA353_IoT_Team5/assets/95265187/e2c8e09b-d97d-48b9-ad89-be69029c477f)

----

## Components
### 1. ESP32 Device
The ESP32 device collects data from sensors, including soil composition data and leaf images. This data is transmitted to the server periodically using the MQTT protocol. If no data is received within the desired span, the user is notified via SMTP email.

### 2. Server
The server receives data from the ESP32 device via MQTT. It includes the following components:
- **Server.ipynb**: Receives data from MQTT, converts the received image string to an image file (leaf.jpeg), and stores the leaf image and soil composition data in separate text files (leaf.txt and composition.txt).

### 3. Machine Learning Model
The machine learning model processes the received data to derive meaningful insights. It includes the following components:
- **Main.ipynb**: Runs the machine learning model on the received data and shares the results with the client via SMTP email.

### 4. MongoDB Database
MongoDB is used to store all collected data and processed results for further analysis. The data stored includes both raw sensor data and the output of the machine learning model.

----

## Usage
1. **ESP32 Device**: Flash the `ESP_main.py` file onto the ESP32 device. Ensure that the device is connected to the appropriate sensors for data collection. Configure the MQTT settings to connect to the MQTT broker.

2. **Server Setup**: Run the `Server.ipynb` notebook on the server. Make sure to install all required dependencies before running the notebook. This notebook will receive data from the ESP32 device via MQTT, extract the image and soil composition data, and store them in the designated files.

3. **Model Processing**: Utilize the `Main.ipynb` notebook to process the collected data using the machine learning model. This notebook will generate insights from the data and share them with the client via SMTP email.

4. **MongoDB Integration**: Run the notebook `Device_to_mongoDB1.ipynb` to send data from the ESP32 device to the MongoDB database. Ensure that the MongoDB server is properly configured and accessible from the server environment.

----

## File Structure
- **ESP_main.py**: Contains the code for the ESP32 device to collect data and transmit it via MQTT.
- **Server.ipynb**: Jupyter notebook for receiving data from MQTT, extracting image and soil composition data, and storing them in files.
- **Main.ipynb**: Jupyter notebook for processing data using the machine learning model and sharing results via SMTP.
- **Device_to_mongoDB1.ipynb**: Notebook for sending data from the ESP32 device to the MongoDB database.
- **Model Folder**: Contains supporting Python files for the machine learning model, including functions and requirements.

----

## Requirements
Ensure that the following dependencies are installed:
- Python 3.x
- Jupyter Notebook
- Paho MQTT library
- MongoDB
- Necessary Python libraries for machine learning model (specified in the `requirements.txt` file in the Model folder)
Certainly, here's the revised Implementation section with instructions on changing paths, credentials, and port numbers:

----

## Implementation

### 1. ESP32 Device Setup
- Update the `ESP_main.py` file with the appropriate MQTT broker credentials, including the broker address, port number, username, and password.
- Modify the path to match the location of the sensor data and image capture on the ESP32 device.
- Ensure that the MQTT broker settings match those configured on the server.

### 2. Server Setup
- Update the notebook with the correct MQTT broker credentials, including the broker address, port number, username, and password.
- Adjust the file paths in the notebook to match the desired location for storing the leaf image (`leaf.jpeg`), leaf data (`leaf.txt`), and soil composition data (`composition.txt`).
- Ensure that the server has access to the necessary directories for storing the received data.

### 3. Machine Learning Model Processing
- In the `Main.ipynb` notebook, update the SMTP email settings with the appropriate credentials for sending emails. This includes the SMTP server address, port number, username, and password.
- Adjust the paths in the notebook to locate the input data (leaf image and soil composition data) and to save the processed results.
- Ensure that the SMTP server allows sending emails from the specified email address.

### 4. MongoDB Integration
- Update the `Device_to_mongoDB1.ipynb` notebook with the MongoDB connection details, including the server address, port number, username, and password.
- Adjust the paths in the notebook to locate the input data (leaf image and soil composition data) and to save the data to the MongoDB database.
- Ensure that the MongoDB server allows connections from the specified IP address and port.

### Security Considerations
- Ensure that all sensitive information, such as MQTT broker credentials, SMTP server credentials, and MongoDB connection details, are kept secure and not shared publicly.
- Use secure methods, such as encryption, for transmitting sensitive data over the network.
- Regularly update passwords and credentials to prevent unauthorized access.

By following these steps and making the necessary adjustments, you can successfully set up and deploy the **Project Name** system while ensuring the security of sensitive information and data transmission.

----

## Outputs
-An email is sent giving updates about the soil conditions and how it can be improved
![WhatsApp Image 2024-04-28 at 18 55 00](https://github.com/A-Shubhi/DA353_IoT_Team5/assets/95135448/d7e34016-204e-4576-852c-98e289efbdae)

- An email is sent explaining the cause of disease and how to prevent it
![WhatsApp Image 2024-04-28 at 19 03 31](https://github.com/A-Shubhi/DA353_IoT_Team5/assets/95135448/16b8d2c6-5c31-4d8a-864f-05b4b5219527)

-When device stays irresponsive for more than 24 hours, an email will be sent to check on the device.
![Screenshot 2024-04-28 185055](https://github.com/A-Shubhi/DA353_IoT_Team5/assets/95135448/bf72cd5d-b3cc-4641-a8ee-dc185e242a96)



