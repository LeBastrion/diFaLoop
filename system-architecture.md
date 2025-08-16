# Dialectic Engine Architecture

## System Flow Visualization

```mermaid
graph TB
    Start([Start: New Question/Data]) --> Init[Initialize Branch & Directories]
    Init --> LoadData[Load Data to data/]
    
    LoadData --> Cycle{Begin Cycle N}
    
    Cycle --> Observer[Observer Agent]
    Observer -->|reads: data/*| ObsOut[writes: reasoning/observations.md]
    
    ObsOut --> Theorist[Theorist Agent]
    Theorist -->|reads: data/* + observations.md| TheoryOut[writes: reasoning/hypotheses.md]
    
    TheoryOut --> Falsifier[Falsifier Agent]
    Falsifier -->|reads: data/* + hypotheses.md| FalsOut[writes: reasoning/falsifications.md]
    
    FalsOut --> TensionHolder[Tension Holder Agent]
    TensionHolder -->|reads: reasoning/*| TensionOut[writes: reasoning/tensions.md]
    
    TensionOut --> CheckCycle{Cycle % 3 == 0?}
    CheckCycle -->|Yes| Distiller[Distiller Agent]
    CheckCycle -->|No| CheckStop
    
    Distiller -->|reads: reasoning/* + archive/*| DistillOut[writes: reasoning/distilled.md]
    DistillOut --> Archive[Archive reasoning/ to archive/cycle_N/]
    Archive --> CheckStop
    
    CheckStop{Check Stop Conditions}
    CheckStop -->|Convergence:<br/>No falsifications 3x| Final
    CheckStop -->|Oscillation:<br/>Same tensions 3x| Final
    CheckStop -->|Exhaustion:<br/>No new hypotheses| Final
    CheckStop -->|Saturation:<br/>Distilled size plateau| Final
    CheckStop -->|Continue| NextCycle[Increment Cycle Counter]
    
    NextCycle --> Cycle
    
    Final[Generate final_result.md] --> Push[Push to Branch with 'FIN']
    Push --> End([End])
    
    style Observer fill:#e1f5fe
    style Theorist fill:#fff3e0
    style Falsifier fill:#ffebee
    style TensionHolder fill:#f3e5f5
    style Distiller fill:#e8f5e9
    style Final fill:#fff59d
```

## Agent Isolation Principle

```mermaid
graph LR
    subgraph "Each Agent Call"
        A[Fresh Context] --> B[No Memory]
        B --> C[Pure Function]
        C --> D[File Output]
    end
    
    subgraph "Information Flow"
        Data[data/*] --> O[Observer]
        O --> OF[observations.md]
        OF --> T[Theorist]
        Data --> T
        T --> TF[hypotheses.md]
        TF --> F[Falsifier]
        Data --> F
        F --> FF[falsifications.md]
        FF --> TH[Tension Holder]
        OF --> TH
        TF --> TH
        TH --> THF[tensions.md]
    end
```

## Directory Structure Evolution

```mermaid
graph TD
    subgraph "Cycle 1-2"
        D1[data/] --> R1[reasoning/<br/>- observations.md<br/>- hypotheses.md<br/>- falsifications.md<br/>- tensions.md]
    end
    
    subgraph "Cycle 3"
        D3[data/] --> R3[reasoning/<br/>+ distilled.md]
        R3 --> A3[archive/cycle_3/]
    end
    
    subgraph "Cycle 6"
        D6[data/] --> R6[reasoning/<br/>updated files]
        A6[archive/<br/>- cycle_3/<br/>- cycle_6/]
    end
    
    subgraph "Final"
        RF[final_result.md<br/>- Surviving hypotheses<br/>- Irreducible tensions<br/>- Meta-observations]
    end
```

## Key Principles

- **No Memory Between Calls**: Each agent invocation is stateless
- **File-Based Communication**: All outputs written to files for persistence
- **Sequential Processing**: Strict order ensures dialectical reasoning
- **Periodic Compression**: Distiller reduces complexity every 3 cycles
- **Automatic Termination**: Multiple stop conditions prevent infinite loops