# Reward Hacking Lab — 30-Minute Facilitator Guide

**Part of the StormClouds "Reward Hacking Lab" workshop kit.**
Pairs with the interactive lab: `reward-hacking-lab-executive.html` (open in any
browser, zero install — run it in **Executive** mode for this session).

- **Version:** 2026-07-23 · draft 1
- **Audience:** executives, managers, product/ops leaders, L&D, AI-governance
- **Format:** one facilitator, one screen, 4–30 participants, ~30 minutes
- **No code required.** Nobody in the room needs to read or write software.
- **License:** free to teach and to run internally; a paid commercial license
  (public/paid workshops, courses, client engagements) carries a 7% royalty.
  Built on the Foundation Layer pattern **FO-089** (an instrument measures a
  *proxy*, never the thing itself — Goodhart's law).

---

## 1. The one idea (say it in a sentence)

> **When a measure becomes a target, it stops being a good measure.**
> A team can drive a metric to the ceiling and destroy the outcome the metric
> was supposed to stand for — at the same time, without anyone lying.

That's it. Everything below is in service of making a room *feel* that, not just
nod at it. (Per FO-088: people can read Goodhart's law in any strategy book and
still not act on it — they change behavior when they **watch it happen**.)

---

## 2. Learning objectives

By the end of the session, each participant can:

- **LO1 — Explain** in plain language why optimizing a metric can degrade the
  outcome it was meant to track (Goodhart's law / proxy metrics).
- **LO2 — Identify** at least one metric on their own team that is at risk of
  being gamed, and name what it is a *proxy for*.
- **LO3 — Propose** at least one safeguard (a counter-metric, a guardrail, or a
  governance change) that reduces that risk.

These three are the record you keep (see §9). Optional mapping: LO1 supports a
general **"AI literacy / risk awareness"** objective, e.g. the awareness that a
model optimizing a proxy reward can behave exactly like the demo. Treat the
regulatory mapping as a *bonus*, not the spine of the session — see §8.

---

## 3. Before the room (setup checklist)

- [ ] Laptop + projector/large screen. Test the display ratio.
- [ ] Open `reward-hacking-lab-executive.html` in a browser. Confirm it loads
      offline (it's a single self-contained file — no network needed).
- [ ] Switch the **Audience** toggle (top-right) to **Executive**. Leave the
      preset on **Naive KPI**.
- [ ] Have this guide open on a second device or printed.
- [ ] (Optional) Print the one-page participant handout (§7 exercise).
- [ ] Decide your room's *anchor example* in advance (see §6) so the "apply to
      your world" block doesn't start from a blank page.

---

## 4. Run sheet (30 minutes)

| Time | Block | You do | You say (script) |
|------|-------|--------|------------------|
| 0:00–0:03 | **Frame** | Title slide / lab on screen, Naive KPI. | "You've all heard *what gets measured gets managed*. Today we watch the other half of that sentence — the part nobody quotes." |
| 0:03–0:10 | **Demo: the metric wins** | Point at the rising line. Then reveal the second line. | "This top line is the KPI on our dashboard — target hit-rate. Look at it climb. Everyone's green, everyone's happy. Now — this second line is the thing the KPI was *for*: real value delivered. Watch what it does." (let the gap land in silence for a beat) |
| 0:10–0:15 | **The switch** | Drag the preset to **Governed KPI** (or the slider right). The second line recovers. | "I didn't change the team. I didn't change the market. I changed **one thing** — what we rewarded. Same people, better incentive, and the value comes back." |
| 0:15–0:22 | **It isn't a toy** | Walk the three real cases (§5), one at a time. | "This isn't a cute simulation. Here's the same shape, with real consequences." |
| 0:22–0:28 | **Apply to your world** | Run the exercise (§7). Capture 2–3 examples on a whiteboard/doc. | "Where does *our* dashboard reward the target over the outcome? Give me a metric and what it's secretly a proxy for." |
| 0:28–0:30 | **Close** | One commitment per person (or per table). Show the law line. | "One metric you'll go look at this week, and one guardrail you'd add. That's the whole ask." |

> **Pacing tip.** The single most important moment is 0:03–0:10 — the *silence*
> after the second line drops. Don't fill it. Let them see the two lines diverge
> before you explain anything.

---

## 5. The three cases (debrief scripts)

Keep each to ~90 seconds. The structure is always the same: **measured → wanted
→ the gap → the cost → the lesson.** These are illustrative framings of
well-documented failures, not a claim that a single metric caused each disaster.

### Therac-25 (medical radiation, 1985–87)
- **Measured:** a clean operational track record — "it has passed its checks and
  we've had no reported problems."
- **Wanted:** a machine that is actually safe.
- **The gap:** absence of *recorded* failures was treated as evidence of safety.
  Latent software race conditions (and removed hardware interlocks) meant the
  proxy said "fine" while the machine delivered massive radiation overdoses.
- **The cost:** patients were seriously injured and killed.
- **Lesson:** "no failures logged" is a proxy for "safe." When you optimize the
  proxy — trust the clean record, remove the redundant check — you can walk
  straight off the edge the metric can't see.

### Challenger (space shuttle, 1986)
- **Measured:** flights survived without catastrophe — a growing track record.
- **Wanted:** a design with sound safety margins.
- **The gap:** O-ring erosion had been observed on earlier flights. Because
  nothing had gone wrong *yet*, the risk was normalized into "acceptable." The
  metric (survived flights) kept climbing while the real margin shrank.
- **The cost:** the vehicle broke apart; seven crew died.
- **Lesson:** "it hasn't failed yet" is a proxy for "it's safe to fly." This is
  the normalization of deviance — the KPI is green right up to the moment it
  isn't.

### LTCM (hedge fund, 1998)
- **Measured / optimized:** expected (average) return, with very high leverage.
- **Wanted:** durable, risk-adjusted profit.
- **The gap:** the models leaned on historical averages and under-weighted tail
  risk and correlation-in-a-crisis. The average looked superb — the variance is
  what mattered.
- **The cost:** ~$4.6 billion lost in months; a Fed-coordinated rescue to
  contain the fallout.
- **Lesson:** optimize the average, ignore the variance, and the variance is
  exactly what ends you. A metric that hides its own downside is the most
  dangerous kind.

> **Bridge line back to the lab:** "Same shape as the demo — the tracked number
> stayed beautiful while the thing underneath rotted."

---

## 6. Choosing your room's anchor example

Pick one *before* the session so 0:22 doesn't stall. Match it to the audience:

- **Generic leadership / mixed room:** OKRs & KPIs. "Revenue booked" vs. revenue
  that *renews*. "Utilization" vs. work that's actually valuable.
- **Sales / RevOps:** "calls made" or "meetings booked" vs. qualified pipeline
  that closes. Reps optimize the activity metric; quality quietly drops.
- **Support / CX:** "tickets closed" or "average handle time" vs. issues actually
  resolved. Fast-close and re-open games the number, not the customer's problem.
- **AI adoption / data teams:** "% of workflows using the model" or a model's own
  reward proxy vs. real business outcome. This is the literal AI-literacy tie-in:
  a model that games its reward behaves *exactly* like this demo.
- **Engineering:** "test coverage %" or "story points" vs. shipped reliability.

---

## 7. The exercise (participant handout)

Give each person (or table) 3–4 minutes and these four lines:

1. **A metric we track:** ____________________
2. **What it's really a proxy for (the outcome we want):** ____________________
3. **How someone could hit the number *without* delivering the outcome:**
   ____________________
4. **One counter-metric or guardrail that would catch that:** ____________________

Harvest 2–3 aloud. The gold is line 3 — when someone laughs because they
recognize it, the lesson has landed. Line 4 is the takeaway they leave with.

---

## 8. Documentation & evidence (the part that makes it "training," not a video)

This is what a compliance-minded buyer is actually paying for. After the session,
keep a short record — it converts "we watched a fun demo" into a defensible
learning event.

**Session record template:**
- Date, facilitator, location/remote, duration.
- Attendees (names or headcount).
- Learning objectives covered: LO1 / LO2 / LO3 (§2).
- Artifacts produced: the whiteboard list of at-risk metrics + each
  participant's completed handout (§7) = evidence of LO2 and LO3.
- One-line participant reflection collected: *"one metric on my team at risk +
  one safeguard I'd add."*

**On regulatory framing — read this carefully.** You *can* map this session to a
general "AI literacy / risk awareness" training objective (e.g. EU AI Act Art. 4
duties around staff understanding of AI risks). **Do not build the whole pitch on
that.** The regulatory wind is not settled — proposals to soften those duties have
been floated — so anchor the value where it's durable: **metric governance and
Goodhart's law are permanent management problems, wider than AI and older than any
regulation.** The AI angle is today's *marketing*; "your metrics can be gamed" is
the *product*.

---

## 9. Disclaimers (say these out loud)

Read or paraphrase these during the demo — they prevent the two failure modes
that reviewers flagged ("you're simulating real AI" and "this predicts my team"):

- "This is a **metaphor**, not a model of any specific AI system or of your team."
- "The simulation illustrates a **principle** (Goodhart's law). It does **not
  predict** anyone's behavior or any model's output."
- "The numbers are **illustrative**, drawn from the tool's own runs — they are not
  a benchmark or a measurement of your organization."

---

## 10. Timing variants

- **Lightning (10–15 min):** Frame + demo + the switch + one case (Challenger) +
  a single show-of-hands "where's your gamed metric?" Skip the handout.
- **Standard (30 min):** this guide as written.
- **Workshop (60–75 min):** add a 20-minute breakout — tables complete the §7
  handout for 2–3 real metrics, then present. Facilitator clusters them into
  patterns (activity-vs-outcome, average-vs-variance, record-vs-reality).

---

## 11. Objections & answers (facilitator prep)

- **"Isn't this obvious?"** — "The law is. Acting on it isn't. Name one metric on
  your own dashboard you'd bet *can't* be gamed. That pause is the point."
- **"Are you saying metrics are bad?"** — "No — unmeasured is worse. The move is a
  *counter-metric*: pair every target with the thing it could quietly destroy."
- **"Does this model our AI?"** — "No. It's a metaphor for a mechanism. But it's a
  faithful one: an AI optimizing a proxy reward gets gamed the same way, which is
  why this is used in AI-literacy sessions."
- **"How is this different from just 'have good KPIs'?"** — "Good KPIs still get
  gamed under enough pressure. The safeguard is structural — counter-metrics and
  governance — not just picking a smarter number."

---

## 12. Attribution

Reward Hacking Lab is a StormClouds product. The underlying pattern is
**FO-089 · INSTRUMENT_MEASURES_PROXY** from the author's Foundation Layer;
the "you only get it when you watch it" premise is **FO-088**. Real cases are
drawn from public record and framed for teaching. Free to teach and run
internally; paid/commercial delivery carries a 7% royalty (see repository
`LICENSE`).
