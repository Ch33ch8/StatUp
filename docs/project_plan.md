# StatUp Project Plan
**Pokemon Battle Predictor & Team Optimizer**

## 1. Project Overview

### Mission
Build a machine learning platform that predicts Pokemon battle outcomes and optimizes team compositions for competitive play.

### Target Users
- Competitive Pokemon players
- Casual fans interested in team building
- Recruiters evaluating technical skills

### Success Metrics
- Predict battle outcomes with >70% accuracy
- Suggest team improvements that increase win probability
- Showcase full-stack development + ML skills

---

## 2. Tech Stack & Rationale

### Backend
- **Python** - Industry standard for ML/data science
- **FastAPI** - Modern, fast API framework with auto-documentation
- **SQLite → PostgreSQL** - Start simple, scale up later

### Machine Learning
- **Scikit-learn** - Beginner-friendly, excellent documentation
- **Pandas** - Data manipulation and feature engineering
- **NumPy** - Numerical computations

### Frontend
- **React** - Component-based, popular with recruiters
- **Chart.js** - Battle prediction visualizations
- **Tailwind CSS** - Modern, utility-first styling

### Data Sources
- **PokeAPI** - Pokemon stats, moves, types, abilities
- **Pokemon Showdown** - Battle replay data (future)
- **Smogon** - Usage statistics and tier data (future)

---

## 3. Database Schema

### Core Tables

**pokemon**
- id, name, hp, attack, defense, special_attack, special_defense, speed
- height, weight, base_experience

**types**
- id, name

**pokemon_types** (junction)
- pokemon_id, type_id, slot (primary/secondary)

**moves**
- id, name, type_id, power, accuracy, pp, damage_class, priority

**pokemon_moves** (junction)
- pokemon_id, move_id

**abilities**
- id, name, description

**pokemon_abilities** (junction)
- pokemon_id, ability_id, is_hidden

**type_effectiveness**
- attacking_type_id, defending_type_id, multiplier

### Future Tables

**teams** (when we add user accounts)
- id, user_id, name, created_at

**team_pokemon** (junction)
- team_id, pokemon_id, moveset

**battles** (for training data)
- id, team1_id, team2_id, winner, battle_data

---

## 4. Development Phases

### Phase 1: Foundation (Weeks 1-2) ✅ IN PROGRESS
**Goals:**
- Project setup and planning
- Environment configuration
- Initial PokeAPI exploration

**Deliverables:**
- ✅ GitHub repo created
- ✅ README, .gitignore, requirements.txt
- ✅ Virtual environment setup
- ✅ Jupyter notebook with PokeAPI exploration
- [ ] Database schema finalized
- [ ] Project structure folders created

---

### Phase 2: Data Collection (Weeks 3-4)
**Goals:**
- Build data pipeline from PokeAPI
- Populate local database
- Create data validation system

**Tasks:**
1. Write Pokemon scraper script
2. Create database and tables
3. Fetch and store all Pokemon (1000+)
4. Fetch and store types, moves, abilities
5. Build type effectiveness matrix
6. Data validation and cleaning

**Deliverables:**
- `src/data/pokemon_scraper.py`
- Populated SQLite database
- Data quality report

---

### Phase 3: Battle Mechanics Engine (Weeks 5-6)
**Goals:**
- Implement core battle calculations
- Type effectiveness system
- Damage calculation formulas

**Tasks:**
1. Research Pokemon damage formulas
2. Build type effectiveness calculator
3. Create damage calculator
4. Speed-based turn order system
5. Critical hits and STAB bonuses
6. Unit tests for battle mechanics

**Deliverables:**
- `src/utils/battle_calculator.py`
- `src/utils/type_effectiveness.py`
- Test suite with >80% coverage

---

### Phase 4: Feature Engineering (Weeks 7-8)
**Goals:**
- Create features for ML models
- Build training dataset

**Features to Engineer:**
- Team offensive coverage (how many types covered)
- Team defensive coverage (resistances/immunities)
- Stat distributions (balanced vs specialized)
- Speed tiers (who moves first)
- Offensive threat score
- Defensive core strength
- Synergy metrics between Pokemon

**Deliverables:**
- `src/models/feature_engineering.py`
- Training dataset (CSV/database)
- Feature documentation

---

### Phase 5: Machine Learning Models (Weeks 9-10)
**Goals:**
- Train battle prediction models
- Optimize team composition

**Models:**
1. **Binary Classifier** - Team A vs Team B winner
2. **Win Probability** - Regression for win percentage
3. **Team Optimizer** - Genetic algorithm or gradient descent

**Tasks:**
1. Split data (train/validation/test)
2. Train baseline models
3. Feature selection and tuning
4. Cross-validation
5. Model evaluation and comparison
6. Save best models

**Deliverables:**
- `src/models/battle_predictor.py`
- `src/models/team_optimizer.py`
- Trained model files (.pkl)
- Model performance report

