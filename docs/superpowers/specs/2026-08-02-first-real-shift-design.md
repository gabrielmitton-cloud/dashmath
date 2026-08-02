# First real shift — Mon Aug 3, 2026

Written Sun Aug 2, the night before. No real driver has used Mile Money on a
real shift. Every feature in it is a guess.

## What shipped tonight (a501e18)

**The memorized rule was wrong by more than a factor of two.** The rule of
thumb was computed per *driven* mile and displayed with no qualifier; the
decline chart is keyed to the miles the offer screen shows. Same tab, two
conventions, no label. A driver reading "$1.35 a mile" against a 5-mile $9
offer would accept it; the chart said that trip needed $14.20.

The fix is not a doubling. No flat $/mile can match the chart, because every
order costs ~8 fixed minutes before any driving happens — the required rate
runs $5.19/mile at 1 mile down to $2.55 at 10. So the rule now has the chart's
shape: a base plus a per-mile, derived from `rawMinutes()` so the two cannot
drift apart again. Both pieces round up, so the rule never accepts what the
chart declines.

**"Send today to Gabriel"** — plain-text export of the day: settings, pace,
shift, and every logged offer with what the app predicted next to what actually
happened. Text, not an encoded URL: no length limit, readable in a text
message, fails visibly. The backup link only ever carried lifetime totals,
which cannot answer whether the app was any use.

Nothing else changed. Tab order, Instacart mode, and the busy/dead idea were
all deliberately left alone — changing them would answer the question before
the shift could.

## Tomorrow

- **Clear his old `dm-settings` first.** He used an earlier version. Old state
  means he skips first-run setup and the onboarding never gets observed.
- **Open it once before he starts, leave the tab open.** No service worker; a
  dead zone with the page unloaded means no app.
- **Text him once, mid-shift: "how many offers have you gotten so far?"**
  That is the denominator. The export gives offers *logged*; only he can give
  offers *received*. Logged-vs-received decides everything below. By Tuesday
  he will not remember.
- **Do not ask "did you like it?"** He is family; he will say yes. Ask "show me
  the last offer you got — what did you do?"
- **If he stops opening it after the first hour, that is the finding.**

## The fork

Recorded in advance. My bet is B or C, not A.

**A — he logged most offers.** The calculator works in the moment. Next:
busy/dead multiplier (the app has no concept of opportunity cost, and a driver
idle 60% of a dead night earns more taking $0.90/mile than declining it), then
"where does it drop you."

**B — he logged a handful, then stopped.** The chart is the product. Make it
the front door, demote the calculator to a setup step, cut the tracker half.

**C — he never reopened it after setup.** The app failed as an app; the
artifact is the product — the chart printed or saved to photos, on the
passenger seat.

## Facebook group

Do not post the chart image: it renders `MILE MONEY` and the Pages URL, which
reads as self-promotion and gets removed. Post the numbers as text, as a driver
asking to be corrected. Tests four things for free: is the number sane for a
real market, do drivers think in shown or driven miles, do they use base+per-mile
or flat $/mile, and what do they say the real dealbreaker is.

**Caveat on my own change:** the folk rule is flat — "$2 a mile." Base+per-mile
is more correct and harder to remember. A rule nobody retains is worth less
than a rougher one they do. If the group comes back overwhelmingly flat, quote
the rule at a typical distance instead and let the chart carry the precision.
