<!-- File: IMPLEMENTATION.md -->
# Implementation Details

This document outlines the technical approach for implementing the Streaming Widget. The widget displays live fundraising campaign data—including goal progress, stretch goals, backing alerts, a countdown timer, a QR code, and a leaderboard—in streaming software environments such as OBS, Streamlabs, Wirecast, Lightstream, and vMix.

## 1. Overview

The widget is primarily a client-side web application built with HTML, CSS, and JavaScript. It dynamically fetches data from a campaign API and updates the UI in real time.

### Key Components:
- **Fundraising Goal Bar:** Shows the progress toward the campaign goal.
- **Stretch Goals:** Displays up to three additional progress bars when the main goal is met.
- **Countdown Timer:** Activates during the final 24 hours of the campaign.
- **Backing Alerts:** Live notifications displaying the donation amount, the backer’s username, and our mascot Nigel’s face. Latest alert is highlighted in green (#28bf2c) and previous alerts in yellow (#FDDE06).
- **QR Code Display:** Shows a QR code with a custom design featuring Nigel’s face.
- **Leaderboard:** Mirrors the live leaderboard from the campaign page.

## 2. Architecture

### 2.1 Frontend
- **HTML/CSS/JS:**  
  - **HTML:** Structure for each component.
  - **CSS:** Styling based on the Figma design, ensuring responsiveness for various streaming layouts.
  - **JavaScript:** Manages dynamic behavior (e.g., progress updates, countdown timer, and real-time alerts).

- **Modular Structure:**  
  Organize the code into separate modules:
  - `goalBar.js` – Handles the main fundraising goal logic.
  - `stretchGoals.js` – Manages the display and updates for stretch goals.
  - `countdown.js` – Implements the countdown timer.
  - `backingAlerts.js` – Processes and displays backing alerts.
  - `qrCode.js` – Renders the QR code.
  - `leaderboard.js` – Updates the leaderboard data.

### 2.2 Data Integration
- **API Integration:**
  - The widget will use the campaign URL provided by the user to fetch data.
  - Real-time data can be obtained using RESTful APIs with periodic polling or via WebSocket for instant updates.
  - Ensure proper handling of API authentication and error states.

## 3. Development Workflow

### 3.1 Local Development
- **Setup:**
  - Clone the repository and install dependencies (e.g., using `npm` for package management).
  - Use a local development server (such as Node.js with Express) to serve the widget.
  
- **Build Tools:**
  - Consider using Webpack or Parcel to bundle JavaScript modules.
  - Use source maps for easier debugging.

### 3.2 Testing & Debugging
- **Local Testing:**
  - Utilize browser developer tools to simulate API responses.
  - Test UI responsiveness across different resolutions.
  
- **Integration Testing:**
  - Add the widget as a browser source in streaming software (OBS, Streamlabs, etc.) to verify its performance.
  - Monitor real-time updates and error handling under simulated network conditions.

## 4. Integration with Streaming Software

### 4.1 Browser Source Configuration
- **Setup Instructions:**
  - Deploy the widget to a publicly accessible URL (e.g., via Netlify or Vercel).
  - In OBS, add a new Browser Source and set its URL to the deployed widget.
  - Adjust dimensions (width and height) according to the stream layout.

### 4.2 Cross-Platform Considerations
- **Supported Platforms:**
  - OBS Studio
  - Streamlabs
  - Wirecast, Lightstream, vMix (similar browser source configuration)
  
- **Performance Optimization:**
  - Ensure the widget is lightweight and minimizes CPU/GPU usage during live streams.
  - Test under various network conditions to ensure seamless updates.

## 5. Error Handling & Fallbacks

### 5.1 API and Network Issues
- Implement robust error handling to manage API failures:
  - Display user-friendly error messages.
  - Retry fetching data upon transient failures.
  - Cache the most recent successful data fetch to mitigate network interruptions.

### 5.2 UI Fallbacks
- Ensure that missing data (e.g., if a campaign URL is invalid) does not break the widget layout.
- Provide default placeholders for images and text.

## 6. Deployment

### 6.1 Hosting
- **Deployment Options:**
  - Use services like Netlify, Vercel, or GitHub Pages.
  - Ensure HTTPS is enabled for secure data transfer.

### 6.2 Continuous Integration / Deployment (CI/CD)
- Set up a CI/CD pipeline to automatically deploy updates to the widget upon merging changes into the main branch.
- Monitor deployment logs to catch and resolve issues early.

## 7. Future Enhancements

### 7.1 Customization
- Allow users to customize widget colors and styles through configuration settings or external CSS overrides.
  
### 7.2 Additional Features
- Add analytics to track user interactions.
- Integrate additional social media platforms for more comprehensive backing alerts.
- Expand API support for additional fundraising platforms.

## 8. Conclusion

This document provides a roadmap for implementing the Streaming Widget. By following the outlined steps and modular approach, the widget can be efficiently developed, tested, and deployed to enhance the live streaming experience. For further questions or contribution guidelines, refer to the project's [CONTRIBUTING.md](CONTRIBUTING.md) file.

