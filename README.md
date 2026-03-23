# 🚴 Claude Cycling Coach Skill

A Claude skill that generates personalized, periodized training plans for road cycling, mountain biking, gravel, XCO, enduro, and cyclocross. Plans are power-based, phase-structured, and rendered as interactive HTML — output quality rivals TrainingPeaks coaching plans.

---

## Installation

### 1. Add the skill file

Save `cycling-coach.skill` then navigate in the side-bar of either claude desktop or claude web-app then: 

`--> Customize --> Skills --> tap the plus symbol --> Upload new skill`

Then upload the skill file you just downloaded. That's it! 

## Usage

Start a conversation with Claude and ask for a training plan. The skill triggers automatically on keywords like **FTP**, **power zones**, **MTB**, **gran fondo**, **enduro**, **XCO**, **gravel**, or any request for a bike training plan. An example prompt could be:

```
Help me create a training plan for the Paluma Push MTB race 18th July 2026 using the 
/cycling-coach skill
```

---

## Data Input Options

### Option A — Strava Integration (recommended)

Claude walks you through a one-time OAuth flow to pull your ride history:

```bash
npx claude-coach auth --client-id=YOUR_ID --client-secret=YOUR_SECRET
npx claude-coach sync --days=730
```

Once synced, Claude queries your actual training data to build a calibrated assessment.

### Option B — Manual Entry

No Strava? No problem. Claude collects what it needs through conversation:

- Weekly hours and longest recent rides
- FTP (watts) and any peak power numbers you know
- Target event, terrain access, and equipment
- For MTB: trail skill level and bike type

---

## Output

Claude generates two files:

| File | Purpose |
|---|---|
| `plan.json` | Full structured plan — weeks, workouts, phases, race strategy |
| `plan.html` | Interactive visual plan — open in any browser |

```bash
# Render JSON to HTML manually if needed
npx claude-coach render plan.json --output plan.html
```

---

## Supported Disciplines

| Discipline | Notes |
|---|---|
| Road cycling | Sweet spot and threshold focus, race calendar periodization |
| Gravel | Extended Zone 2 blocks, fueling practice, handling days |
| XCO mountain bike | VO2max intervals + technical skills curriculum |
| Enduro / All-Mountain | Anaerobic stage efforts + liaison climbing fitness |
| Cyclocross | High-intensity peak phase, running fitness, dismount skills |

---

## How It Works

1. **Assessment** — Claude analyses your training history or gathers data manually
2. **Zones** — Power and HR zones derived from your FTP or field test results
3. **Periodization** — Base → Build → Peak → Taper phases structured around your event date
4. **Workouts** — Each session includes duration, zone targets, and human-readable instructions
5. **Validation** — Claude presents its assessment for your confirmation before writing the plan
6. **Race strategy** — Pacing, nutrition, and taper guidance included for the target event

---

- A 20-minute FTP test is recommended in week 1–2 if you don't know your current FTP
- MTB plans include a technical skills curriculum alongside fitness sessions
- Plans err conservative with manual data — it's easier to add load than dig out of a hole
