# GitHub Webhook Processor & UI
A simple Full-Stack implementation to capture, store, and display GitHub events (Push, Pull Request, Merge) in real-time. This project uses a polling mechanism to update the UI every 15 seconds without re-displaying old data.

# The Tech Stack
Backend: Flask (Python)

Database: MongoDB

Frontend: Vanilla JS, HTML, CSS

Tunneling: ngrok (for local testing of GitHub payloads)

# Key Logic
Deduplication: Uses a MongoDB Unique Index on the X-GitHub-Delivery ID to ensure the same webhook isn't stored twice.

Efficient Polling: The frontend tracks a lastTimestamp and only requests events from the Flask API that are newer than that marker using the $gt operator.

Formatting: Custom Python/JS logic to convert ISO timestamps into a human-readable format (e.g., 30th January 2026).

# Local Setup
Install dependencies: pip install flask pymongo

Database: Ensure MongoDB is running locally or provide a Mongo Atlas URI in app.py.

Run the server: python app.py

Expose the port: ngrok http 5000 (Use the generated URL in your GitHub Webhook settings).
