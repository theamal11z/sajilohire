# SajiloHire – AI-Powered Recruitment Assistant

SajiloHire is an intelligent hiring platform that revolutionizes recruitment through AI-powered candidate onboarding, smart scoring algorithms, and comprehensive candidate assessment. Built for the Aqore Hackathon, it combines cutting-edge AI technology with modern web development to streamline the hiring process.

## 📁 Project Structure

```
aqore/
├── sajilo-ai-hire/          # Frontend (React + Vite + TypeScript)
├── sajilohire-backend/      # Backend (FastAPI + Python)
├── swagger.json             # Aqore API Documentation
├── api.txt                  # API Reference
└── README.md               # This file
```

## 🚀 Key Features

### For Candidates
- **Smart Job Discovery**: Browse curated job opportunities from top companies
- **AI-Powered Onboarding**: Interactive chat-based screening process that adapts to responses
- **Profile Enrichment**: Automatic LinkedIn and GitHub data integration via PhantomBuster
- **Real-time Assessment**: Intelligent evaluation of technical skills and cultural fit

### For Recruiters
- **Intelligent Dashboard**: Comprehensive candidate overview with AI-generated insights
- **Smart Scoring System**: Multi-dimensional candidate evaluation (fit score, turnover risk, culture alignment)
- **Advanced Analytics**: Deep candidate analysis including personality assessment and technical competency
- **Social Intelligence**: Professional background verification and consistency checking

### AI Components
- **Adaptive Interview Engine**: Dynamic questioning based on OpenAI GPT-4o-mini
- **Candidate Scoring**: Multi-factor assessment including consistency, depth, and motivation alignment
- **Culture-Fit Analysis**: Behavioral pattern matching and values alignment
- **Risk Assessment**: Turnover prediction and credibility flagging
- **Social Verification**: Cross-platform data validation and trust scoring

## 🏗️ Architecture Overview

### Frontend (React Application)
**Location**: `./sajilo-ai-hire/`

- **Framework**: React 18 with TypeScript and Vite
- **Styling**: Tailwind CSS with shadcn/ui components
- **State Management**: TanStack Query for server state management
- **Routing**: React Router for client-side navigation
- **Form Handling**: React Hook Form with Zod validation
- **UI Components**: Modern component library with dark/light theme support

**Key Pages**:
- `/` - Landing page with platform overview
- `/jobs` - Job listings with search and filtering
- `/apply` - Multi-step application form
- `/onboarding/{candidateId}` - AI-powered chat onboarding
- `/dashboard` - Recruiter dashboard with candidate analytics
- `/candidate/{candidateId}` - Detailed candidate profile

### Backend (FastAPI Application)
**Location**: `./sajilohire-backend/`

- **Framework**: FastAPI with async/await support
- **Database**: SQLAlchemy ORM with PostgreSQL/SQLite
- **AI Integration**: OpenAI GPT-4o-mini for conversational AI
- **External APIs**: Aqore Hackathon API integration
- **Data Enrichment**: PhantomBuster for LinkedIn/GitHub scraping
- **Caching**: Intelligent data synchronization and caching layer

**Key Endpoints**:
- `/sajilo/jobs` - Job listings from Aqore API
- `/sajilo/person` - Candidate creation and management
- `/sajilo/chat/{person_id}` - AI conversation handling
- `/sajilo/dashboard/{job_id}` - Recruiter analytics
- `/sajilo/candidate/{person_id}/full` - Complete candidate profile
- `/sajilo/phantombuster-analysis/{person_id}` - Social media insights

## 🛠️ Tech Stack

| Component | Frontend | Backend |
|-----------|----------|---------|
| **Language** | TypeScript | Python 3.11+ |
| **Framework** | React 18 + Vite | FastAPI |
| **Styling** | Tailwind CSS + shadcn/ui | - |
| **Database** | - | SQLAlchemy + PostgreSQL/SQLite |
| **State Management** | TanStack Query | - |
| **AI/ML** | - | OpenAI GPT-4o-mini, TextBlob, NumPy |
| **External APIs** | Axios HTTP Client | Requests + Aqore API + PhantomBuster |
| **Testing** | ESLint + TypeScript | Pytest |
| **Server** | Vite Dev Server | Uvicorn |

