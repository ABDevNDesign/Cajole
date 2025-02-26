<!-- File: DESIGN.md -->
# Design & Architecture

This document details the design and architecture of the Streaming Widget.

## Overview

The widget is structured into several key components:

1. **Fundraising Goal Bar**  
   - **Purpose:** Displays the current campaign progress.
   - **Behavior:** Automatically updates when a new backing is received.  
   - **Stretch Goals:** If the fundraising goal is reached, a stretch goal bar appears underneath. Up to three stretch goals can be displayed sequentially.

2. **Backing Alerts**  
   - **Purpose:** Notify viewers each time someone backs the campaign.
   - **UI Elements:**  
     - Displays Nigel’s mascot on the left.
     - Shows the donation amount (e.g., `$XX`) and the backer’s username.
     - For Twitch users, ensures that only the Twitch username is shown.
   - **Styling:**  
     - The most recent backing alert appears in a green bubble (`#28bf2c`).
     - The two previous alerts are displayed in yellow bubbles (`#FDDE06`).

3. **Countdown Clock**  
   - **Purpose:** Activates when the campaign is in its final 24 hours.
   - **Display:** Shown below the current goal bar (or stretch goal bar) during this period.

4. **QR Code**  
   - **Purpose:** Provides a scannable QR code that includes a design element featuring Nigel’s face.
   - **Use Case:** Can be displayed separately on the stream.

5. **Leaderboard**  
   - **Purpose:** Replicates the live leaderboard from the campaign page.
   - **Behavior:** Continuously updates to reflect the latest standings.

## Technical Considerations

- **Data Synchronization:**  
  The widget should poll or subscribe to real-time data updates from the campaign page to keep the displayed information current.
  
- **Integration:**  
  Designed to work as a browser source for streaming software (OBS, Streamlabs, etc.). Consider cross-browser compatibility and performance.

- **Customization:**  
  Users must be able to input their campaign URL to fetch data, ensuring the widget is dynamic and reusable.

---

