⏳ Chronos Core — Minimalist Date & Countdown Tracker

Chronos Core is a lightweight, high-fidelity, single-page web application designed for tracking personal target dates and milestones in an immersive, distraction-free environment.

Featuring a modern dark-mode design system with glassmorphism effects, a glowing ambient backdrop, and a live-updating countdown display showing DD : HH : MIN : SEC, the application seamlessly guides you from a configuration screen to a beautifully simple full-screen tracking display.

✨ Key Features

Double-Screen Architecture: Fluid transition from a setup control panel to an absolute, distraction-free countdown presentation.

Accurate "DD : HH : MIN : SEC" Formatting: Traditional digital clock colon-separators with an animated pulse loop.

Strict Local Midnight Parsing: Eliminates timezone offsets and browser discrepancy bugs by converting date inputs strictly into local midnight (00:00:00) of the target day.

Responsive Fluid Layouts: Optimally scaled and padded for mobile touchscreens, tablets, and full-resolution desktops.

Lightweight & No Dependencies: Written in 100% pure vanilla HTML, modern CSS3, and native JavaScript—no frameworks or external libraries required.

📂 Project Structure

The project has an intentionally minimalist structure, ideal for lightning-fast loading speeds and easy free hosting:

├── index.html         # Main app containing UI, CSS styles, and JavaScript engine
└── README.md          # Documentation (This file!)


📐 How the Code Works (Under the Hood)

1. Timezone-Safe Date Parsing

Normally, parsing a raw date string directly via new Date("YYYY-MM-DD") treats the input as UTC midnight, which shifts the actual countdown target day depending on your local timezone. Chronos Core resolves this by splitting the string manually and initializing the local midnight instance:

const dateParts = dateInput.split('-'); // e.g. ["2026", "12", "31"]
const targetDate = new Date(
    parseInt(dateParts[0], 10),      // Year
    parseInt(dateParts[1], 10) - 1,  // Month Index (0-based)
    parseInt(dateParts[2], 10),      // Day
    0, 0, 0, 0                       // Hours, Mins, Secs, Ms (Midnight)
);


2. Time Conversion Math

JavaScript timestamps are measured in milliseconds. The app calculates the difference between your target date and the current time, then converts it down to standard units using the modulo operator (%):

const msInDay = 1000 * 60 * 60 * 24;
const msInHour = 1000 * 60 * 60;
const msInMinute = 1000 * 60;
const msInSecond = 1000;

const days = Math.floor(diffMs / msInDay);
const hours = Math.floor((diffMs % msInDay) / msInHour);
const minutes = Math.floor((diffMs % msInHour) / msInMinute);
const seconds = Math.floor((diffMs % msInMinute) / msInSecond);


📝 License

This project is open-source and available under the MIT License. Feel free to customize, modify, or expand the code for your own projects!