## 🔗 API Integration

### Aqore Hackathon API
- **Base URL**: `https://hackathonapi.aqore.com`
- **Documentation**: `https://hackathonapi.aqore.com/swagger/v1/swagger.json`
- **Key Endpoints**:
  - `/Client/GetAllClients` - Retrieve client information
  - `/Job/GetJobs` - Fetch available job listings
  - `/Person/GetPersons` - Access candidate profiles

### Internal API Communication
- **Frontend ↔ Backend**: REST API with JSON responses
- **Base URL**: `http://localhost:8000` (development)
- **Authentication**: JWT-based (planned)
- **Real-time Features**: Polling for chat updates and status changes

## 📦 Installation & Setup

### Prerequisites
- **Node.js** (v18+) and npm/yarn
- **Python** (3.11+) and pip
- **PostgreSQL** (optional, SQLite used by default for development)
- **OpenAI API Key** (for AI features)

### Quick Start

1. **Clone the repository**:
```bash
git clone <repository-url>
cd aqore
```

2. **Set up Backend**:
```bash
cd sajilohire-backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Create environment file
cp .env.example .env
# Edit .env with your API keys and settings
```

3. **Set up Frontend**:
```bash
cd ../sajilo-ai-hire

# Install dependencies
npm install

# Create environment file
cp .env.example .env
# Edit .env with backend URL
```

### Environment Configuration

#### Backend (.env in `sajilohire-backend/`)
```env
DATABASE_URL=sqlite:///./sajilo.db
OPENAI_API_KEY=your_openai_api_key_here
AQORE_API_BASE_URL=https://hackathonapi.aqore.com
PHANTOMBUSTER_API_KEY=your_phantombuster_key  # Optional
SAJILO_OFFLINE_MODE=false
```

#### Frontend (.env in `sajilo-ai-hire/`)
```env
VITE_API_BASE_URL=http://localhost:8000
```

## 🚀 Running the Application

### Development Mode

1. **Start Backend Server**:
```bash
cd sajilohire-backend
source venv/bin/activate
python main.py
```
Backend will be available at: `http://localhost:8000`
API Documentation: `http://localhost:8000/docs`

2. **Start Frontend Server** (in new terminal):
```bash
cd sajilo-ai-hire
npm run dev
```
Frontend will be available at: `http://localhost:5173`

### Production Build

1. **Build Frontend**:
```bash
cd sajilo-ai-hire
npm run build
npm run preview
```

2. **Run Backend in Production**:
```bash
cd sajilohire-backend
uvicorn main:app --host 0.0.0.0 --port 8000
```

## 🔄 How Frontend and Backend Connect

### 1. Job Listings Flow
- Frontend fetches jobs from `/sajilo/jobs`
- Backend calls Aqore API and caches results
- Frontend displays job cards with apply buttons

### 2. Candidate Application Flow
- Multi-step form in React (`/apply`)
- POST to `/sajilo/person` creates candidate
- PUT to `/sajilo/person/{id}/extend` adds profile data
- Redirect to AI onboarding chat

### 3. AI Onboarding Process
- React chat interface at `/onboarding/{candidateId}`
- Real-time messaging via `/sajilo/chat/{person_id}`
- FastAPI + OpenAI generates adaptive questions
- Progress tracking and completion detection

### 4. Recruiter Dashboard
- Dashboard at `/dashboard` shows candidate analytics
- Data from `/sajilo/dashboard/{job_id}`
- Real-time score updates and filtering options

### 5. Profile Enrichment
- PhantomBuster integration enriches social data
- Background processing for LinkedIn/GitHub scraping
- Trust scores and verification flags

## 🎯 Hackathon Context

### Problem Solved
Traditional recruitment processes are:
- **Time-consuming**: Manual resume screening and interviews
- **Subjective**: Inconsistent evaluation criteria
- **Limited**: Missing qualified candidates due to resume-only filtering
- **Inefficient**: High cost-per-hire and lengthy processes

### SajiloHire's Unique Approach
1. **Conversational AI**: Replace static forms with intelligent chat
2. **Multi-dimensional Scoring**: Technical + cultural + stability assessment
3. **Social Intelligence**: Cross-platform verification and insights
4. **Predictive Analytics**: Risk assessment and culture fit prediction
5. **Real-time Insights**: Live candidate analytics for recruiters

