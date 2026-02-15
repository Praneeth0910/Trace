# MVP Scope: TRACE Railway Safety System
## Hackathon Prototype Version

**Target Timeline**: 2-3 weeks  
**Goal**: Demonstrate core AI-powered collision detection and alerting capabilities  
**Audience**: AWS AI for Bharat Hackathon judges and stakeholders

---

## MVP Philosophy

The MVP focuses on demonstrating the **core value proposition**: AI-powered collision detection and real-time alerting for railway safety. We'll use simulated data, simplified architecture, and essential features only.

**What's IN**: Core safety features, visual demo, AI detection  
**What's OUT**: Full scalability, production deployment, advanced ML training, comprehensive testing

---

## MVP Features (Must-Have)

### 1. Real-Time Train Monitoring (Simplified)
**Scope**: Display 10-20 simulated trains on a map
- Show train positions updating in real-time (every 2-5 seconds)
- Display train ID, speed, and current route
- Visual indicators for train status (running, stopped, alert)

**Excluded from MVP**:
- ❌ 500+ concurrent trains
- ❌ Connection loss detection
- ❌ Historical playback
- ❌ Detailed train metadata

### 2. Collision Risk Detection (Core Feature)
**Scope**: Rule-based collision detection with basic ML scoring
- Detect when two trains are on converging paths
- Calculate simple collision probability based on distance and speed
- Generate alerts when collision risk exceeds threshold (>70%)
- Show estimated time to collision

**Excluded from MVP**:
- ❌ Complex ML model training
- ❌ Historical pattern analysis
- ❌ Advanced trajectory prediction
- ❌ Multiple collision scenarios simultaneously

### 3. Signal Conflict Detection (Simplified)
**Scope**: Basic signal conflict rules
- Detect when two trains have green signals for same track segment
- Flag conflicting signal states
- Generate critical alerts

**Excluded from MVP**:
- ❌ Complex signal state validation
- ❌ Signal timing optimization
- ❌ Historical signal log analysis

### 4. Alert System (Essential)
**Scope**: Basic alert generation and display
- Create alerts for collision risks and signal conflicts
- Display alerts in a list with severity (CRITICAL, HIGH, MEDIUM)
- Show affected trains and risk details
- Allow operators to acknowledge alerts

**Excluded from MVP**:
- ❌ Alert history (90-day retention)
- ❌ Complex alert lifecycle management
- ❌ Alert resolution tracking
- ❌ Multi-channel notifications

### 5. Dashboard UI (Demo-Ready)
**Scope**: Single-page dashboard with map and alerts
- Interactive map showing train positions (using Mapbox or Leaflet)
- Alert panel showing active alerts
- Simple train info panel on click
- Basic system status indicator

**Excluded from MVP**:
- ❌ Multiple dashboard views
- ❌ Advanced filtering and search
- ❌ Historical data visualization
- ❌ Performance metrics dashboard
- ❌ User authentication

### 6. AI-Driven Suggestions (Basic)
**Scope**: Simple corrective suggestions
- Generate 1-2 basic suggestions per alert (speed reduction, emergency stop)
- Display suggestions with simple descriptions
- Show which trains are affected

**Excluded from MVP**:
- ❌ Complex suggestion ranking
- ❌ Multiple strategy types
- ❌ Suggestion outcome tracking
- ❌ ML-based suggestion optimization

### 7. Simulated Data Generator
**Scope**: Generate realistic train movement data
- Simulate 10-20 trains on predefined routes
- Create collision scenarios for demonstration
- Generate signal state changes
- Configurable scenario triggers

**Excluded from MVP**:
- ❌ Integration with real railway data
- ❌ Complex network topology
- ❌ Historical data replay

---

## MVP Architecture (Simplified)

### High-Level Architecture

```
┌─────────────────┐
│  Data Simulator │ (Python script)
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Backend API    │ (FastAPI)
│  - REST API     │
│  - WebSocket    │
│  - Risk Engine  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  In-Memory DB   │ (SQLite or dict)
└─────────────────┘
         │
         ▼
┌─────────────────┐
│  Dashboard UI   │ (React)
│  - Map View     │
│  - Alert Panel  │
└─────────────────┘
```

