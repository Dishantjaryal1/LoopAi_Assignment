# Data Ingestion API

A simple API system built with **Node.js** and **Express** to demonstrate handling asynchronous batch processing, priority-based queueing, and rate limiting.

---

## Overview

This project implements two RESTful APIs:

1. **Ingestion API** (`POST /ingest`):  
   Accepts a list of IDs and a priority level, splits the IDs into batches of 3, and processes them asynchronously with respect to priority and rate limiting.

2. **Status API** (`GET /status/:ingestion_id`):  
   Returns the current processing status of a given ingestion request, including detailed batch statuses.

---

## Features

- **Batch processing**: Only 3 IDs processed concurrently in each batch.
- **Priority-based processing**: Higher priority batches are processed before lower priority ones.
- **Asynchronous handling**: Batches are queued and processed in the background.
- **Rate limiting**: Processes only 1 batch every 5 seconds.
- **In-memory persistence**: Stores ingestion and batch statuses for status tracking.
- **Simulated external API calls**: Mocks external API delay and response without real calls.

---

## API Details

### 1. Ingestion API

- **Endpoint**: `POST /ingest`
- **Input**:
  ```json
  {
    "ids": [1, 2, 3, 4, 5],
    "priority": "HIGH"
  }

## 2. Status API

- **Endpoint**: `GET /status/:ingestion_id`
- **Input**:  
  The `ingestion_id` returned by the ingestion API in the URL path.

- **Behavior**:  
  Retrieves the current processing status of the ingestion request, including the statuses of all batches associated with that ingestion.

- **Output**:  
  ```json
  {
    "ingestion_id": "abc123",
    "status": "triggered",
    "batches": [
      {
        "batch_id": "<uuid>",
        "ids": [1, 2, 3],
        "status": "completed"
      },
      {
        "batch_id": "<uuid>",
        "ids": [4, 5],
        "status": "triggered"
      }
    ]
  }

## Testing 

![Screenshot 2025-06-05 120140](https://github.com/user-attachments/assets/4fdd688c-d69a-4e90-a649-57bbecd734f9)


## deployment link
[click here](https://loopaiassignment-production-86a2.up.railway.app/)