### Innovation Highlights
- **Adaptive Interview Engine**: Questions evolve based on candidate responses
- **Social Verification System**: LinkedIn/GitHub data validation
- **Culture-Fit AI**: Behavioral pattern matching
- **Turnover Risk Prediction**: AI-powered retention forecasting

## 🚀 Deployment Options

### Docker Deployment

**Backend Dockerfile** (`sajilohire-backend/Dockerfile`):
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

**Frontend Dockerfile** (`sajilo-ai-hire/Dockerfile`):
```dockerfile
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Cloud Deployment
- **Frontend**: Deploy to Vercel, Netlify, or AWS S3 + CloudFront
- **Backend**: Deploy to Railway, Heroku, or AWS ECS
- **Database**: PostgreSQL on AWS RDS or Google Cloud SQL

## 📋 API Documentation

### Key Frontend-Backend Interactions

| Frontend Route | Backend Endpoint | Purpose |
|---------------|------------------|---------|
| `/jobs` | `GET /sajilo/jobs` | Fetch job listings |
| `/apply` | `POST /sajilo/person` | Create candidate |
| `/onboarding/{id}` | `GET/POST /sajilo/chat/{id}` | AI conversation |
| `/dashboard` | `GET /sajilo/dashboard/{job_id}` | Recruiter analytics |
| `/candidate/{id}` | `GET /sajilo/candidate/{id}/full` | Complete profile |

### Health Monitoring
- Backend Health: `GET /health`
- Database Status: Included in health check
- Upstream API Status: Aqore API connectivity

## 🐛 Troubleshooting

### Common Issues

1. **Backend not starting**:
   - Check Python version (3.11+ required)
   - Verify all dependencies installed
   - Check DATABASE_URL format

2. **Frontend API errors**:
   - Ensure backend is running on port 8000
   - Check VITE_API_BASE_URL in .env
   - Verify CORS configuration

3. **AI features not working**:
   - Validate OPENAI_API_KEY
   - Check OpenAI API quota/limits
   - Review backend logs for API errors

4. **Database issues**:
   - SQLite: Check file permissions
   - PostgreSQL: Verify connection string
   - Check table creation in logs

## 🤝 Contributing

### Development Workflow
1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Make changes in appropriate directory (`sajilo-ai-hire/` or `sajilohire-backend/`)
4. Test both frontend and backend
5. Commit: `git commit -m 'Add amazing feature'`
6. Push: `git push origin feature/amazing-feature`
7. Create Pull Request

### Code Standards
- **Frontend**: ESLint + Prettier configuration
- **Backend**: Black code formatting + type hints
- **Testing**: Jest (frontend) + Pytest (backend)
- **Documentation**: JSDoc + Python docstrings

## 📊 Performance Metrics

### Expected Performance
- **Page Load Time**: < 2s (frontend)
- **API Response Time**: < 500ms (backend)
- **AI Response Time**: < 3s (OpenAI dependent)
- **Concurrent Users**: 100+ (with proper scaling)

### Monitoring
- Frontend: Vite dev tools + React DevTools
- Backend: FastAPI automatic docs + logging
- Database: SQLAlchemy query logging
- External APIs: Request/response monitoring

## 🎓 Learning Resources

### For Frontend Development
- [React Documentation](https://react.dev)
- [Vite Guide](https://vitejs.dev/guide/)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [shadcn/ui Components](https://ui.shadcn.com)

### For Backend Development
- [FastAPI Documentation](https://fastapi.tiangolo.com)
- [SQLAlchemy Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)

## 📄 License

This project is developed for the Aqore Hackathon. All rights reserved.

---

## 📞 Support & Contact

For questions, issues, or contributions:
- **GitHub Issues**: Create detailed bug reports or feature requests
- **Documentation**: Check `/docs` endpoints on the backend
- **API Reference**: Visit `http://localhost:8000/docs` when backend is running

---

**🏆 Built for the Aqore Hackathon**

*SajiloHire - Making hiring decisions easier, faster, and smarter through the power of AI.*

**Project Team**: Building the future of recruitment, one conversation at a time.
