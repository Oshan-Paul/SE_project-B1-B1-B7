Okay, here is a comprehensive README.md file tailored for your UPES Campus Navigator project (Leaflet/OSM version), incorporating all the sections you requested.

You should copy and paste the content below into a file named README.md in the root directory of your GitHub repository (E:\Downloads\CollageGpsApp\README.md). Make sure to replace placeholder paths with your actual JavaFX SDK path where indicated.

# UPES Campus Navigator (Leaflet/OSM Edition)

A desktop application developed as a Software Engineering project to provide interactive navigation within the UPES (University of Petroleum and Energy Studies) campus using open-source mapping technologies.

## Table of Contents

1.  [Problem Description](#1-problem-description)
2.  [Key Features & Functionalities](#2-key-features--functionalities)
3.  [Target Audience](#3-target-audience)
4.  [Tools & Technologies Used](#4-tools--technologies-used)
5.  [Package Dependencies / Prerequisites](#5-package-dependencies--prerequisites)
6.  [Steps to Execute the Project](#6-steps-to-execute-the-project)
7.  [SDLC Model Adopted](#7-sdlc-model-adopted)
8.  [Requirements Gathering & Validation](#8-requirements-gathering--validation)
9.  [Testing Method](#9-testing-method)
10. [Challenges Faced](#10-challenges-faced)
11. [Deployment](#11-deployment)
12. [Future Scope](#12-future-scope)
13. [Team Members & Roles](#13-team-members--roles)

---

## 1. Problem Description

Navigating large university campuses like UPES can often be challenging, especially for new students, visitors, faculty, and staff. Finding specific blocks (e.g., CIT Block, Admin Block), labs, libraries, or hostels efficiently can be time-consuming using traditional static maps or verbal directions. This project aims to provide a user-friendly digital solution for on-campus navigation.

---

## 2. Key Features & Functionalities

*   **Interactive Map Display:** Embeds a dynamic map using Leaflet.js, displaying OpenStreetMap tiles centered on the UPES campus region. Supports panning and zooming.
*   **Location Selection:** Provides dropdown menus populated with predefined key campus locations.
*   **Point-to-Point Routing:** Allows users to select a starting point and destination from the dropdowns.
*   **Visual Route Calculation:** Calculates and displays the optimal walking route between selected points directly on the map using Leaflet Routing Machine and the OSRM engine.
*   **Route Visualization:** Displays the route as a line on the map with start/end markers and provides a basic route summary (distance/time).
*   **Internal Path Reference:** Calculates an internal path sequence based on predefined campus connections (primarily displayed as text reference).
*   **Simple UI:** Desktop application interface built with JavaFX for ease of use.

---

## 3. Target Audience

*   **New Students:** Helping them familiarize themselves with the campus layout.
*   **Existing Students:** Finding specific locations they may not visit often.
*   **Faculty & Staff:** Navigating between different buildings or offices.
*   **Visitors & Guests:** Providing directions during events, admissions, or visits.

---

## 4. Tools & Technologies Used

*   **Core Language:** Java (JDK 11+)
*   **UI Framework:** JavaFX SDK (Version 11+ corresponding to JDK)
*   **Web Integration:** JavaFX WebView / WebEngine
*   **Frontend (Map):** HTML5, CSS3, JavaScript (ES6+)
*   **Mapping Library:** Leaflet.js
*   **Routing Plugin:** Leaflet Routing Machine
*   **Map Data:** OpenStreetMap (OSM) Tiles
*   **Routing Engine:** Open Source Routing Machine (OSRM) - using public demo server
*   **IDE:** Visual Studio Code (with Extension Pack for Java)
*   **Version Control:** Git / GitHub

---

## 5. Package Dependencies / Prerequisites

To compile and run this project, you need:

1.  **Java Development Kit (JDK):** Version 11 or higher (e.g., JDK 17, 21). Ensure `java` and `javac` commands work in your terminal and `JAVA_HOME` is set.
2.  **JavaFX SDK:** Version 11 or higher, compatible with your JDK version. Download from [OpenJFX](https://openjfx.io/). You **must** know the path to the `lib` folder within the extracted SDK.
3.  **Internet Connection:** Required at runtime to fetch OpenStreetMap tiles and contact the OSRM routing server.

*(Note: Leaflet.js and Leaflet Routing Machine are included via CDN links in `map.html` and do not require separate installation.)*

---

## 6. Steps to Execute the Project

1.  **Clone the Repository:**
    ```bash
    git clone [URL_of_your_GitHub_repository]
    cd [repository_folder_name] # e.g., cd CollageGpsApp
    ```
2.  **Prerequisites Check:** Ensure JDK and JavaFX SDK are installed and you know the path to the JavaFX SDK `lib` folder.
3.  **Configure VS Code (If using):**
    *   Open the project folder in VS Code.
    *   Edit `.vscode/settings.json`: Update the `java.project.referencedLibraries` path to point to your **actual** JavaFX SDK `lib` folder.
    *   Edit `.vscode/launch.json`: Update the `--module-path` in `vmArgs` to point to your **actual** JavaFX SDK `lib` folder.
4.  **Compile the Code:** Open a terminal or command prompt **in the project's root directory** (`CollageGpsApp`) and run:
    ```bash
    javac --module-path "E:\Downloads\openjfx-24_windows-x64_bin-sdk.zip\javafx-sdk-24\lib" --add-modules javafx.controls,javafx.web src/Location.java src/GPSApp.java -d bin
    ```
    *   Fix any compilation errors reported. If successful, this creates the `bin` directory with `.class` files.
5.  **Copy Resources:** The `map.html` file needs to be available at runtime. Copy it from `src` to `bin`:
    ```bash
    # On Windows PowerShell:
    copy .\src\map.html .\bin\

    # On Linux/macOS/Git Bash:
    cp ./src/map.html ./bin/
    ```
6.  **Run the Application:**
    *   **From Command Line:** (Make sure you are in the project root directory)
        ```bash
        
        java --module-path "E:\Downloads\openjfx-24_windows-x64_bin-sdk.zip\javafx-sdk-24\lib" --add-modules javafx.controls,javafx.web --add-exports javafx.web/netscape.javascript=ALL-UNNAMED -cp bin GPSApp
        ```
    *   **From VS Code:** Open the "Run and Debug" view (Ctrl+Shift+D), select your launch configuration (e.g., "Launch GPSApp (Leaflet/OSM)"), and click the green play button (or press F5).

---

## 7. SDLC Model Adopted

An **Iterative Development Model** was primarily adopted for this project.

*   **Rationale:** Given the learning curve with JavaFX, WebView, and mapping libraries, an iterative approach allowed for building the application in manageable stages, incorporating feedback, and refining features progressively. Requirements evolved (e.g., switching from Google Maps to Leaflet/OSM).
*   **Phases (Loosely Followed):**
    1.  **Initial Planning:** Define core goal (campus navigation).
    2.  **Iteration 1 (Basic UI):** Design and implement the basic JavaFX window with dropdowns and button (no map). Test UI responsiveness.
    3.  **Iteration 2 (Map Integration Attempt 1):** Integrate WebView and attempt Google Maps loading. Encounter challenges (API key, billing).
    4.  **Iteration 3 (Map Integration Attempt 2):** Pivot to Leaflet/OSM/OSRM. Implement `map.html` and Java-to-JS communication. Test map loading.
    5.  **Iteration 4 (Routing):** Implement routing calls, debug JavaScript errors, handle resource loading. Test route display.
    6.  **Evaluation & Refinement:** Test overall functionality, identify bugs (like tile loading), improve error handling, prepare documentation.

---

## 8. Requirements Gathering & Validation

*   **Initial Requirement:** Create a desktop application for UPES campus navigation.
*   **Gathering Approach:**
    *   **Brainstorming:** Initial ideas on core features (map view, location selection, route display).
    *   **Use Case Analysis:** Defining primary user actions (select start, select end, view route).
    *   **Prototyping:** The initial non-map UI served as a basic prototype. The subsequent map integration steps were incremental prototypes.
    *   **Assumption-Based:** Assumed standard map interactions (pan, zoom) and the need for walking directions.
    *   **Technical Investigation:** Researching mapping libraries (Google Maps vs. Leaflet/OSM) influenced technical requirements.
*   **Validation Approach:**
    *   **Testing:** Comparing application behavior against expected use cases (functional testing).
    *   **Team Review:** Discussing functionality and identifying gaps or issues within the development team.
    *   **Debugging:** Resolving technical errors inherently validated that certain requirements (like Java-to-JS communication) were met.
    *   **Visual Inspection:** Checking if the displayed map and routes appeared logical.

---

## 9. Testing Method

A combination of testing methods was employed, primarily focused on manual testing due to the UI-intensive nature and integration complexity:

1.  **Unit Testing (Limited):** Basic checks could be applied to the `Location.java` class or potentially the Dijkstra algorithm implementation if isolated. (Formal unit tests might not have been extensively written).
2.  **Integration Testing:** This was crucial and done implicitly throughout development:
    *   Testing the JavaFX UI interaction with the backend Java logic.
    *   Testing the Java code's ability to correctly load `map.html` into the `WebView`.
    *   Testing the Java-to-JavaScript communication (`executeScript` calls and function name matching).
    *   Testing the JavaScript's interaction with Leaflet and the OSRM routing service.
3.  **System / Functional Testing:** Testing the end-to-end workflow:
    *   Launching the application.
    *   Selecting valid start/end locations.
    *   Clicking "Find Route".
    *   Observing if the map tiles load, the route line appears correctly, and the text area updates.
    *   Testing edge cases (selecting same start/end location, not selecting locations).
4.  **User Acceptance Testing (UAT) / Exploratory Testing:** Performed by team members acting as end-users to check usability, visual correctness of routes, and identify any unexpected behavior or bugs.

---

## 10. Challenges Faced

*   **Initial JavaFX Setup:** Correctly configuring the JDK and JavaFX SDK, especially the `--module-path` and `--add-modules` VM arguments, was an initial hurdle.
*   **Google Maps Integration Issues:** Encountered difficulties with Google Maps Platform setup, specifically around API key generation, billing requirements, and API enablement, leading to the decision to switch technologies.
*   **WebView & Resource Loading:** Ensuring `map.html` was correctly located on the runtime classpath (`-cp bin`) and loaded properly by the `WebView` required careful configuration.
*   **Java <-> JavaScript Communication:** Debugging `executeScript` calls and ensuring function names matched between Java and JavaScript (`drawRoute` vs `drawRouteFromJava`) was essential.
*   **Map Tile Loading in WebView:** Diagnosing why map tiles failed to load within the WebView (when working in a browser) required investigating potential network, proxy, or `WebView`-specific issues.
*   **Debugging:** Standard Java debugging combined with browser developer tools (when testing `map.html` directly) was necessary to pinpoint issues across the Java/Web boundary.
*   **Dependency Management:** Managing JavaFX as external modules requires careful command-line arguments or IDE configuration, unlike build tools like Maven/Gradle.

*Addressing Them:* Challenges were addressed through persistent debugging, research (Stack Overflow, documentation), simplifying test cases, testing components individually (like `map.html` in a browser), refining command-line arguments, and ultimately pivoting technology (Google Maps to Leaflet/OSM) when one approach proved too problematic for the project context.

---

## 11. Deployment

Currently, the application is primarily intended to be run from source code via an IDE or command line.

*   **Manual Execution:** Follow the steps outlined in section [6. Steps to Execute the Project](#6-steps-to-execute-the-project). This requires the end-user to have the correct JDK and JavaFX SDK installed and configured.
*   **Potential Future Deployment (Not Implemented):** For easier distribution, native installers could be created using tools like:
    *   **`jlink`:** Creates a custom Java runtime image containing the application, its dependencies, and the necessary JDK modules.
    *   **`jpackage`:** Builds platform-specific native installers (e.g., EXE, MSI, DMG, DEB, RPM) that bundle the application and a runtime image (often created using `jlink`). 
---

## 12. Future Scope

*   **Implement Intermediate Waypoints:** Pass the full path sequence from Dijkstra to OSRM via JavaScript for more accurate campus path routing.
*   **Location Search:** Add a search bar to find locations instead of only using dropdowns.
*   **Enhanced UI/UX:**
    *   Improve visual design.
    *   Display detailed turn-by-turn directions from OSRM within the application (requires parsing the routing response).
    *   Consider adding custom markers or icons for different location types.
*   **More Points of Interest:** Expand the `locations` data to include more buildings, labs, facilities, etc., with accurate coordinates.
*   **Offline Capability:** Explore using offline tile servers or vector tiles and potentially hosting a local OSRM instance (significant undertaking).
*   **Robust Error Handling:** Add more specific error handling for network issues, OSRM routing failures, etc.
*   **Alternative Routers/Tiles:** Investigate other routing engines or OSM tile providers if the demo server limitations become an issue.

---

## 13. Team Members & Roles

This project was developed by:

*   Oshan Paul
*   Aditya Rana
*   Shivangi Thapliyal


---