### Simplified Components

#### 1. Data Simulator (Python)
- **Purpose**: Generate simulated train movements and scenarios
- **Implementation**: Simple Python script with configurable scenarios
- **Output**: POST data to backend API every 2-5 seconds

#### 2. Backend API (FastAPI)
- **Purpose**: Process data, detect risks, serve dashboard
- **Components**:
  - REST endpoints for train data and alerts
  - WebSocket for real-time updates
  - Simple rule-based risk detection engine
  - Basic ML scoring (distance/speed calculations)
- **Storage**: In-memory Python dictionaries or SQLite

#### 3. Dashboard UI (React)
- **Purpose**: Visualize trains and alerts
- **Components**:
  - Map component with train markers
  - Alert list component
  - Train detail panel
  - WebSocket client for updates

---

## MVP Tech Stack (Minimal)

### Backend

#### Core Framework
- **Python 3.11+** - Programming language
- **FastAPI 0.104+** - Web framework
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation

#### Data Storage (Simplified)
- **SQLite** - Lightweight file-based database (or in-memory dicts)
- **No Kafka** - Direct API calls instead
- **No Redis** - In-memory state in Python
- **No TimescaleDB** - SQLite is sufficient for MVP

#### ML/AI (Minimal)
- **NumPy** - Basic calculations
- **scikit-learn** (optional) - Simple ML scoring
- **No XGBoost** - Use rule-based + simple formulas for MVP

#### Testing (Optional for MVP)
- **pytest** - Basic unit tests only
- **No property-based testing** - Skip for MVP
- **No load testing** - Not needed for demo

### Frontend

#### Core Framework
- **React 18** - UI framework
- **TypeScript** (optional) - Can use JavaScript for speed
- **Vite** - Build tool

#### UI Components
- **Leaflet** or **Mapbox GL JS** - Map visualization
  - *Recommendation*: Use **Leaflet** (free, no API key needed)
- **Basic CSS** or **Tailwind CSS** - Styling (skip Material-UI for speed)
- **No Redux** - Use React Context or simple state

#### HTTP Client
- **Axios** or **fetch** - API calls
- **WebSocket API** - Built-in browser WebSocket

### Development Tools

#### Containerization (Optional)
- **Docker** - For consistent environment (optional for MVP)
- **No Docker Compose** - Run services directly

#### Version Control
- **Git** - Source control
- **GitHub** - Code hosting

#### Code Quality (Minimal)
- **Black** - Python formatter (optional)
- **ESLint** - JavaScript linter (optional)
- **Skip mypy, Ruff** - Not critical for MVP

### Deployment (Simplified)

#### Option 1: Local Demo
- Run backend and frontend locally
- No cloud deployment needed
- Use `localhost` for demo

#### Option 2: Simple Cloud Deployment
- **AWS EC2** - Single instance for backend
- **AWS S3 + CloudFront** - Static frontend hosting
- **No ECS, no RDS, no MSK** - Too complex for MVP

#### Option 3: Serverless (Fastest)
- **Vercel** or **Netlify** - Frontend hosting (free tier)
- **AWS Lambda + API Gateway** - Backend (if needed)
- **No infrastructure management**

---

## MVP Requirements (Subset)

### From Full Requirements - Keep These:

✅ **Requirement 1**: Real-Time Train Monitoring (simplified to 10-20 trains)  
✅ **Requirement 2**: Signal Conflict Detection (basic rules only)  
✅ **Requirement 3**: Collision Risk Prediction (simplified calculation)  
✅ **Requirement 4**: AI-Driven Corrective Suggestions (1-2 basic suggestions)  
✅ **Requirement 7**: Centralized Command Dashboard (single view)  
✅ **Requirement 8**: Alert Management System (basic create/acknowledge)

### From Full Requirements - Defer These:

⏸️ **Requirement 5**: Routing Risk Analysis (defer to post-MVP)  
⏸️ **Requirement 6**: Network Congestion Monitoring (defer to post-MVP)  
⏸️ **Requirement 9**: Data Integration (use simulator instead)  
⏸️ **Requirement 10**: Scalability (not needed for demo)  
⏸️ **Requirement 11**: Advanced ML (use simple rules + formulas)  
⏸️ **Requirement 12**: Fault Tolerance (not critical for demo)

