# 🚴 Aixle

**Aixle** is an automated, open-source cycling coach powered by **Google Gemini AI** and **Intervals.icu**.

It acts as the "axle" of your training—analyzing your data and driving your performance forward. Every morning, Aixle calculates your fatigue and training phase, then authors a custom **Zwift workout (.zwo)** tailored specifically to your goal.

## ✨ Features

*   **Smart Periodization:** Automatically determines if you are in Base, Build, or Peak phase based on your target race date.
*   **Daily AI Generation:** Creates engaging workouts (Pyramids, Over-Unders) with embedded text instructions, tailored to your daily TSB (Fatigue).
*   **Context Aware:** Pushes you when you're fresh, protects you when you're tired.
*   **Zwift Compatible:** Generates standard `.zwo` files with cadence targets and motivational messages.
*   **Auto-Sync:** Includes a script to sync workouts from Google Drive to Zwift automatically.

## 🛠 Prerequisites

1.  **Google Account** (for Gemini API, Sheets, Drive).
2.  **Intervals.icu Account** (for fitness data).
3.  **Zwift** (PC/Mac recommended for auto-sync).

## 🚀 Quick Start

### 1. Get API Keys
*   **Intervals.icu:** Settings -> Developer -> API Key.
*   **Gemini API:** [Google AI Studio](https://aistudio.google.com/).

### 2. Install Script
1.  Create a Google Sheet and open `Extensions` > `Apps Script`.
2.  Copy `Code.gs` from this repository.
3.  Configure the `USER_SETTINGS` at the top:
    ```javascript
    const USER_SETTINGS = {
      LANGUAGE: "en",
      GOAL_DESCRIPTION: "Increase FTP by 10W",
      TARGET_DATE: "2026-06-01",
      WORKOUT_FOLDER: "Aixle_Workouts", // Folder created in Google Drive
      // ...
    };
    ```

### 3. Automate
Set Apps Script triggers to run `fetchAndLogActivities` at 2:00 AM and `generateOptimalZwiftWorkoutsAutoByGemini` at 6:00 AM.

### 4. Sync
#### For Windows Users (Aixle Sync Agent)
Use the included `WatchZwiftZwo.ps1` script. It will automatically create an **"Aixle"** category inside Zwift and sync your workouts there.

1.  Install **Google Drive for Desktop**.
2.  Open `WatchZwiftZwo.ps1` with a text editor and update the top configuration:
    ```powershell
    $sourceFolder = "G:\My Drive\Aixle_Workouts" # Your Google Drive path
    $zwiftId = "123456"                          # Your Zwift ID
    ```
3.  Right-click the file and select "Run with PowerShell".
    *   You will see a new folder named "Aixle" in your Zwift workout selection screen.

## ⚠️ Disclaimer
Aixle is an experimental tool. Use the generated workouts at your own risk.

## License
MIT License
