# OTA Updates for ESP32 via Web Platform

This project outlines the process for performing Over-The-Air (OTA) updates to upload code to an ESP32 microcontroller through a web-based platform. Below is a summary of the workflow, including user authentication, code compilation, and firmware updates.

## Overview
The process involves registering an ESP32-based device (e.g., a bot) on a server, writing and compiling code in a web editor, and uploading the compiled `.bin` file to the ESP32 over the internet. An initial wired upload is required to configure the ESP32 for OTA updates.

[View the detailed OTA Update Process (PDF)](./ota.pdf)

## Steps

### 1. User Authentication
- **Register the Device**: Obtain the product ID (e.g., `bot_001`) and password (e.g., `12345`) for your ESP32-based bot.
- **Log In**: Use these credentials to register and log into the web platform.
- The platform's database stores attributes like `product_id` and `password`.

### 2. Access the Programming Environment
- **Log In to Platform**: Use the registered credentials to access the coding environment.
- **Configure Network Access**: Enter the SSID (network name) and password to allow the ESP32 to connect to the user's internet.
- **Coding Interface**: Write code in the provided editor, with options to compile and upload the code.

### 3. Backend Compilation
- **Code Submission**: The code is sent from the frontend to the backend via HTTP requests.
- **Compilation**: The backend uses `arduino-cli` to compile the code and generates a `.bin` file.
- **Download Link**: A static download link (e.g., `http://127.0.0.1:5000/bot_001.ino.bin`) is created for the compiled file.

### 4. Uploading Code to ESP32
- **Fetch Binary**: The ESP32 connects to the internet using the user's network credentials and retrieves the `.bin` file from the server using the generated link.
- **Upload**: The firmware is updated on the ESP32 with the new code.

### 5. Initial Firmware Setup
- **Wired Upload**: Perform an initial wired upload to configure the ESP32 with the user's internet credentials and the static download link.
- **Trigger Update**: Press the trigger button on the ESP32 to fetch and apply OTA updates from the internet.

## Prerequisites
- ESP32-based device (e.g., a bot).
- Internet connection with SSID and password.
- Web platform account with registered product ID and password.
- `arduino-cli` installed on the backend server for code compilation.

## Notes
- Ensure the ESP32 is configured for OTA updates during the initial wired setup.
- The platform's backend must be running to compile code and serve `.bin` files.

For a detailed explanation, refer to the [OTA Update Process PDF](./ota.pdf).