---

## MVP Design (Simplified)

### Data Models (Minimal)

```python
# Train
class Train:
    train_id: str
    position: tuple[float, float]  # (lat, lon)
    speed: float  # km/h
    heading: float  # degrees
    route_id: str
    status: str  # "RUNNING" | "STOPPED" | "ALERT"

# Alert
class Alert:
    alert_id: str
    alert_type: str  # "COLLISION" | "SIGNAL_CONFLICT"
    severity: str  # "CRITICAL" | "HIGH" | "MEDIUM"
    affected_trains: list[str]
    message: str
    timestamp: float
    acknowledged: bool

# Suggestion
class Suggestion:
    suggestion_id: str
    alert_id: str
    action: str  # "REDUCE_SPEED" | "EMERGENCY_STOP"
    description: str
    affected_trains: list[str]
```

### API Endpoints (Minimal)

```
GET  /api/trains              - Get all active trains
GET  /api/alerts              - Get active alerts
POST /api/alerts/{id}/ack     - Acknowledge alert
GET  /api/suggestions/{alert} - Get suggestions for alert
WS   /ws                      - WebSocket for real-time updates
```

### Risk Detection Logic (Simplified)

```python
def detect_collision_risk(train1, train2):
    """Simple collision detection"""
    distance = calculate_distance(train1.position, train2.position)
    
    # Check if trains are close and on converging paths
    if distance < 5000:  # 5km threshold
        # Calculate time to collision
        relative_speed = abs(train1.speed - train2.speed)
        if relative_speed > 0:
            time_to_collision = distance / (relative_speed * 1000/3600)
            
            # If collision within 5 minutes, raise alert
            if time_to_collision < 300:  # 5 minutes
                probability = 1 - (distance / 5000)  # Simple formula
                return Alert(
                    alert_type="COLLISION",
                    severity="CRITICAL" if probability > 0.7 else "HIGH",
                    affected_trains=[train1.train_id, train2.train_id],
                    message=f"Collision risk in {time_to_collision:.0f}s"
                )
    return None
```

---

## MVP Development Plan (2-3 Weeks)

### Week 1: Core Backend + Data Simulator
**Days 1-2**: Project setup
- Initialize Python project with FastAPI
- Create basic data models
- Set up SQLite database

**Days 3-4**: Data simulator
- Create train movement simulator
- Generate collision scenarios
- Test data generation

**Days 5-7**: Risk detection engine
- Implement collision detection logic
- Implement signal conflict detection
- Create alert generation
- Add basic suggestion generator

### Week 2: Dashboard UI
**Days 8-9**: React setup + Map
- Initialize React project
- Integrate Leaflet map
- Display train markers

**Days 10-11**: Alert UI
- Create alert list component
- Add train detail panel
- Implement WebSocket connection

**Days 12-14**: Integration + Polish
- Connect frontend to backend
- Test real-time updates
- Add basic styling
- Fix bugs

### Week 3: Demo Preparation
**Days 15-17**: Demo scenarios
- Create compelling demo scenarios
- Add demo mode with scripted events
- Prepare presentation materials

**Days 18-19**: Testing + Refinement
- End-to-end testing
- Performance optimization
- UI polish

**Days 20-21**: Documentation + Deployment
- Write README and demo guide
- Deploy to cloud (if needed)
- Prepare hackathon submission

---

## MVP Success Criteria

### Functional Requirements
✅ Display 10-20 trains moving on a map in real-time  
✅ Detect and alert on collision risks automatically  
✅ Detect and alert on signal conflicts  
✅ Generate 1-2 corrective suggestions per alert  
✅ Allow operators to acknowledge alerts  
✅ Update dashboard in real-time via WebSocket

### Demo Requirements
✅ Run stable demo for 5-10 minutes without crashes  
✅ Show at least 2 collision scenarios  
✅ Show at least 1 signal conflict scenario  
✅ Demonstrate alert acknowledgment  
✅ Show suggestions being generated  
✅ Professional-looking UI

