# MERIT GAMES - SIMULATION OVERVIEW

## CORE ARCHITECTURE

### The Game Engine
A 10-week life simulation where students navigate career decisions while competing on visible metrics and unknowingly being scored on cooperation.

### Three Layers of Play
1. **Surface Layer**: Traditional success metrics competition
2. **Hidden Layer**: Cooperation tracking and collective benefit scoring  
3. **Meta Layer**: Recognition that the game itself is the problem

## KEY COMPONENTS

### Time Structure
- **10 weeks** = 10 simulated years
- **Weekly cycle**: Market Update → Decisions → Consequences → Social Phase
- **Real-time pressure**: 24-48 hour decision windows
- **Accelerating complexity**: Crisis frequency increases each week

### Scoring System
**Visible Metrics (60%)**
- Salary: Career earnings trajectory
- Influence: Impact and reach
- Reputation: Trust and consistency  
- Network: Connection quality/quantity

**Hidden Metric (40%)**
- Collective Vitality: Cooperation, knowledge-sharing, positive-sum choices
- Multiplies over time, compounds in final weeks
- Only revealed at game's end

### Decision Types
- **Career**: Job moves, industry pivots, education
- **Resources**: Time, money, political capital allocation
- **Crisis**: Scandals, health, family, economic shocks
- **Ethics**: Whistleblowing, loyalty, information sharing
- **Social**: Relationships, alliances, betrayals

## GAME FLOW

```mermaid
graph TB
    subgraph "VISIBLE GAME"
        A[Initial Conditions<br/>Debt • City • Network] --> B[Weekly Decisions]
        B --> C[Salary]
        B --> D[Influence]
        B --> E[Reputation]
        B --> F[Network]
        C --> G[LEADERBOARD]
        D --> G
        E --> G
        F --> G
    end
    
    subgraph "HIDDEN GAME"
        H[Share Information] --> K[Collective<br/>Vitality]
        I[Help Competitors] --> K
        J[Choose We Over Me] --> K
        K --> L[MULTIPLIER<br/>EFFECT]
    end
    
    subgraph "WEEK 10: REVELATION"
        G --> M[Traditional<br/>Winners]
        L --> N[True<br/>Winners]
        M --> O[THE PARADOX:<br/>Individual optimization failed.<br/>Cooperation was rational.]
        N --> O
    end
    
    style A fill:#e1f5fe
    style G fill:#ffecb3
    style K fill:#c8e6c9
    style L fill:#81c784,stroke:#333,stroke-width:3px
    style O fill:#ff6b6b,color:#fff,stroke:#333,stroke-width:3px
```

### The Architecture of Deception

```mermaid
flowchart LR
    subgraph "WEEK 1-3: ESTABLISHING"
        A1[Learn Rules] --> A2[Optimize Metrics]
        A2 --> A3[Early Leaders Emerge]
    end
    
    subgraph "WEEK 4-6: COMPETING"
        B1[Zero-Sum Thinking] --> B2[Betrayals Begin]
        B2 --> B3[Trust Erodes]
    end
    
    subgraph "WEEK 7-9: ESCALATING"
        C1[Algorithm Adapts] --> C2[Old Strategies Fail]
        C2 --> C3[Desperation Peaks]
    end
    
    subgraph "WEEK 10: REVEALING"
        D1[Collective Crisis] --> D2[Only Cooperation Works]
        D2 --> D3[Hidden Metric Revealed]
        D3 --> D4[Everything Recontextualizes]
    end
    
    A3 --> B1
    B3 --> C1
    C3 --> D1
    
    style A1 fill:#e3f2fd
    style B2 fill:#fff3e0
    style C2 fill:#ffebee
    style D3 fill:#e8f5e9
    style D4 fill:#311b92,color:#fff
```

## ALGORITHMIC BEHAVIOR

### Adaptive Elements
- **Rule Changes**: Unannounced shifts in what behaviors reward
- **Counter-Strategies**: Algorithm learns and blocks dominant patterns
- **Information Asymmetry**: Different players see different opportunities
- **Noise Injection**: False signals mixed with real data

### Real-World Integration
- Stock market movements affect game economy
- News events trigger crisis scenarios
- Class dynamics influence game state
- Professor can inject wild cards

## INTERACTION DYNAMICS

### Competition Mechanics
- Zero-sum: Jobs, network connections are finite
- Relative scoring: Influence measured against peers
- Reputation attacks: Can damage others
- Information hoarding: Knowledge as currency

### Cooperation Mechanics  
- Information sharing: Helps all, costs individual advantage
- Mutual support: Crisis assistance
- Joint ventures: Shared risk/reward
- Collective action: Some problems only solvable together

## THE REVELATION

### Week 10 Transformation
1. Individual optimization strategies begin failing
2. Collective action problems emerge requiring cooperation
3. Hidden metric multipliers activate
4. True algorithm revealed: rewards collaboration exponentially
5. "Winners" realize the game's real lesson

### Three Possible Outcomes
- **Win the Wrong Game**: Top visible metrics, low cooperation
- **Discover the Hidden Game**: Balance visible and hidden success
- **Reject the Game**: Recognize system's fundamental flaws

## DESIGN PHILOSOPHY

The simulation is a **trap that teaches**:
- Mirrors real-world incentive structures
- Rewards individual optimization initially
- Punishes pure self-interest eventually  
- Reveals cooperation as rational strategy
- Questions what "winning" means

The cruelest truth: Even understanding the game completely doesn't free you from playing it.

## CINEMATIC TRANSLATION

### Visual Representation
- **Dashboard Aesthetic**: Clean, corporate, seductive
- **Leaderboard Drama**: Public rankings drive tension
- **Decision Moments**: Time pressure visualization
- **Crisis Alerts**: Breaking news style interruptions
- **Revelation Sequence**: Hidden metrics emerge like virus spreading

### Narrative Function
- Externalizes internal character conflicts
- Makes abstract themes concrete
- Provides clear stakes/consequences
- Enables betrayal mechanics
- Forces moral choices under pressure

The game isn't just plot device—it's the film's central metaphor for how algorithms shape human behavior by defining what we optimize for, while hiding what actually matters.