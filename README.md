# local-LLM-ui

This repository contains a reference implementation of a lightweight and friendly AI assistant, designed to run locally without requiring a GPU or cloud services.

While originally created as a secretary AI, it can be adapted for various other use cases, such as customer support, knowledge retrieval, or general AI-powered interactions. 

Additionally, it supports deployment on an Apache local server, allowing the AI to be accessible over the internet if needed.


**Live Demo**: Access the chatbot hosted on an Apache server, running on a MacBook here: [https://home.tago.so/ai/](https://home.tago.so/ai/)

![images/CleanShot%202025-01-27%20at%2023.43.10%402x.png](https://github.com/tagoso/secretary-AI/blob/e7e42d0d5aa8b4f46bcad95a85e96c7fc4737aff/images/CleanShot%202025-01-27%20at%2023.43.10%402x.png)

---

## How to Use

### 1. Clone the Repository

```bash
git clone <repository_url>
cd <repository_folder>
```

### 2. Set Up Environment Variables

1. Create a `.env` file based on `.env.example`:
   ```bash
   cp .env.example .env
   ```
2. Update the `.env` file with the necessary values:
   - `ALLOWED_ORIGIN`
   - `GENERATE_API_URL`
   - `MODEL_NAME`
   - `PORT`

### 3. Install Dependencies

```bash
npm install
```

### 4. Start the Backend Server

```bash
node server.js
```

### 5. Set Up Ollama

- Ensure **Ollama** is installed and running locally.
- Load the required model:
  ```bash
  ollama create <model_name> -f <path_to_Modelfile>
  ```
- **This is the fun part** -- Customize the Modelfile to suit your preferences. Edit the file to define behavior, rules, or responses specific to your needs before creating the model. You can also modify the temprature and other parameters.

### 6. (Optional) Configure Apache

- Install and configure Apache to serve the frontend (`ollama-frontend`) at your desired domain or subdomain.
- For basic setup:
  - Ensure you have Apache installed on your system.
  - Edit your httpd.conf file to include a <VirtualHost> block pointing to the frontend directory.
- (Optional) Set up SSL/TLS for secure communication using Let's Encrypt or similar tools.
  - Use mod_ssl for enabling HTTPS.
  - Generate certificates with a tool like certbot.

### 7. Access the Frontend

Navigate to:

```
http://localhost:<PORT>
```

Replace `<PORT>` with the value specified in your `.env` file.

### 8. Test the AI Assistant

Use the chat interface to interact with your AI secretary. Sample questions are available to help you get started.

---

## Features

- **Lightweight AI Assistant**: Powered by the Mistral 7B language model.
- **Secure Backend API**: Ensures safe handling of user queries.
- **Interactive Web Interface**: Provides real-time responses through a sleek chat UI.

---

## Project Overview

A friendly AI secretary designed to keep your life organized. This humble yet efficient assistant:

- Runs entirely on a macOS laptop (no GPU or cloud required).
- Delivers clear, concise responses with minimal hallucinations.
- Embraces occasional harmless mistakes with charm. 😉

### Key Components

#### Backend

- Built with **Node.js** and **Express.js**.
- Security features include:
  - **Helmet** for secure headers.
  - **Domain-restricted CORS**.
  - **Rate limiting**.
  - **Request logging**.

#### Frontend

- Interactive chat interface built with **HTML**, **CSS**, and **JavaScript**.
- Real-time query and response functionality.

#### AI Model Integration

- Uses a custom Modelfile for behavior and rules configuration.
- I have confirmed that it runs smoothly on **Mistral 7B**, but you are free to use other models. However, in that case, you will need to make modifications to the Modelfile.

---

## Deployment

- **Local macOS Environment**:
  - Runs seamlessly on a macOS laptop without requiring a GPU or cloud resources.
- **Self-Contained Hosting**:
  - Backend and frontend are designed for standalone deployment.
- **Scalable**:
  - Optimized for potential production extension.

---

## License

This project is licensed under the **Apache License 2.0**. See the `LICENSE` file for details.
