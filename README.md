Rational Agents: Lions vs. Hyenas – NetLogo Simulation
Practical Assignment #1 – Introduction to Artificial Intelligence
BSc in Informatics Engineering (Regular, Part-Time & European Course) – 2nd Year, 1st Semester – 2023/2024
ISEC – Instituto Superior de Engenharia de Coimbra

Project Overview
This repository contains the complete implementation of Practical Assignment #1 from the Introduction to Artificial Intelligence course at ISEC. The project involves designing, implementing, and analyzing rational reactive agents (lions and hyenas) in a competitive survival simulation using NetLogo.
Core Objective: Maximize agent survival time in a toroidal world with limited resources, local perceptions, energy management, and competitive interactions.

Repository Structure

IIA_TP_v0.nlogo – Base model (initial implementation)
IIA_TP_v1.nlogo – Improved model (full features + experiments)
TP1.pdf – Official assignment specification (Portuguese)
Relatorio.docx – Final report (analysis, results, conclusions)
images/ – Screenshots and diagrams
experiments/ – BehaviorSpace output (CSV)
README.md – This file


Environment (as per specification)
Toroidal 2D Grid (open world):

Black: Empty – movement allowed
Brown: Small food – energy gain energP (1–25), respawns randomly
Red: Large food – energy gain energG (1–50), becomes brown after eaten
Blue: Safe zone – 0–5 cells (configurable), lions rest here

Food Distribution (user-configurable):

Small food: 0–20%
Large food: 0–10%
Respawn maintains approximate % over time


Agents
Lion Agent (leoes)

Perceptions: 3 cells (front, left, right) – see Figure 1 in TP1.pdf
Actions (1 per tick):

Eat (if energy < initial)
Move forward / Turn left / Turn right
Fight (1 hyena detected)
Special Escape (2+ hyenas) – 6 maneuvers:

2+ hyenas left only → Right 1 (cost 2)
2+ hyenas right only → Left 1 (cost 2)
2+ hyenas front or both sides → Back 1 (cost 3)
Front + left → Back-Left 1 (cost 5)
Front + right → Back-Right 1 (cost 5)
All sides → Back 2 (cost 4)




Energy: Lose 1 per normal action, 2–5 on escape

Hyena Agent (hienas)

Perceptions: Front, left, right
Grouping: agrupamento = 1 + nearby hyenas

Color: Green (solo) → Pink (group)


Actions:

Eat (priority)
Group Attack (if agrupamento > 1 and 1 lion detected)

Lion → Red food
Energy loss shared among group


Pack Movement: Leader dictates direction
Solo: Random move/turn


Death: energia < 1 → Die


Implemented Models
v0 (Base Model)

Full compliance with specification
Combat, grouping, food conversion, energy system

v1 (Improved Model)

Safe zones with immunity (tempoEspera)
Pre-computed vision (visao)
Lions exit safe zones after rest
Hyenas skip immune lions
Auto-stop at 8000 ticks or extinction
Live plot of agent counts
BehaviorSpace experiments (10+ configs)


Quick Start

Install: NetLogo 6.3.0+
Open: IIA_TP_v1.nlogo
Recommended Settings:

Lions: 42
Hyenas: 50
Lion Energy: 47
Hyena Energy: 50
Small Food: 10%
Large Food: 5%
Blue Cells: 3
Wait Time: 30
Lion Kill Cost: 90%
Hyena Kill Cost: 16%


Run: Setup → Go

Auto-stops at 8000 ticks or extinction




Experiments (BehaviorSpace in v1)
Tested Configurations (10–30 runs each):

pEnergHienaMorta: 0%, 50%, 100%
nhienas / nleoes: 20–100
energiahienas / energialeoes: 33, 66, 100
energG / energP: 0–50
tempoAzuis: 100, 200, 300
deuzero: Balanced config (30 runs)

Key Results:

Safe zones → +58% lion survival
Group attacks → Hyenas dominate without balance
Optimal: 42 lions / 50 hyenas → sustainable ecosystem


Key Improvements (v0 → v1)

Vision: On-the-fly → Pre-computed visao
Safe Zones: Visual only → Full immunity (tempoEspera)
Lion Rest Exit: Stuck → Auto fd 1 after wait
Hyena Attack: Always kills → Skip immune lions
Auto-Stop: – → 8000 ticks / extinction
Live Plot: – → Agent counts
Experiments: – → Full BehaviorSpace


Results Summary
Average Survival (ticks):

v0: ~500 ticks

Lions survive: 12%
Hyenas survive: 89%


v1: ~2500 ticks

Lions survive: 67%
Hyenas survive: 45%



Balanced survival achieved with safe zones and tuned energy costs.

Documentation

Specification: TP1.pdf – 100% compliant
Report: Relatorio.docx – 10 pages, 3 experiments/model
Code: Clean, commented (Portuguese)


Authors

Miguel Cardoso
João Pinto

Course: Introduction to Artificial Intelligence
Institution: ISEC – Instituto Superior de Engenharia de Coimbra
Academic Year: 2023/2024

License
Academic Use Only
