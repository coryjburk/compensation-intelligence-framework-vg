# David Eccles School of Business Full-Time MBA Program - Interactive Strategic Offer Compensation Calculator

---

## Live Link

**[Compensation Intelligence Framework (vG)]**(https://coryjburk.github.io/compensation-intelligence-framework-vg/ )

---


## Overview
The Interactive Strategic Offer Compensation Calculator is a self-contained, single-page web application (HTML/CSS/JavaScript) designed to empower MBA and graduate students during salary negotiations. [cite_start]When navigating the hiring system, having a real-time scenario planner gives candidates immense leverage to counter-offer and visualize the true long-term value of an employer's compensation package[cite: 621]. 

[cite_start]This tool operates completely client-side, requiring no backend database, meaning it is fast, secure, and easily hostable on virtually any platform[cite: 623].

## Core Features & Modes
To provide accurate modeling across different employer types, the application is divided into two distinct analytical modes:

### 1. Startup / Early-Stage Mode
Designed for high-growth, early-stage ventures. This mode evaluates:
* [cite_start]Base cash and performance bonuses tied to corporate KPIs (growth, expenses, margins)[cite: 625].
* [cite_start]"Write-off" or tax-advantaged perks (e.g., QSEHRA, phone stipends)[cite: 625].
* [cite_start]Phantom Equity or Stock Appreciation Rights (SARs), incorporating customized backend vesting schedules and potential clawbacks[cite: 625].

### 2. Traditional Corporate Mode
Designed for mid-market to Fortune 500 total compensation packages. This mode evaluates:
* [cite_start]Base salary escalators and fixed signing bonuses[cite: 626].
* [cite_start]Target bonus percentages[cite: 626].
* [cite_start]Initial Restricted Stock Unit (RSU) grants[cite: 626].
* [cite_start]Annual equity refresh cycles modeled over 3-year or 4-year horizons[cite: 626].

## Deployment & Hosting Instructions
Because this is a static HTML application, it is highly versatile. Choose the deployment method that best fits your student cohort's workflow.

### Option A: Local File Distribution (Fastest)
You can distribute the tool directly to students for offline use.
1. [cite_start]Save the codebase as `Offer_Calculator.html`[cite: 630].
2. [cite_start]Email the file directly to students or upload it to your university's files dashboard[cite: 630].
3. [cite_start]When students download and click the file, it will open an interactive sandbox locally right inside their default web browser[cite: 631].

### Option B: GitHub Pages (Recommended for Web Hosting)
Host the calculator live on the web for free using GitHub Pages.
1. Upload the `Offer_Calculator.html` file to the root of your GitHub repository.
2. Rename the file to `index.html`.
3. Navigate to your repository **Settings** > **Pages**.
4. Under "Source", select the `main` branch and save. 
5. GitHub will provide a live URL you can share with students.

### Option C: Embedding Directly in an LMS (Canvas / Blackboard)
If your university utilizes Canvas or a similar modern Learning Management System (LMS), you can embed the tool directly into a course module.
1. [cite_start]Create a new page or content block in your LMS[cite: 632].
2. [cite_start]Switch the text editor viewpoint from "Rich Text" to "HTML / Code View" (`</>`)[cite: 633].
3. [cite_start]Paste the entire HTML code block directly into the field and click **Save**[cite: 634].

### Option D: Google Sheets Alternative
[cite_start]If students prefer a traditional spreadsheet interface over a web sandbox layout, the data parameters can be ported into Google Sheets[cite: 635].
1. [cite_start]Copy the layout parameters into a new Google Sheet[cite: 635].
2. [cite_start]Navigate to `Extensions -> Apps Script` to paste calculation logic for custom pop-ups[cite: 636].
[cite_start]*Note: Running the standalone HTML web app (Options A, B, or C) generally offers a faster, more seamless experience for students comparing offers side-by-side[cite: 637].*

## Tech Stack
* **HTML5**: Application structure and layout.
* **CSS3**: Responsive styling (Mobile & Desktop friendly).
* **Vanilla JavaScript (ES6)**: Core calculation logic and dynamic DOM updates.

## Usage
Simply enter the parameters of your job offer into the designated input fields. The dynamic visualizations and summary metrics will automatically update in real-time, allowing you to instantly see the financial impact of negotiating a higher signing bonus, tweaking an equity refresh schedule, or adjusting base salary expectations.
