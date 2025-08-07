# Smart Home Environmental Monitoring System

This project is a smart home system built with an Arduino-based sensor array and the N8N workflow automation tool. It monitors environmental conditions and provides intelligent, AI-powered notifications.

## Features

* **Multi-Sensor Data Collection:** The system collects data from a variety of sensors, including temperature, humidity, gas levels, light, and barometric pressure.
* **Wi-Fi Connectivity:** An ESP8266 module is used to send sensor data to a webhook.
* **AI-Powered Analysis:** The N8N workflow utilizes the Google Gemini Chat Model through an "AI Agent" node to analyze sensor data and provide smart, contextual advice.
* **Conditional Workflows:** The `If` node in the workflow allows for different paths based on the sensor data, enabling separate responses for normal conditions versus critical alerts.
* **Data Logging:** The "Get row(s) in sheet in Google Sheets" tool is integrated to log all sensor data for long-term analysis and historical tracking.
* **Automated Notifications:** The final stage of the workflow sends the AI-generated analysis as a notification (e.g., via Telegram).
* **Flexible and Modular:** The N8N workflow is highly customizable and can be easily expanded with new sensors or services.

## Hardware Components

* Arduino Uno
* Breadboard
* ESP8266 Wi-Fi Module
* DHT11 Temperature & Humidity Sensor
* MQ-2 Gas Sensor
* BH1750 Ambient Light Sensor
* BMP280 Barometric Pressure Sensor
* Jumper Wires

## Software Requirements

* **Arduino IDE:** To program the microcontroller.
* **N8N:** For workflow automation.
* **Google Gemini API:** For AI analysis.
* **Google Sheets:** For data logging.
* **Telegram:** For notifications.

## Setup

### 1. Hardware Setup
Wire the sensors and the ESP8266 module to your Arduino using a breadboard. Refer to the circuit diagrams created for this project for detailed pin connections.

### 2. Arduino Code
Upload the Arduino code to your board. Ensure you update the code with your Wi-Fi credentials and the N8N Webhook URL to enable data transmission.

### 3. N8N Workflow
Import or build the N8N workflow shown in the attached images. The workflow consists of the following key nodes:
1.  **Webhook:** Listens for incoming data from the Arduino.
2.  **If:** Routes the data based on conditions (e.g., gas sensor value).
3.  **AI Agent:** Analyzes the sensor data using the Google Gemini model.
4.  **Get row(s) in sheet in Google Sheets:** Logs the sensor data for historical tracking.
5.  **Send Message:** Sends the final analysis as a notification.

## How It Works

1.  The Arduino collects data from all connected sensors.
2.  The ESP8266 sends this data to the N8N Webhook via an HTTP GET request.
3.  The N8N workflow is triggered and the `If` node directs the data to the appropriate `AI Agent` based on the sensor readings.
4.  The `AI Agent`, powered by Google Gemini, analyzes the data and provides a detailed summary or a critical alert.
5.  The analysis is then logged to a Google Sheet and sent as a message to your chosen notification service.
