# SajiloHire – AI-Powered Recruitment Assistant

SajiloHire is an intelligent hiring platform that revolutionizes recruitment through AI-powered candidate onboarding, smart scoring algorithms, and comprehensive candidate assessment. Built for the Aqore Hackathon, it combines cutting-edge AI technology with modern web development to streamline the hiring process.

## 📂 Repository Structure

This project involves two separate repositories:

- **Frontend Repository**: [sajilohire-frontend](https://github.com/theamal11z/sajilohire-frontend.git)
- **Backend Repository**: [sajilohire-backend](https://github.com/theamal11z/sajilohire-backend.git)

## 🚀 Key Features

- **Smart Job Discovery**: Browse curated job opportunities from top companies
- **AI-Powered Onboarding**: Interactive chat-based screening process using OpenAI GPT-4o-mini
- **Profile Enrichment**: Automatic LinkedIn and GitHub data integration via PhantomBuster
- **Intelligent Dashboard**: Comprehensive candidate overview with AI-generated insights
- **Smart Scoring System**: Multi-dimensional candidate evaluation (fit score, turnover risk, culture alignment)
- **Social Verification**: Cross-platform data validation and trust scoring

## 🏗️ Tech Stack

### Frontend (React + TypeScript)
- React 18 with Vite and TypeScript
- Tailwind CSS with shadcn/ui components
- TanStack Query for state management
- React Router and React Hook Form

### Backend (FastAPI + Python)
- FastAPI with async/await support
- SQLAlchemy ORM with PostgreSQL/SQLite
- OpenAI GPT-4o-mini for conversational AI
- Integration with Aqore Hackathon API

## 📦 Setup Instructions

### Prerequisites
- Node.js (v18+) and npm
- Python (3.11+) and pip
- OpenAI API Key

### Frontend Setup

1. **Clone and setup the frontend repository**:
```bash
git clone https://github.com/theamal11z/sajilohire-frontend.git
cd sajilohire-frontend
npm install
```

2. **Create environment file**:
```bash
cp .env.example .env
# Edit .env with backend URL:
# VITE_API_BASE_URL=http://localhost:8000
```

3. **Start development server**:
```bash
npm run dev
```
Frontend will be available at `http://localhost:5173`

### Backend Setup

1. **Clone and setup the backend repository**:
```bash
git clone https://github.com/theamal11z/sajilohire-backend.git
cd sajilohire-backend
```

2. **Create virtual environment and install dependencies**:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. **Create environment file**:
```bash
cp .env.example .env
# Edit .env with your API keys:
# DATABASE_URL=sqlite:///./sajilo.db
# OPENAI_API_KEY=your_openai_api_key_here
# AQORE_API_BASE_URL=https://hackathonapi.aqore.com
```

4. **Start development server**:
```bash
python main.py
```
Backend will be available at `http://localhost:8000`
API Documentation at `http://localhost:8000/docs`

## 🔗 API Integration

### Aqore Hackathon API
- **Base URL**: `https://hackathonapi.aqore.com`
- **Key Endpoints**: Jobs, Clients, and Person management
- **Documentation**: Available in `swagger.json`

### Frontend-Backend Communication
- REST API with JSON responses
- Key endpoints: `/sajilo/jobs`, `/sajilo/person`, `/sajilo/chat/{person_id}`
- Real-time chat interface for AI onboarding

## 🎯 Hackathon Innovation

### Problem Solved
Traditional recruitment is time-consuming, subjective, and inefficient. SajiloHire addresses this with:

1. **Conversational AI**: Replace static forms with intelligent chat
2. **Multi-dimensional Scoring**: Technical + cultural + stability assessment
3. **Social Intelligence**: Cross-platform verification and insights
4. **Predictive Analytics**: Risk assessment and culture fit prediction

### Key Innovation
- **Adaptive Interview Engine**: Questions evolve based on candidate responses
- **Social Verification System**: LinkedIn/GitHub data validation
- **Turnover Risk Prediction**: AI-powered retention forecasting

## 🚀 Deployment

### Frontend
- Deploy to Vercel, Netlify, or similar platforms
- Build command: `npm run build`

### Backend
- Deploy to Railway, Heroku, or AWS
- Production command: `uvicorn main:app --host 0.0.0.0 --port 8000`

## 🏆 Built for the Aqore Hackathon

*SajiloHire - Making hiring decisions easier, faster, and smarter through the power of AI.*
