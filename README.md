# Submission Machine Learning Google Cloud

This repository is a full-stack machine learning solution for skin cancer detection, utilizing Google Cloud for backend services and a web-based frontend for user interaction.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Backend](#backend)
- [Frontend](#frontend)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Endpoints](#endpoints)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

**Submission-MachineLearning-GoogleCloud** is a web application that allows users to upload skin lesion images and get predictions (Cancer/Non-cancer) using a machine learning model deployed on Google Cloud. The backend is powered by Node.js and TensorFlow.js, while results and history are stored on Google Firestore.

## Features

- **Image Upload:** Users can drag-and-drop or select images for analysis.
- **Skin Cancer Detection:** Predicts whether a lesion is cancerous or not using a trained ML model.
- **Suggestions:** Provides actionable recommendations based on the prediction.
- **Prediction History:** Stores and retrieves previous prediction results.
- **Google Cloud Integration:** Uses Firestore for persistent data storage.
- **Responsive Frontend:** Built with vanilla JS, HTML, and CSS.

## Architecture

```
Frontend (Asclepius)
    |
    v
Backend (Node.js, TensorFlow.js) -- Google Cloud Firestore
    ^
    |
User
```

- **Frontend:** Handles user interactions, image upload, and displaying results.
- **Backend:** Handles inference, validation, and data storage.

## Backend

- Built with Node.js and Hapi.js.
- Loads a TensorFlow.js model for inference.
- Accepts image uploads, performs predictions, and stores results in Firestore.
- Provides endpoints for prediction and retrieving history.

### Key Files

- `Backend/src/server/server.js` - Server entry point.
- `Backend/src/services/inferenceService.js` - Prediction logic.
- `Backend/src/services/storeData.js` - Firestore integration.

## Frontend

- Located in `Frontend/asclepius/`.
- Clean drag-and-drop interface for uploading images.
- Shows prediction results and suggestions.

### Key Files

- `Frontend/asclepius/index.html` - Main HTML file.
- `Frontend/asclepius/src/scripts/main.js` - Handles UI and API calls.
- `Frontend/asclepius/src/scripts/api.js` - Communicates with the backend.

## Setup & Installation

### Prerequisites

- Node.js 18+
- Google Cloud account with Firestore access
- Docker (optional, for containerization)

### Backend Setup

```bash
cd Backend
npm install
# Set environment variable MODEL_URL to point to your model location
npm run start
```

Or use Docker:

```bash
docker build -t skin-cancer-backend .
docker run -p 8080:8080 --env MODEL_URL=<model_url> skin-cancer-backend
```

### Frontend Setup

No build step is required. Open `Frontend/asclepius/index.html` in your browser or serve it via any static file server.

## Usage

1. Open the frontend in your browser.
2. Drag and drop or select a skin image.
3. Click "Predict".
4. View the result and suggestion.

## Endpoints

### `POST /predict`

- **Description:** Upload an image and get a prediction.
- **Payload:** `multipart/form-data` with an `image` file.
- **Response:** JSON containing the prediction result and suggestion.

### `GET /predict/histories`

- **Description:** Retrieve all past prediction results.

## Contributing

Feel free to open issues or submit pull requests for improvements and new features!

## License

This project is open source and available under the [MIT License](LICENSE).

---

**Asclepius** - Automated skin cancer detection system.
