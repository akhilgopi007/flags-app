# Flag Master Pro: App Documentation

## 1. Project Overview
**Flag Master Pro** is a lightweight, mobile-first Single Page Application (SPA) designed to help a 4-year-old learn world flags through visual recognition, phonics, and auditory reinforcement. It is designed to run offline and is optimized for iPad (iPadOS 26.1) and mobile browsers.

## 2. Technical Stack
* **Frontend:** Vanilla HTML5, CSS3, and JavaScript (ES6+).
* **Hosting:** Designed for GitHub Pages (`akhilgopi007.github.io/flags-app`).
* **External Assets:** Fetches flag images dynamically from **FlagCDN** (no local storage required).
* **Audio/Voice:** Uses the built-in **Web Audio API** for sound effects and **Web Speech API** for text-to-speech.

## 3. Core Features

### A. Learning Modes
The app automatically toggles between two primary modes:
1.  **Identify Mode:** Shows a large flag image; the user selects the correct country name from four text buttons.
2.  **Find Mode:** Provides a country name via text and voice; the user selects the correct flag from a grid of four flag images.

### B. Phonics Integration
Designed for a child who cannot yet read full words:
* **Visual Cues:** The first letter of country names in text buttons is enlarged, bolded, and colored differently (`--accent`).
* **Unique Options Logic:** In Identify mode, the app ensures all four multiple-choice options start with **different letters** (e.g., if the answer is "India," no other "I" countries will appear).

### C. Voice & Audio Engine
* **Voice Feedback:** The app speaks the country name when a text button is clicked (Identify mode) or when a round starts (Find mode).
* **Voice Selector:** Includes an admin dropdown to choose between available system voices, prioritizing "Premium," "Enhanced," or "Siri" voices for natural speech.
* **SFX:** Synthesized chimes for correct answers and low-pitched thuds for errors using the Web Audio API.

### D. Gamification & Discipline
* **Hearts System:** Users start with 5 hearts (lives); a wrong answer grays out a heart using CSS filters and opacity for iPad compatibility.
* **Permanent Game Over:** When all lives are lost, a "Game Over" screen overlays the UI with no restart button, requiring a page refresh.
* **Smart Rotation:** Implements a history queue to prevent immediate repetition; a country will not reappear until at least 40% of the active flag pool has been shown.

### E. Admin Panel (Settings)
Accessible via a ⚙️ icon:
* **Flag Library:** A searchable list of 250+ ISO-standard countries with flag thumbnails.
* **Persistence:** Selections and voice preferences are saved to the browser's `localStorage`.
* **Force Voice Sync:** A utility button to refresh the browser's voice list, crucial for Safari/iPadOS background loading quirks.

## 4. Layout & UI
* **Mobile-First:** Uses a responsive grid and `max-height` capping to ensure all buttons remain visible on iPad screens without scrolling.
* **Tap Targets:** Large buttons and `touch-action: manipulation` settings prevent accidental zooming or double-taps.
* **Visual Feedback:** A CSS-based confetti celebration triggers on correct answers.

## 5. Persistence Data Structure
The app relies on `localStorage` for two keys:
1.  `selectedFlags`: An array of country names (strings) currently enabled for the game.
2.  `preferredVoiceName`: The name of the `SpeechSynthesisVoice` selected by the user.