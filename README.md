# greenfeast
# Smart Food Waste Monitoring System 🍽️🚨

A computer vision system that detects food waste, identifies the person responsible, and sends automated SMS alerts with payment links.

## Features ✨

- **Face Recognition** 👤: Identifies individuals using MediaPipe
- **Food Detection** 🍛: Uses YOLOv8 to detect and quantify food items
- **Waste Calculation** 📊: Estimates wasted food by comparing before/after plate states
- **Automated Alerts** 📱: Sends SMS notifications via Twilio with:
  - Waste details
  - Fine amount (₹0.10 per gram)
  - UPI payment QR code
- **Real-time Monitoring** 📹: Processes live camera feed with OpenCV

## System Architecture 🏗️

```mermaid
graph TD
    A[Camera Input] --> B{Face Detection}
    B -->|Detected| C[Person Identification]
    B -->|Not Detected| D[Continue Monitoring]
    C --> E[Initial Plate Scan]
    E --> F[Food Quantification]
    F --> G[Monitor Consumption]
    G --> H{Significant Waste?}
    H -->|Yes| I[Send SMS Alert]
    H -->|No| G
    I --> J[Generate Payment QR]
