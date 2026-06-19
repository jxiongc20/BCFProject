# ⚾ Brewers Community Foundation Grant Awards Web Application

## 📖 Overview

The Brewers Community Foundation (BCF) Grant Awards Web Application is a full-stack web application developed through the i.c.stars Milwaukee Cycle 20 program in partnership with Brewers Community Foundation.

The application automates the process of displaying approved grant award information from Monday.com, making it accessible through both a public-facing website and an event kiosk display. By integrating directly with Monday.com, the solution eliminates manual updates and ensures award information remains current and accurate.

---

## 🎯 Project Objectives

- Automate grant award data retrieval and display.
- Reduce manual data entry and maintenance.
- Improve visibility of Brewers Community Foundation grant recipients.
- Create an engaging public-facing experience.
- Support both website and kiosk display environments.

---

## ✨ Features

### Grant Award Display
- Displays approved grant recipients and award information.
- Responsive design for desktop and mobile users.
- Dynamic content updates from Monday.com.

### Kiosk Experience
- Dedicated kiosk view for events and presentations.
- Auto-rotating carousel functionality.
- Large-screen optimized layout.

### Data Integration
- Direct integration with Monday.com using GraphQL.
- Automated retrieval of approved award records.
- Centralized source of truth for displayed data.

### API Endpoints
- Separate endpoints for public and kiosk views.
- JSON-based responses for frontend consumption.
- Error handling and fallback mechanisms.

---

## 🛠️ Tech Stack

### Frontend
- HTML5
- CSS3
- JavaScript (ES6+)

### Backend
- Node.js
- Express.js
- GraphQL

### Data Source
- Monday.com API

### Tools & Methodologies
- GitHub
- Jira
- Agile / Scrum

---

## 🏗️ System Architecture

```text
Monday.com
    │
    ▼
GraphQL API
    │
    ▼
Node.js / Express Backend
    │
    ├── Public Website
    │
    └── Kiosk Display
```

---

## 📂 Project Structure

```text
BCFProject/
│
├── public/
│   ├── Images/
│   ├── grant-form.html
│   ├── kiosk.html
│   ├── sponsors.html
│   ├── story.html
│   └── style.css
│
├── server.js
├── package.json
├── .env                # Environment variables (not committed)
├── .gitignore
└── README.md
```

> Folder names may vary based on implementation.

---

## 🚀 API Endpoints

### Page Routes

| Route | Description |
|---|---|
| `GET /` | Homepage / sponsors landing page |
| `GET /story` | Public story page |
| `GET /kiosk` | Kiosk display view |
| `GET /grant-form` | Grant application form |

### Data API Routes

| Route | Description |
|---|---|
| `GET /api/asset-proxy` | Proxies media/image assets (e.g. from monday.com) to avoid CORS/auth issues |
| `GET /api/storypage-stories` | Returns approved grant award story data for the public story page |
| `GET /api/kiosk-stories` | Returns approved grant award story data formatted for the kiosk display |

---

## ⚙️ Getting Started

These instructions will get a local copy of the project up and running on your own machine.

### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or higher recommended)
- npm (comes bundled with Node.js)
- A [monday.com](https://monday.com) account with API access and an existing board set up with the required columns (see below)

### 1. Clone the repository

```bash
git clone https://github.com/jxiongc20/BCFProject.git
cd BCFProject
```

### 2. Install dependencies

```bash
npm install
```

### 3. Set up environment variables

Create a `.env` file in the root of the project (same folder as `server.js`). Use the template below and fill in your own values:

```
MONDAY_TOKEN=your_monday_api_token
URL=your_monday_api_url
MONDAY_BOARD_ID=your_board_id
MONDAY_NAME_COLUMN_ID=your_name_column_id
MONDAY_CATEGORY_COLUMN_ID=your_category_column_id
MONDAY_STATUS_COLUMN_ID=your_status_column_id
MONDAY_REQUEST_AMOUNT_COLUMN_ID=your_request_amount_column_id
MONDAY_IMPACT_MEDIA_COLUMN_ID=your_impact_media_column_id
MONDAY_IMPACT_DESCRIPTION_COLUMN_ID=your_impact_description_column_id
MONDAY_DATE_COLUMN_ID=your_date_column_id
MONDAY_NEW_APPLICATION_GROUP_ID=your_new_application_group_id
MONDAY_AWARDED_GROUP_ID=your_awarded_group_id
MONDAY_AWARDED_KIOSK_GROUP_ID=your_awarded_kiosk_group_id
```

> ⚠️ **Never commit your `.env` file to GitHub.** It contains sensitive credentials and is already excluded via `.gitignore`.

#### Where to find these values

- **MONDAY_TOKEN**: Generate this from your monday.com account under **Admin > API** (or your profile's developer settings).
- **URL**: The monday.com GraphQL API endpoint, typically `https://api.monday.com/v2`.
- **MONDAY_BOARD_ID**: Found in the URL of your monday.com board, or via the API.
- **Column IDs / Group IDs**: Found by inspecting your board's columns/groups via the monday.com API or board settings.

### 4. Run the server

```bash
npm start
```

This runs `node server.js`. By default, the app will be available at:

```
http://localhost:3000
```

- Homepage: `http://localhost:3000/`
- Story page: `http://localhost:3000/story`
- Grant application form: `http://localhost:3000/grant-form`
- Kiosk display view: `http://localhost:3000/kiosk`

If port 3000 is already in use, either stop the other process or update the port in `server.js`.

---

## 🔍 Troubleshooting

| Issue | Solution |
|---|---|
| `EADDRINUSE` error on start | Port 3000 is already in use. Close other running instances of the app or change the port. |
| `Cannot find module` errors | Run `npm install` again to make sure all dependencies are installed. |
| monday.com data not loading | Double check your `.env` values, especially `MONDAY_TOKEN` and `MONDAY_BOARD_ID`, and confirm your API token has access to the relevant board. |
| Images not displaying | Verify fallback image handling is configured and media column data is correctly formatted in monday.com. |
| Kiosk carousel not rotating correctly | Check the rotation/timing logic in the kiosk frontend JS. |

---

## 👩‍💻 My Contributions

### Project Management
- Facilitated team standups and sprint planning.
- Coordinated project deliverables and deadlines.
- Managed stakeholder communication.
- Supported Agile workflow execution.

### Full-Stack Development
- Assisted with frontend development and UI implementation.
- Supported backend API integration.
- Worked with GraphQL queries and data retrieval.
- Participated in testing and debugging activities.

### UI/UX Design
- Improved information layout and user experience.
- Contributed to responsive design implementation.
- Enhanced kiosk display usability.

---

## 🔍 Challenges & Solutions

| Challenge | Solution |
|------------|------------|
| Keeping grant information current | Integrated Monday.com as the source of truth |
| Image display inconsistencies | Implemented fallback image handling |
| Carousel timing issues | Refined automatic rotation logic |
| Data formatting errors | Added validation and error handling |
| Supporting multiple display experiences | Created dedicated endpoints for website and kiosk views |

---

## 🏆 Project Highlights

- Successfully integrated Monday.com data into a public-facing application.
- Built a scalable architecture using Node.js, Express, and GraphQL.
- Delivered both web and kiosk experiences from a shared backend.
- Reduced manual maintenance of grant award information.
- Presented the final solution to Brewers Community Foundation stakeholders.

---

## 📈 Future Enhancements

- Search and filtering functionality
- Award recipient analytics dashboard
- Enhanced accessibility features
- Administrative management portal
- Additional mobile experience improvements

---

## 🙏 Acknowledgments

Special thanks to:

- Brewers Community Foundation
- i.c.stars Milwaukee
- Project mentors and stakeholders
- Development team members

---

## 📋 Project Information

| Category | Details |
|-----------|----------|
| Project | Brewers Community Foundation Grant Awards Web Application |
| Organization | Brewers Community Foundation |
| Program | i.c.stars Milwaukee – Cycle 20 |
| Year | 2026 |
| Type | Community Impact Web Application |

---

> Built to increase transparency, accessibility, and visibility of community grant awards while reducing manual administrative effort.
