# Lightweight Gardening Application Plan

This document outlines a plan for developing a lightweight, personal gardening application that you can access on both your phone and PC. The plan details the design choices, tech stack, data model, and development order.

---

## 1. Overview

The goal is to create a personal seed and plant management tool for your vegetable garden. You will be able to enter data about various seeds, including:

- **Plant Name**
- **Seed Count**
- **Shelf Life**
- **Pre-germination Dates (indoor)**
- **Transplanting Dates**
- **Direct Sowing Dates (in the field)**
- **Harvest Dates**

Additional attributes include:

- **Sun Exposure:** (Full Sun, Partial Shade, or Shade)
- **Soil Type:** (Sandy, Loamy, or Clayey)
- **Water Needs:** (Low, Medium, or High)
- **Plant Spacing:** (In-row and between rows)
- **Frost Hardiness:** (Boolean)
- **Companion Planting:** (Other plants that work well together)

Since this application is for your personal use, you prefer not to host it on a server or incur any hosting costs.

---

## 2. Tech Stack and Architecture

### Front-End Framework
- **Vue.js:** A lightweight framework well-suited for small projects.
- *Alternative:* **React** is an equally viable option if you prefer its ecosystem.

### HTML5 & CSS3
- **Responsive Design:** Use frameworks like **Bootstrap 5** or **Tailwind CSS** to ensure the interface adapts well to both phones and PCs.

### Data Persistence
- **IndexedDB:** Use this for storing complex data objects, with a wrapper like **Dexie.js** for easier manipulation.
- *Note:* LocalStorage is an option, but it has limitations regarding capacity and data structure.

### Build Tools
- **Vite** or **Webpack:** For bundling JavaScript and optimising performance (this step is optional if the project remains simple).

### Optional Enhancements
- **Data Backup:** Implement features for data export/import (e.g., JSON) for backups.

---

## 3. Development Roadmap

### Step 1: Requirements Gathering & Analysis
- **Document Features:** Define input fields for plant name, seed count, shelf life, multiple month selections for sowing stages, sun exposure, etc.
- **User Stories:** For example, "As a user, I want to mark multiple months for transplanting so that I can plan my garden effectively."

### Step 2: Data Model Design
- **Define Schema:** Each seed entry might include:
  - `plantName`: String
  - `seedCount`: Number
  - `shelfLife`: Date (or a formatted string)
  - `preGerminationMonths`: Array of integers (month indices)
  - `transplantingMonths`: Array of integers
  - `directSowingMonths`: Array of integers
  - `harvestMonths`: Array of integers
  - `sunExposure`: Enum (e.g., "Full Sun", "Partial Shade", "Shade")
  - `soilType`: Enum (e.g., "Sandy", "Loamy", "Clayey")
  - `waterNeeds`: Enum (e.g., "Low", "Medium", "High")
  - `inRowSpacing`: Number (e.g., centimetres)
  - `betweenRowsSpacing`: Number
  - `isFrostHardened`: Boolean
  - `companionPlants`: Array of strings
- **Pre-define Options:** Ensure all choices are predetermined and not left to be decided later.

### Step 3: UI/UX Design & Wireframing
- **Layout Design:** Sketch a simple, intuitive layout including forms for adding and editing seed entries.
- **Responsive Views:** Create designs that work on both mobile and desktop.
- **Transitional States:** For example, show a confirmation message after a new entry is submitted.

### Step 4: Set Up the Development Environment
- **Version Control:** Initialise a Git repository.
- **Project Structure:** Configure your chosen build tool and organise your components, styles, and utility functions.

### Step 5: Front-End Development
- **Build Interface:** Use your chosen framework (Vue.js or React) to develop:
  - A main dashboard for listing seed entries.
  - A form component for adding or editing entries (with dropdowns and checkboxes for multiple month selections).
- **Ensure Responsiveness:** Adjust the layout for both PC and mobile views.

### Step 6: Integrate Local Storage
- **Implement CRUD Operations:** Use IndexedDB (with Dexie.js) to manage create, read, update, and delete functions for seed entries.
- **Testing:** Ensure data storage and retrieval works correctly across different browsers.

### Step 7: Testing and Debugging
- **Manual Testing:** Verify functionality on both desktop and mobile devices.
- **Unit Testing:** Consider using Jest (or similar) for testing core functionalities such as month selection storage.

### Step 8: Optimisation and Finishing Touches
- **Performance:** Optimise by minimising unused code and implementing caching for offline use.
- **UI Enhancements:** Add animations or confirmation dialogues for a better user experience.

### Step 9: Deployment & Offline Usage
- **Static Site Deployment:** Build the application as a static site to avoid server costs.
- **Local Installation:** Provide instructions for running the app locally (e.g., opening `index.html` in a browser) or installing it as a PWA on mobile devices.

---

## 4. Alternative Considerations

- **Framework Choice:**  
  While Vue.js is recommended for its simplicity and reactivity, React remains an alternative if you are more familiar with it.

- **Storage Options:**  
  IndexedDB is preferred for handling complex data structures, but localStorage could be used for minimal data with awareness of its limitations.

- **Future Expansion:**  
  Should you decide to expand the app later (supporting multiple users or analytics), you might integrate a lightweight backend (e.g., Node.js with Express) and utilise a cloud database service.

---

## 5. Conclusion

This plan provides a clear roadmap for building a fully functional, lightweight gardening application that meets your requirements. By following these steps—from planning and wireframing to data model design, front-end development, testing, and deployment—you will have a robust personal tool for managing your garden. Feel free to adapt the plan based on your evolving needs and preferences as the development progresses.