---

### Phase 6: Backend API (Weeks 11-12)
**Goals:**
- Build REST API
- Integrate ML models

**Endpoints:**
- `GET /api/pokemon` - List all Pokemon
- `GET /api/pokemon/{id}` - Get Pokemon details
- `POST /api/predict-battle` - Predict battle outcome
- `POST /api/optimize-team` - Get team suggestions
- `GET /api/types` - Get type chart
- `GET /api/moves` - Search moves

**Deliverables:**
- `src/api/main.py`
- API documentation (auto-generated by FastAPI)
- Integration tests

---

### Phase 7: Frontend Interface (Weeks 13-14)
**Goals:**
- Build interactive web UI
- Connect to backend API

**Pages/Components:**
1. **Team Builder**
   - Drag-and-drop Pokemon selection
   - View team stats and coverage
   
2. **Battle Predictor**
   - Input two teams
   - Display win probability
   - Show key matchups
   
3. **Team Optimizer**
   - Submit current team
   - Get optimization suggestions
   - Compare before/after stats

4. **Pokemon Explorer**
   - Search and filter Pokemon
   - View detailed stats

**Deliverables:**
- React application
- Responsive design
- Data visualizations

---

### Phase 8: Polish & Deploy (Weeks 15-16)
**Goals:**
- Testing and bug fixes
- Documentation
- Deployment

**Tasks:**
1. End-to-end testing
2. Performance optimization
3. Security review
4. Write comprehensive README
5. Create demo video
6. Deploy to cloud (Heroku/Vercel/AWS)
7. Domain name setup

**Deliverables:**
- Live application URL
- Demo video for portfolio
- Complete documentation

---

## 5. MVP vs Future Features

### MVP (Minimum Viable Product)
- [x] PokeAPI integration
- [ ] Database with Pokemon/types/moves
- [ ] Type effectiveness calculator
- [ ] Basic battle prediction model
- [ ] Simple team builder UI
- [ ] Win probability display

### Future Enhancements
- [ ] User accounts and saved teams
- [ ] Pokemon Showdown replay analysis
- [ ] Meta analysis (most popular Pokemon/teams)
- [ ] Move recommendation system
- [ ] EV/IV optimization
- [ ] Competitive tier filtering (OU, UU, etc.)
- [ ] Mobile app
- [ ] Real-time battle simulation
- [ ] Social features (share teams)

---

## 6. Learning Goals

### Machine Learning
- Classification and regression
- Feature engineering
- Model evaluation and tuning
- Optimization algorithms

### APIs
- RESTful API design
- API consumption (PokeAPI)
- API development (FastAPI)
- Authentication (future)

### Data Engineering
- Web scraping
- Database design
- Data validation
- ETL pipelines

### Full-Stack Development
- Backend (Python/FastAPI)
- Frontend (React)
- Database (SQL)
- Deployment

### Software Engineering
- Git version control
- Project planning
- Testing (unit, integration)
- Documentation

---

## 7. Portfolio Presentation

### README Highlights
- Problem statement
- Technical architecture diagram
- Key features with screenshots
- Tech stack explanation
- Installation instructions
- Live demo link

### Demo Talking Points
1. "Built end-to-end ML pipeline from data collection to deployment"
2. "Engineered features based on Pokemon battle mechanics"
3. "Achieved X% prediction accuracy through feature engineering"
4. "Designed RESTful API with FastAPI"
5. "Created interactive React frontend with real-time predictions"

---

## 8. Timeline Summary

**Total Duration:** 16 weeks (4 months)

- Weeks 1-2: Foundation ← **WE ARE HERE**
- Weeks 3-4: Data Collection
- Weeks 5-6: Battle Engine
- Weeks 7-8: Feature Engineering
- Weeks 9-10: ML Models
- Weeks 11-12: Backend API
- Weeks 13-14: Frontend
- Weeks 15-16: Deploy & Polish

**Realistic Adjustment:** If working part-time, double the timeline (8 months)

---

## 9. Risk Management

### Potential Challenges
1. **PokeAPI rate limits** - Cache data locally
2. **Large dataset** - Start with Gen 1 Pokemon only
3. **Complex battle mechanics** - Simplify for MVP
4. **ML model accuracy** - Focus on type matchups first
5. **Scope creep** - Stick to MVP, add features later

### Mitigation Strategies
- Build incrementally
- Test frequently
- Document decisions
- Ask for help when stuck
- Celebrate small wins

---

## 10. Next Immediate Steps

1. [ ] Finalize database schema
2. [ ] Create project folder structure
3. [ ] Build Pokemon scraper script
4. [ ] Set up SQLite database
5. [ ] Fetch first 151 Pokemon (Gen 1)

---

**Last Updated:** [Today's Date]
**Status:** Phase 1 - Foundation (In Progress)