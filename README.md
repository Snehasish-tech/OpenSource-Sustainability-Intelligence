# OpenSource Sustainability Intelligence (OSSI)

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)
![Status](https://img.shields.io/badge/status-active-success.svg)
![Build](https://img.shields.io/badge/build-passing-brightgreen.svg)

**A human‑centric platform to assess open‑source project health, maintainer workload, sustainability risk, and trust—so communities and companies can act before projects burn out.**

[Features](#-mvp-features) • [Installation](#-installation) • [Usage](#-usage) • [Tech Stack](#-tech-stack-planned) • [Roadmap](#️-roadmap) • [API Documentation](#-api-documentation)

</div>

---

## 📖 Table of Contents
- [Vision & Mission](#-vision)
- [Core Objectives](#-core-objectives)
- [MVP Features](#-mvp-features)
- [Scoring Overview](#-scoring-overview-initial)
- [Installation](#-installation)
- [Usage](#-usage)
- [Tech Stack](#-tech-stack-planned)
- [Architecture](#-architecture)
- [API Documentation](#-api-documentation)
- [Roadmap](#️-roadmap)
- [FAQ](#-faq)
- [License](#-license)

---

## 🌍 Vision
Ensure the long‑term sustainability of open‑source projects by combining repository health metrics with human‑centric signals like maintainer workload and burnout risk. OSSI empowers communities and organizations to make data-driven decisions about project dependencies and contributions.

## 🎯 Mission
Build a transparent, explainable platform that provides actionable insights and early warnings for projects at risk of abandonment or low trust. We bridge the gap between technical metrics and human factors to create a holistic view of project sustainability.

---

## ✅ Core Objectives
- **📊 Analyze Repository Health Metrics** - Monitor commit patterns, issue management, and community engagement
- **👥 Evaluate Maintainer Workload** - Track maintainer concentration and identify potential burnout risks
- **⚠️ Calculate Bus Factor & Risk** - Identify single points of failure and predict abandonment probability
- **🎯 Trust & Sustainability Scoring** - Provide comprehensive, weighted assessment of project viability
- **💡 Generate Actionable Recommendations** - Offer data-driven suggestions for improving project health
- **📈 Public Dashboard** - Deliver transparent, explainable metrics through intuitive visualizations

---

## 🔍 MVP Features
### 1) Repository Health
- Last commit date
- Commit frequency
- Open vs closed issues
- README quality
- Contributors count
- Star growth
- License presence

### 2) Maintainer Workload
- Active maintainers count
- Workload concentration
- PR/issue response delay
- Commit activity trends

### 3) Bus Factor & Risk
- Single‑point‑of‑failure score
- Probability of abandonment
- Trend‑based risk prediction

### 4) Trust & Sustainability Score
- Weighted scoring system
- Visual dashboards (charts/gauges)

### 5) Recommendations
- Add co‑maintainers
- Label beginner‑friendly issues
- Contributor guidance

---

## 🧠 Scoring Overview (Initial)
Weighted Score System (0–100):
- Project Health: **40%**
- Maintainer Workload: **30%**
- Bus Factor & Risk: **20%**
- Trust & License: **10%**

Output Example:
- **Sustainability Score:** 82/100
- **Status:** Healthy
- **Maintainer Risk:** Medium
- **Recommendation:** Add co‑maintainers, label beginner‑friendly issues

---

## 🧱 Tech Stack (Planned)
### Backend
- **Runtime:** Node.js + Express *(or Python + Flask)*
- **API Integration:** GitHub REST API / GraphQL
- **Authentication:** GitHub OAuth 2.0
- **Rate Limiting:** Redis

### Database
- **Primary:** MongoDB (for flexibility) / Firebase (for real-time updates)
- **Caching:** Redis for performance optimization

### Frontend
- **Framework:** React 18+ with TypeScript
- **State Management:** Redux / Context API
- **Visualization:** Chart.js / Recharts / D3.js
- **Styling:** Tailwind CSS / Material-UI
- **Build Tool:** Vite / Webpack

### DevOps & Deployment
- **CI/CD:** GitHub Actions
- **Hosting:** Vercel / Netlify (Frontend), AWS / GCP (Backend)
- **Monitoring:** Prometheus + Grafana
- **Logging:** Winston / Bunyan

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Frontend (React)                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Dashboard   │  │   Analytics  │  │    Reports   │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└────────────────────────────┬────────────────────────────────┘
                             │ REST API
┌────────────────────────────┴────────────────────────────────┐
│                    Backend (Node.js/Express)                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Health Engine│  │  Risk Engine │  │ Score Engine │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└────────────────┬────────────────────────────┬───────────────┘
                 │                            │
      ┌──────────┴──────────┐      ┌─────────┴─────────┐
      │   GitHub API        │      │   Database        │
      │   (REST/GraphQL)    │      │   (MongoDB)       │
      └─────────────────────┘      └───────────────────┘
```

### Key Components
- **Health Engine:** Analyzes repository metrics and commit patterns
- **Risk Engine:** Calculates bus factor and abandonment probability
- **Score Engine:** Computes weighted sustainability scores
- **Recommendation Engine:** Generates actionable insights
- **Cache Layer:** Redis for optimized API response times

---

## 📦 Installation

### Prerequisites
- Node.js (v18.x or higher) / Python (3.9+)
- MongoDB (v5.x or higher) or Firebase account
- GitHub Personal Access Token
- Git

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/Snehasish-tech/OpenSource-Sustainability-Intelligence.git
   cd OpenSource-Sustainability-Intelligence
   ```

2. **Install dependencies**
   ```bash
   # For Node.js backend
   npm install
   
   # For Python backend
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` with your credentials:
   ```env
   GITHUB_TOKEN=your_github_personal_access_token
   MONGODB_URI=mongodb://localhost:27017/ossi
   PORT=3000
   NODE_ENV=development
   JWT_SECRET=your_jwt_secret
   ```

4. **Initialize the database**
   ```bash
   npm run db:init
   ```

5. **Start the development server**
   ```bash
   # Backend
   npm run dev
   
   # Frontend (in separate terminal)
   cd frontend
   npm run dev
   ```

6. **Access the application**
   - Frontend: `http://localhost:5173`
   - Backend API: `http://localhost:3000`
   - API Documentation: `http://localhost:3000/api-docs`

---

## 🚀 Usage

### Quick Start
```bash
# Analyze a repository
curl -X POST http://localhost:3000/api/analyze \
  -H "Content-Type: application/json" \
  -d '{"repo": "owner/repository"}'

# Get sustainability score
curl http://localhost:3000/api/score/owner/repository
```

### Using the Dashboard
1. Navigate to the web interface
2. Enter a GitHub repository URL (e.g., `https://github.com/facebook/react`)
3. Click "Analyze" to generate the sustainability report
4. View detailed metrics, charts, and recommendations
5. Export reports as PDF or JSON

### Command Line Interface (Planned)
```bash
# Install CLI globally
npm install -g ossi-cli

# Analyze a repository
ossi analyze owner/repository

# Get quick score
ossi score owner/repository

# Generate report
ossi report owner/repository --format=pdf
```

---

## 📊 API Documentation

### Base URL
```
https://api.ossi.dev/v1
```

### Authentication
All requests require a GitHub token:
```bash
Authorization: Bearer YOUR_GITHUB_TOKEN
```

### Endpoints

#### 1. Analyze Repository
```http
POST /api/analyze
Content-Type: application/json

{
  "repo": "owner/repository",
  "options": {
    "includeHistory": true,
    "depth": 12
  }
}
```

**Response:**
```json
{
  "sustainabilityScore": 82,
  "status": "Healthy",
  "metrics": {
    "health": 85,
    "maintainerLoad": 70,
    "busFactor": 4,
    "trustScore": 90
  },
  "recommendations": [
    "Add co-maintainers",
    "Label beginner-friendly issues"
  ]
}
```

#### 2. Get Project Score
```http
GET /api/score/{owner}/{repo}
```

#### 3. Get Historical Trends
```http
GET /api/trends/{owner}/{repo}?period=6m
```

#### 4. Get Maintainer Analysis
```http
GET /api/maintainers/{owner}/{repo}
```

#### 5. Get Risk Assessment
```http
GET /api/risk/{owner}/{repo}
```

### Rate Limits
- **Authenticated:** 5,000 requests/hour
- **Unauthenticated:** 60 requests/hour

---

## 🗺️ Roadmap

### ✅ Phase 1: Planning & Repository Setup (Completed)
- [x] Define project scope and objectives
- [x] Create repository structure
- [x] Document initial requirements

### 🔄 Phase 2: Backend & GitHub API Integration (In Progress)
- [ ] Set up Express/Flask server
- [ ] Implement GitHub API client
- [ ] Create data models and schemas
- [ ] Build authentication system
- [ ] Implement rate limiting and caching

### 📅 Phase 3: Maintainer Workload & Risk Engine (Q2 2026)
- [ ] Develop workload calculation algorithms
- [ ] Implement bus factor analysis
- [ ] Create risk prediction models
- [ ] Build trend analysis engine
- [ ] Add ML-based abandonment prediction

### 📅 Phase 4: Frontend & Dashboard (Q3 2026)
- [ ] Design UI/UX wireframes
- [ ] Build React components
- [ ] Integrate Chart.js visualizations
- [ ] Implement responsive design
- [ ] Create interactive dashboards

### 📅 Phase 5: Recommendations & Reports (Q4 2026)
- [ ] Develop recommendation engine
- [ ] Generate automated reports
- [ ] Add PDF export functionality
- [ ] Implement email alerts
- [ ] Create comparison features

### 📅 Phase 6: Testing & Deployment (Q1 2027)
- [ ] Unit testing (Jest/Pytest)
- [ ] Integration testing
- [ ] Load testing and optimization
- [ ] Security auditing
- [ ] Production deployment
- [ ] Documentation finalization

### 🔮 Future Enhancements
- AI-powered insights using GPT-5
- Multi-platform support (GitLab, Bitbucket)
- Browser extension
- Slack/Discord integrations
- Custom scoring weights
- Enterprise features
- White-label solutions

---

## ❓ FAQ

### What is a "Bus Factor"?
The bus factor is the number of team members who, if they were suddenly unavailable (hit by a bus), would severely impact the project. A low bus factor indicates high risk.

### How is the sustainability score calculated?
The score is a weighted average:
- Project Health: 40%
- Maintainer Workload: 30%
- Bus Factor & Risk: 20%
- Trust & License: 10%

### Is this tool free to use?
Yes, OSSI is open-source and free. We may offer premium features for enterprises in the future.

### How often is data updated?
Dashboard data is refreshed every 24 hours. Premium users can request real-time updates.

### Can I analyze private repositories?
Yes, with proper GitHub token permissions. Your data remains private.

### What makes OSSI different from other tools?
OSSI uniquely focuses on human-centric signals like maintainer burnout and workload concentration, not just technical metrics.

### How can I integrate OSSI into my CI/CD pipeline?
We provide a CLI tool and REST API that can be integrated into any CI/CD workflow. Documentation available in `/docs/cicd-integration.md`.

---

## 📄 License
This project is licensed under **Apache License 2.0** - see the [LICENSE](LICENSE) file for details.

---

## 🔗 Links
- **Documentation:** [docs.ossi.dev](https://docs.ossi.dev)
- **API Reference:** [api.ossi.dev/docs](https://api.ossi.dev/docs)
- **Blog:** [blog.ossi.dev](https://blog.ossi.dev)
- **Community:** [community.ossi.dev](https://community.ossi.dev)

---

<div align="center">

**Made with ❤️ for the Open Source Community**

[⬆ Back to Top](#opensource-sustainability-intelligence-ossi)

</div>