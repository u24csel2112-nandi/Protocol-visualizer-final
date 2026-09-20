# Assignment Reflection Document

**Project:** Dual-Panel Activity & Protocol Visualizer
**Author:** [Your Name / Student ID]
**Date:** [Date]

## 1. AI Platform and Model Used
For this assignment, I utilized **Google Antigravity** (powered by **Gemini 3.1 Pro (High)**). I chose this platform because of its deep integration with local development environments, its ability to quickly bootstrap full-stack Python + FastAPI applications, and Gemini 3.1 Pro's high proficiency in writing structured state machines (needed for the animated protocol visualizer).

## 2. Synchronization of the Two Panels
The application maintains a dual-panel layout where the left panel dictates user intent and the right panel acts as a reactive visualization surface. 
- **State Machine Implementation:** The frontend uses Vanilla JavaScript. When a user clicks "Visit Page" or "Send Email", a `startSimulation()` function is fired which extracts the form parameters (URL, Email, Quality).
- **Protocol Generation:** It immediately generates a linear sequence array representing the exact protocol messages (e.g., DNS -> HTTP, or DNS -> SMTP) based on those inputs.
- **Timing and Animation:** A `setInterval` loop sequentially injects these message nodes into the DOM of the right panel, appending them to the visualizer area every 1.5 seconds.
- **Controls:** Pause, Play, Next, and Previous controls interact directly with this sequence iterator, allowing real-time step-by-step examination of the protocol flow.

## 3. AI Adjustments and Corrections
During development, the AI initially attempted to generate static mockups without clear progression logic.
- **Correction:** I specifically requested an animated sequence with "step forward/backward" functionality. The AI updated the script to use a JavaScript interval-based state machine.
- **Protocol Accuracy:** The AI originally omitted the `DNS MX` lookup for the Mail sequence, jumping straight into SMTP. I corrected this behavior to ensure a realistic depiction of how mail clients first resolve the Mail Exchange server before sending an EHLO.
- **Segmented Streaming:** I ensured the AI differentiated the streaming sequence from a standard HTTP request by forcing it to request an `.m3u8` manifest file followed by `.ts` video chunks, accurately simulating HLS (HTTP Live Streaming) behavior over standard HTTP ports.

## 4. Key Differences Observed Between Protocol Flows
- **DNS + HTTP (Browsing):** The flow is strictly request-response. A single DNS A-record lookup is followed by a stateless HTTP GET. The transaction is brief, terminating as soon as the HTML payload is delivered.
- **SMTP (Mail):** In contrast to HTTP, SMTP is a highly stateful, conversational protocol. It requires a lengthy handshake (`EHLO`), explicit envelope definitions (`MAIL FROM`, `RCPT TO`), and a specific terminal sequence (`<CR><LF>.<CR><LF>`) to indicate the end of data before formally closing the connection with `QUIT`.
- **HTTP Streaming:** While it uses the same underlying stateless HTTP protocol as browsing, streaming acts like a continuous polling mechanism. Instead of one large response, it fetches a playlist (manifest), then sequentially issues multiple HTTP GET requests for individual binary segments (`segment1.ts`, `segment2.ts`), allowing the client to adjust bandwidth mid-stream.
