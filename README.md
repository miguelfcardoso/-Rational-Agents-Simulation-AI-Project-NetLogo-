🦁🐺 Rational Agents: Lions vs. Hyenas
NetLogo Simulation – Practical Assignment #1
Introduction to Artificial Intelligence

BSc in Informatics Engineering (Regular • Part-Time • European Course)
2nd Year – 1st Semester – 2023/2024
ISEC – Instituto Superior de Engenharia de Coimbra

🧠 Project Overview

This repository contains the complete implementation of Practical Assignment #1 from the Introduction to Artificial Intelligence course at ISEC.
The project focuses on designing and analyzing rational reactive agents – lions 🦁 and hyenas 🐺 – within a competitive survival simulation built using NetLogo.

🎯 Core Objective:
Maximize agent survival time in a toroidal world with limited resources, local perception, energy management, and competitive interactions.

📂 Repository Structure
File	Description
IIA_TP_v0.nlogo	Base model (initial implementation)
IIA_TP_v1.nlogo	Improved model (enhanced logic + experiments)
README.md	This documentation
TP1.pdf	Official assignment specification (Portuguese)
Relatorio.docx	Final report with analysis, results, and conclusions
🌍 Environment (Based on Specification)
🧭 World

Toroidal 2D Grid (wrap-around edges)

Color	Meaning	Notes
⚫ Black	Empty cell	Movement allowed
🟤 Brown	Small food	Energy gain energP (1–25); respawns randomly
🔴 Red	Large food	Energy gain energG (1–50); turns brown when eaten
🔵 Blue	Safe zone	0–5 cells (configurable); lions rest safely here
🌱 Food Distribution (User-Configurable)

Small food: 0–20%

Large food: 0–10%

Respawn maintains approximate food percentages over time

🦁 Lion Agent (leoes)

Perception:

Detects 3 cells ahead: front, left, right (see Figure 1 in TP1.pdf)

Actions (1 per tick):

🍖 Eat (if energy < initial)

🚶‍♂️ Move forward, turn left, or turn right

⚔️ Fight (if one hyena detected)

🏃‍♂️ Special Escape (if ≥2 hyenas nearby) – performs 6 maneuver types:

Situation	Maneuver	Energy Cost
2+ hyenas left	Turn right (1 cell)	2
2+ hyenas right	Turn left (1 cell)	2
Front or both sides	Move back (1 cell)	3
Front + left	Back-left (1 cell)	5
Front + right	Back-right (1 cell)	5
Surrounded	Back (2 cells)	4

Energy Consumption:

−1 per normal action

−2 to −5 per escape action

🐺 Hyena Agent (hienas)

Perception:

Detects front, left, and right cells

Grouping:
agrupamento = 1 + nearby hyenas

Color:
🟢 Solo hyena → 💗 Pink when grouped

Actions:

🍖 Eat (priority action)

👥 Group Attack (if grouped and 1 lion detected)

Converts the lion → red food

Energy loss shared among the group

🧭 Movement:

Grouped → Leader dictates direction

Solo → Random movement/turn

Death:
energia < 1 → 💀 Hyena dies

🧩 Implemented Models
🔸 v0 – Base Model

Fully compliant with specification

Includes combat, grouping, food conversion, and energy system

🔹 v1 – Improved Model

🔵 Safe zones with temporary immunity (tempoEspera)

👁️ Pre-computed vision system (visao)

🦁 Lions automatically exit safe zones after resting

🐺 Hyenas skip immune lions

⏱️ Auto-stop at 8000 ticks or species extinction

📊 Live plots tracking agent populations

🧪 BehaviorSpace experiments (10+ configurations)

⚙️ Quick Start

Install: NetLogo 6.3.0+

Open: IIA_TP_v1.nlogo

Recommended Settings:

Parameter	Value
Lions	42
Hyenas	50
Lion Energy	47
Hyena Energy	50
Small Food	10%
Large Food	5%
Blue Cells	3
Wait Time	30
Lion Kill Cost	90%
Hyena Kill Cost	16%

Run:
Setup → Go
(Simulation auto-stops at 8000 ticks or extinction)

🧪 Experiments (BehaviorSpace – v1)

Configurations Tested: (10–30 runs each)

pEnergHienaMorta: 0%, 50%, 100%

nhienas / nleoes: 20–100

energiahienas / energialeoes: 33, 66, 100

energG / energP: 0–50

tempoAzuis: 100, 200, 300

deuzero: Balanced configuration (30 runs)

📈 Key Results

🔵 Safe zones → +58% lion survival rate

👥 Group attacks → Hyenas dominate if unbalanced

⚖️ Optimal setup: 42 lions / 50 hyenas → Sustainable coexistence

🔁 Key Improvements (v0 → v1)
Feature	v0	v1
Vision	On-the-fly	Pre-computed (visao)
Safe Zones	Visual only	Full immunity (tempoEspera)
Lion Rest Exit	Stuck	Auto forward after wait
Hyena Attack	Always fatal	Skips immune lions
Auto-Stop	—	✅ 8000 ticks/extinction
Live Plot	—	✅ Agent counts
Experiments	—	✅ BehaviorSpace configs
📊 Results Summary
Version	Avg. Survival (ticks)	Lions Survive	Hyenas Survive
v0	~500	12%	89%
v1	~2500	67%	45%

🧩 Balanced survival achieved through safe zones and optimized energy management.

📚 Documentation
File	Description
TP1.pdf	Official assignment specification (Portuguese)
Relatorio.docx	10-page report with analysis and results
*.nlogo	Clean, well-documented NetLogo source code
👨‍🏫 Authors

Miguel Cardoso

João Pinto

📘 Course: Introduction to Artificial Intelligence
🏛️ Institution: ISEC – Instituto Superior de Engenharia de Coimbra
📅 Academic Year: 2023/2024

⚖️ License

🧩 Academic Use Only
This project is intended exclusively for educational and research purposes within the scope of ISEC’s AI coursework.
