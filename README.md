# FleetBook — Azure Serverless Vehicle Booking System

## Project Overview
This project is a serverless vehicle booking system developed for CST8917 Lab 3. It utilizes Azure Service Bus, Logic Apps, and Azure Functions to process booking requests through a decoupled, asynchronous architecture.

## Architecture Flow
1. **Web Client (HTML/JS):** Sends booking data to an Azure Service Bus Queue.
2. **Logic App:** Triggered by the Queue message, decodes the data, and sends it to an Azure Function.
3. **Azure Function:** Validates availability (Ottawa = Success, Montreal = Failure).
4. **Logic App Branching:** - **True:** Sends confirmation email and publishes to `confirmed-sub` Topic.
   - **False:** Sends rejection email and publishes to `rejected-sub` Topic.

## Demo Video
[PASTE YOUR YOUTUBE LINK HERE]

## Setup Instructions
1. Clone the repository.
2. Deploy the `function_app.py` to an Azure Function App (Python 3.11+).
3. Configure the Service Bus Namespace with a Queue named `booking-queue` and a Topic named `booking-results`.
4. Create two subscriptions for the Topic: `confirmed-sub` and `rejected-sub`.
5. Import and configure the Logic App using the provided workflow logic.
6. Open `client.html` and enter your Service Bus Namespace and SAS Primary Key.

## Security Note
Real SAS keys and connection strings have been excluded. See `local.settings.example.json` for required configuration keys.
