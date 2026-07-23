# Node.js Express & Redis Caching Demo

A lightweight, professional backend application showcasing how to implement a high-performance **Redis caching layer** in an Express.js application using `ioredis`. 

API response caching reduces network latency, minimizes calls to external service providers, and prevents hitting API rate limits.

---

## 🚀 Features

*   **Redis Connection Pool:** Centralized client setup using the powerful and robust `ioredis` library.
*   **Simple Key-Value Cache:** Script demonstrating basic Redis set, get, and key-expiry operations.
*   **API Response Caching:** Integration with an Express.js server to cache external REST API endpoints with a configured **Time-To-Live (TTL)**.

---

## 🛠️ Project Structure

*   [`client.js`](./client.js) - Sets up and exports the Redis connection client.
*   [`string.js`](./string.js) - Interactive test script showcasing basic string write/read operations.
*   [`server.js`](./server.js) - Express web server exposing a GET route that caches external API results with a 30-second TTL.
*   [`package.json`](./package.json) - Contains project metadata and npm dependency list (`express`, `ioredis`, `axios`).

---

## 📋 Prerequisites

Before running the application, ensure you have the following installed on your system:
*   [Node.js](https://nodejs.org/) (v16 or higher recommended)
*   [Redis Server](https://redis.io/downloads/) running locally on the default port `6379`.

---

## ⚙️ Installation

1. Clone or navigate to the repository directory:
   ```bash
   cd redis
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

---

## 🏃 Running the Application

### 1. Test Basic Redis Operations
Run the script to verify that your Node.js application can successfully connect and read/write to the Redis server:
```bash
node string.js
```
*Expected console output:*
```text
Result Heloo from Redis
```

### 2. Start the Express Caching Server
Start the web server:
```bash
node server.js
```
The server will start listening on port `9000`.

### 3. Test Caching In Action
Open your browser or run a curl command to hit the main endpoint:
```bash
curl http://localhost:9000/
```
*   **First Request:** The server fetches mock todo data from the external `jsonplaceholder.typicode.com` API, saves the response to Redis with a 30-second TTL, and returns it.
*   **Subsequent Requests (within 30s):** The server retrieves the cached data instantly from your Redis memory, completely bypassing the external API request.
