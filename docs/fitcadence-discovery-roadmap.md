---
doc: ROAD-001
title: FitCadence – Discovery roadmap
version: 1.1
status: Complete (frozen)
updated: 2026-11-03
owner: Teodora
---

# FitCadence – Discovery roadmap

**Where I am now:** discovery (P0) is complete, vision v1.0 Approved · **Next:** delivery, starting with `P1.1 · Setup`. See `fitcadence-delivery-roadmap.md`.

## Map

Each box with 💬 is a separate Claude.ai chat. Context moves between chats only through documents and handoff blocks, not chat history.

```mermaid
---
config:
  theme: base
  themeVariables:
    background: '#ffffff'
    primaryColor: '#ffffff'
    primaryTextColor: '#111827'
    primaryBorderColor: '#6b7280'
    lineColor: '#374151'
    textColor: '#111827'
    titleColor: '#111827'
    clusterBkg: '#ffffff'
    clusterBorder: '#9ca3af'
    edgeLabelBackground: '#ffffff'
---
flowchart TB
    subgraph CANVAS[" "]
        direction TB

        subgraph S0["💬 Chat · P- · Project setup"]
            direction LR
            s1["SDLC approach<br/>& tool choices"] --> s2["Decisions<br/>D-01 … D-08"] --> s3["Project kit<br/>brief · instructions · skill"]
        end

        subgraph S1["💬 Chat · P0.1 · Vision interview · uses vision-interview skill"]
            direction LR
            v1["1 · Problem"] --> v2["2 · Users"] --> v3["3 · Goals G-n"] --> v4["4 · Learning L-n"]
            v4 --> v5["5 · Scope CAP-n / NG-n"] --> v6["6 · Constraints C-n"] --> v7["7 · Assumptions A-n<br/>& Risks R-n"] --> v8["8 · Wrap-up"]
            v8 --> d1[["📄 00-vision.md v0.x"]]
        end

        subgraph S2["💬 Chat · P0.2 · Vision review & challenge"]
            direction LR
            r1["Red-team:<br/>gaps, contradictions,<br/>scope creep"] --> r2["Route open questions Q-n<br/>to later phases"] --> g1{{"✅ My approval"}} --> d2[["📄 00-vision.md v1.0<br/>Approved"]]
        end

        subgraph NEXT["Next"]
            direction LR
            n1["P1 – P8 · Delivery<br/>see the delivery roadmap"]
        end

        S0 ==>|handoff + upload brief| S1
        S1 ==>|handoff + upload vision v0.x| S2
        S2 ==>|vision approved| NEXT
    end

    classDef canvas fill:#ffffff,stroke:#ffffff,color:#111827
    classDef step fill:#ffffff,stroke:#6b7280,color:#111827
    classDef done fill:#d1fae5,stroke:#059669,color:#064e3b
    classDef active fill:#dbeafe,stroke:#2563eb,stroke-width:3px,color:#1e3a8a
    classDef artifact fill:#fef3c7,stroke:#d97706,color:#78350f
    classDef gate fill:#fce7f3,stroke:#db2777,color:#831843

    class CANVAS canvas
    class s1,s2,s3,r1,r2 done
    class v1,v2,v3,v4,v5,v6,v7,v8 done
    class S0,S1,S2 done
    class NEXT,n1 active
    class d1,d2 artifact
    class g1 gate
```

**Legend:** green = done · blue (thick border) = next · yellow = document produced · pink = my approval gate

## Status tracker

| Context                          | Type              | Status                        | Output                                                            | Version                |
| -------------------------------- | ----------------- | ----------------------------- | ----------------------------------------------------------------- | ---------------------- |
| P- · Project setup               | 💬 Claude.ai chat | ✅ Done                       | Brief, Project instructions, vision-interview skill, this roadmap | BRIEF-001 v0.3         |
| P0.1 · Vision interview          | 💬 Claude.ai chat | ✅ Done (8 of 8 stages)       | `00-vision.md`; input: `Training_System_Spec.md`                  | vision v0.7, spec v0.4 |
| P0.2 · Vision review & challenge | 💬 Claude.ai chat | ✅ Done (approved 2026-11-03) | `00-vision.md` Approved                                           | vision v1.0            |
| P1 to P8 · Delivery              | ⌨️ and 💬         | ▶️ Next                       | See `fitcadence-delivery-roadmap.md`                              | ROAD-002 v0.1          |

## Status of this file

Frozen: P0 is complete. Update it only if discovery is reopened, for example a vision change that needs a new `P0.x` chat. Delivery tracking is in `fitcadence-delivery-roadmap.md`.

## Change log

- 1.1 (2026-11-03): Delivery split into its own roadmap (ROAD-002). The "Next" box now collapses P1 to P8 into one summary box. File marked complete and frozen. Removed the "how to keep this current" steps (no longer needed).
- 1.0 (2026-11-03): P0.2 done, vision v1.0 Approved. P1.1 active. Status tracker updated.
- 0.9 (2026-11-01): P0.1 done (all 8 interview stages green, vision v0.7). P0.2 active. Status tracker updated (brief v0.3, spec v0.4).
- 0.8 (2026-11-01): Interview stage 7 (Assumptions & Risks) marked done, stage 8 (Wrap-up) active. Status tracker updated (vision v0.6).
- 0.7 (2026-11-01): Interview stage 6 (Constraints) marked done, stage 7 (Assumptions & Risks) active. Status tracker updated (vision v0.5).
- 0.6 (2026-11-01): Interview stage 5 (Scope) marked done, stage 6 (Constraints) active. Status tracker updated (vision v0.4).
- 0.5 (2026-11-01): Interview stage 4 (Learning) marked done, stage 5 (Scope) active. Status tracker updated (vision v0.3).
- 0.4 (2026-11-01): Interview stage 3 (Goals) marked done, stage 4 (Learning) active. Status tracker and versions updated (brief v0.2, vision v0.2).
- 0.3 (2026-10-31): P0.1 in progress. Interview stages 1 (Problem) and 2 (Users) marked done, stage 3 (Goals) active. Status tracker updated.
- 0.2 (2026-10-31): Forced light theme and white canvas so the diagram stays readable in dark mode (VS Code, Claude.ai, GitHub).
- 0.1 (2026-10-31): Initial roadmap; Project setup done, P0.1 next.
