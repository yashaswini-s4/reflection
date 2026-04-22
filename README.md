# Daily Reflection Tree
**DT Fellowship Assignment Submission**


## Overview

A deterministic daily reflection agent built as a branching decision tree. The system walks a user through a structured end-of-day reflection — no LLM is called at runtime. Every path through the tree is pre-authored, rule-based, and fully auditable.


## Part A — Tree Structure

The tree is defined as a flat TSV with these columns:

 Column     Purpose                                                         
 
 id         Unique node identifier                                          
 parentId   Node this branches from (null for root)                         
 type       start / question / reflect / end                                
 text       Question shown to the user                                      
 options    Pipe-separated choices, or text for free-text input           
 nextIds    Pipe-separated next node IDs matching each option               

### Tree Shape

Total nodes: 25 | Unique paths: 36+ | Depth per session: 8–9 steps

## Part B — The App

### How It Works

1. One question shown at a time
2. Choice nodes: user clicks a button → next node loads
3. Text nodes: user types a response → clicks Continue → next node loads
4. All answers accumulate in memory and show as a summary at the end
5. Back button allows stepping backward with full state restore

### Design Decisions

**No LLM at runtime.** Every next pointer is hard-coded. No API calls. Fully deterministic.

**Single-file deployment.** HTML + CSS + JS in one file. No build step, no npm, no server.

**Free-text nodes.** Going-deeper and axis questions use open text. The user's own words are preserved and shown in the final summary.

**Back navigation.** Each step pushes to a history stack. Back pops the stack and restores state.

### Stack

- Vanilla HTML + CSS + JS (ES6)
- Google Fonts from CDN
- Zero runtime dependencies


## Psychology Framework

**Axis 1 — Agency:** Based on Locus of Control (Rotter, 1954). Did you drive the day or react to it?

**Axis 2 — Radius of Self-Centrism:** Asks who your energy served — self, close others, team, or community — and whether that radius was the right one.

**Axis 3 — Orientation:** Informed by Growth Mindset (Dweck). The "do differently tomorrow" and gratitude questions orient toward forward motion and appreciation.



---

## Submission Note

The key design decision was where to converge the 9 opening branches. Converging at A3_AGENCY keeps the tree disciplined — every user, regardless of starting mood, reflects on the same three axes. This mirrors DT's PDGMS approach: constrained branching that always arrives at a structured, actionable output.