### Technical Requirements
✅ Backend responds within 500ms for API calls  
✅ WebSocket updates every 2-5 seconds  
✅ Map renders smoothly with 20 trains  
✅ No critical bugs during demo  
✅ Code is documented and readable

---

## What We're NOT Building (MVP)

### Infrastructure
❌ Kubernetes/ECS orchestration  
❌ Multi-region deployment  
❌ Auto-scaling  
❌ Load balancers  
❌ CDN for assets

### Data & Storage
❌ TimescaleDB with hypertables  
❌ Apache Kafka message queue  
❌ Redis caching layer  
❌ Data persistence beyond demo  
❌ Database migrations

### ML & AI
❌ Trained XGBoost models  
❌ Historical pattern analysis  
❌ Anomaly detection  
❌ Model training pipeline  
❌ Feature engineering

### Testing
❌ Property-based tests  
❌ Load testing  
❌ Integration test suite  
❌ E2E testing  
❌ 100+ test coverage

### Features
❌ User authentication  
❌ Multi-user support  
❌ Historical data analysis  
❌ Advanced filtering/search  
❌ Routing risk analysis  
❌ Network congestion monitoring  
❌ Alert history (90 days)  
❌ Suggestion outcome tracking  
❌ Performance metrics dashboard

### Production Readiness
❌ Security hardening  
❌ Monitoring and alerting  
❌ Backup and recovery  
❌ Disaster recovery  
❌ Compliance certifications  
❌ Production documentation

---

## Post-MVP Roadmap

### Phase 2: Enhanced ML (Post-Hackathon)
- Train actual XGBoost model on historical data
- Implement advanced trajectory prediction
- Add anomaly detection
- Improve suggestion quality

### Phase 3: Scalability (Production Prep)
- Migrate to TimescaleDB + Kafka architecture
- Add Redis caching
- Implement horizontal scaling
- Add load balancing

### Phase 4: Advanced Features
- Routing risk analysis
- Network congestion monitoring
- Historical playback
- Advanced analytics dashboard

### Phase 5: Production Deployment
- Security hardening
- Monitoring and alerting
- Multi-region deployment
- Compliance and certifications

---

## MVP Package Dependencies

### Backend (requirements.txt)
```
fastapi==0.104.1
uvicorn[standard]==0.24.0
pydantic==2.5.0
numpy==1.26.2
python-multipart==0.0.6
websockets==12.0
```

### Frontend (package.json)
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "leaflet": "^1.9.4",
    "react-leaflet": "^4.2.1",
    "axios": "^1.6.2"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.2.0",
    "vite": "^5.0.0"
  }
}
```

---

## MVP File Structure

```
trace-mvp/
├── backend/
│   ├── main.py              # FastAPI app
│   ├── models.py            # Data models
│   ├── risk_engine.py       # Risk detection logic
│   ├── simulator.py         # Data simulator
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── App.jsx          # Main app component
│   │   ├── Map.jsx          # Map component
│   │   ├── AlertPanel.jsx   # Alert list
│   │   └── api.js           # API client
│   ├── package.json
│   └── index.html
├── README.md
└── demo-scenarios.json      # Predefined demo scenarios
```

---

## Key MVP Decisions

### Why SQLite instead of TimescaleDB?
- No setup required
- Sufficient for 20 trains
- Easy to demo locally
- Can migrate later

### Why Leaflet instead of Mapbox?
- Free and open source
- No API key needed
- Simpler integration
- Good enough for demo

### Why skip Kafka?
- Overkill for MVP
- Direct API calls are simpler
- Faster development
- Can add later for scale

### Why skip Redux?
- React Context is sufficient
- Less boilerplate
- Faster development
- Simpler for small app

### Why skip comprehensive testing?
- Focus on working demo
- Manual testing is sufficient
- Add tests post-hackathon
- Time constraint priority

---

**Last Updated**: February 2026  
**Version**: 1.0 (MVP Scope)  
**Status**: Ready for Implementation  
**Target**: AWS AI for Bharat Hackathon
