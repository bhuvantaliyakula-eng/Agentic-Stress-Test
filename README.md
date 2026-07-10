# Lyzr Agent Ascending Block Memory Experiment

A performance experiment testing how well Lyzr Studio AI agents retain critical information as prompts grow progressively longer and more complex. Compares memory retention across different underlying models.

---

## Background

Built as part of an internship at Lyzr, this experiment explores how prompt length and noise volume affect an agent's ability to focus on and recall key information. The test uses a simulated inventory management scenario — an AI agent acting as a **Reorder Planner** for a product called GIZMO-003 — as a consistent, gradeable benchmark.

The agent is given this information at the start of every prompt:
- SKU: GIZMO-003
- Current stock: 0
- Average order size: 13.3 units
- Max order size: 20 units
- Order frequency: irregular, large spikes

---

## How It Works

Each round sends one large prompt to the agent containing three sections:

1. **GIZMO-003 order details** — always at the top
2. **N unrelated inventory questions** — grows by 1 every round
3. **One recall check question** — always at the bottom

Round 1 has 1 noise question in the middle. Round 2 has 2. By Round 500 the agent is receiving a single prompt with 500 unrelated questions buried between the key information and the recall check.

All rounds share the same session so the agent builds conversation memory across rounds. The recall question cycles through 5 fixed questions in order.

---

## Grading System

Every recall response is automatically scored out of 4:

| Criteria | What it checks |
|---|---|
| `mentioned_sku` | Did the response mention GIZMO-003 by name? |
| `mentioned_facts` | Did it reference specific numbers (13.3 avg, 20 max)? |
| `mentioned_pattern` | Did it describe demand as irregular or spiky? |
| `reasonable_qty` | Did it suggest a restock quantity between 10-25 units? |

Each yes = 1 point. Score of 4 = perfect recall. Score of 0 = complete failure.

---



---

*Internship project — Lyzr, 2026*
