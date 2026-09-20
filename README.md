# Protocol Visualizer Dashboard

This is a standalone web dashboard that allows a user to perform common application-layer activities (Browsing, Mail, Streaming) and simultaneously visualizes the underlying protocol exchanges (DNS, HTTP, SMTP) in real time.

## How to Run

This project has been bundled into a single "pure frontend" file for your convenience! You do not need a server or Python to run it.

1. Simply double-click on `Protocol_Visualizer.html` to open it in your web browser.

## Features
- **Dual-Panel Layout:** Actions on the left, live protocol visualization on the right.
- **Three Activities Supported:**
  - **Browsing:** Visualizes DNS and HTTP (GET Request & Response).
  - **Mail:** Visualizes DNS (MX) and complete SMTP conversation (EHLO, MAIL FROM, RCPT TO, DATA, QUIT).
  - **Streaming:** Visualizes DNS and HTTP streaming sequences (Manifest + Segments).
- **Controls:** Fully pause, replay, and step through the protocol messages.

## Demo Video & Submission
*Remember to record your 2-4 minute demo video highlighting the dual-panel synchronization as per the assignment guidelines.*
