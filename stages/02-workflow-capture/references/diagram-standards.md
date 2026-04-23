# Mermaid Diagram Standards

Every workflow diagram produced in stage 02 follows these shape and color conventions. Apply them via `classDef` at the top of every `.mmd` file.

## Shape Conventions

| Node Type | Mermaid Syntax | Used For |
|-----------|---------------|----------|
| Terminal | `([Label])` | Start and end points |
| Process | `[Label]` | Actions, steps, tasks |
| Decision | `{Label}` | Yes/No or branching choices |

## Color Classes

```
classDef terminal fill:#E8E8E8,stroke:#999999,color:#333333
classDef process  fill:#D6EAF8,stroke:#2E86C1,color:#333333
classDef decision fill:#FFF3CD,stroke:#F0AD4E,color:#333333
classDef exception fill:#FADBD8,stroke:#E74C3C,color:#333333
classDef complete fill:#D5F5E3,stroke:#27AE60,color:#333333
```

## Class Assignments

| Class | Color | Applied To |
|-------|-------|------------|
| `terminal` | Light gray | Start node |
| `process` | Light blue | Standard process steps |
| `decision` | Amber | All decision diamonds |
| `exception` | Light red | Exception handling steps (kick back, delete, back-and-forth) |
| `complete` | Light green | Successful completion terminals |

## Usage

Declare classes after the flowchart direction line. Assign with `:::` inline or with a `class` statement at the bottom.

```
flowchart TD
    classDef terminal  fill:#E8E8E8,stroke:#999999,color:#333333
    classDef process   fill:#D6EAF8,stroke:#2E86C1,color:#333333
    classDef decision  fill:#FFF3CD,stroke:#F0AD4E,color:#333333
    classDef exception fill:#FADBD8,stroke:#E74C3C,color:#333333
    classDef complete  fill:#D5F5E3,stroke:#27AE60,color:#333333

    A([Start]):::terminal
    B[Process step]:::process
    C{Decision?}:::decision
    D[Exception handling]:::exception
    E([Done]):::complete
```
