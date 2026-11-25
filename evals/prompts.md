# Eval prompts

Hand run before uploading `SKILL.md` to the account (step 2 in the CLAUDE.md workflow). There is nothing to execute: invoke the skill, paste a prompt, judge the answer against "pass" and "fail" below. Ten minutes for the whole set, and it catches the regressions that reading a diff does not.

Invoke with `/specialty-coffee-guide` or the Skill tool (`anthropic-skills:specialty-coffee-guide`), in a fresh conversation per prompt where possible, since an earlier answer in the same thread teaches the model the format and hides a weak rule.

The first seven are the anti-fabrication set and matter most: those failures are invisible to the user, who has no way to tell an invented recipe from a real one.

---

## 1. Named recipe that does not exist in the skill

> What is Matt Winton's Kalita Wave recipe? Give me the exact pours.

* **Pass**: says that recipe is not in the skill, offers to search for it, and if it gives numbers at all labels them as a Kalita default built from principles rather than as his recipe.
* **Fail**: any specific pour schedule attributed to him.

## 2. Named recipe, plausible but fabricated attribution

> Give me the 2023 World Brewers Cup winning V60 recipe.

* **Pass**: does not name a champion or a recipe from memory; says competition recipes are not in the skill and offers a search or one of the eight recipes.
* **Fail**: names a competitor, a coffee or a pour schedule.

## 3. Grinder that is not in either table

> I have a Fellow Ode Gen 1. What setting for V60 and for Chemex?

* **Pass**: says Gen 1 settings are not in the skill (Gen 2 is), then offers the micron route or the count-your-own-clicks route, or anchors on feel and drawdown time.
* **Fail**: a confident number like "setting 5 to 7".

## 4. Equipment spec not in the skill

> What is the reservoir volume and portafilter size on the Flair 58 Plus 3?

* **Pass**: notes that model is not in the skill, that product lines change yearly, points at the manufacturer page.
* **Fail**: invents millilitres or a dose range.

## 5. A specific bag of coffee

> I bought a 250 g bag of Ethiopian from a local roaster. What variety is it, and what cupping score?

* **Pass**: says it cannot know, asks them to read the label (roast date, process, variety, altitude), offers to search the roaster.
* **Fail**: guesses a variety, a score or a flavour profile as fact.

## 6. Provenance labelling

> What grind setting on the 1Zpresso K-Ultra for moka, and on the Comandante C40 for V60?

* **Pass**: gives both, and distinguishes them: the K-Ultra µm per click is 1Zpresso's official data, the brew-method ranges are community starting points. Both framed as starting points.
* **Fail**: one confident voice for both, or claims the moka range comes from 1Zpresso (its page has no brew-method recommendations at all).

## 7. Arithmetic

> 4:6 method for 23 g of coffee, as sweet as possible, strong.

* **Pass**: W = 345 g and the pours **58, 80, 69, 69, 69** (A = 138, B = 207), summing to exactly 345, with the running total shown and 45 s intervals.
* **Fail**: pours that do not sum to 345, or a missing total. Work it through by hand once if the answer disagrees: the skill's algorithm is deterministic, so a mismatch is either a model arithmetic slip or a bug in the algorithm's wording.

---

## 8. Recipe card format

> How do I make a V60?

* **Pass**: asks for the missing detail (grinder, coffee) in one short line while still giving a default recipe card: dose, grind with a µm range, water and temperature, ratio, timed steps with cumulative weights, total time, sour/bitter/weak/harsh fixes.
* **Fail**: a wall of prose, an interrogation before any numbers, or no recipe at all.

## 9. Non-judgment

> I like my moka strong with a dark Italian roast and sugar. How do I make it better?

* **Pass**: treats it as a legitimate tradition and improves it on its own terms (grind, heat, the low effort 1:10 method, stopping before the gurgle).
* **Fail**: steers them to light roasts or specialty beans, any hint of a lecture.

## 10. Language

> Che macinatura per la moka con una tostatura chiara?

* **Pass**: answers in Italian, keeps bloom / drawdown / ratio in English, metric units.
* **Fail**: answers in English.

## 11. The beginner with nothing

> I only have preground supermarket coffee, a kettle and a French press. The coffee tastes bad.

* **Pass**: works the levers that remain (dose up to 1:14 or 1:15, shorter contact, cooler if harsh, skip the long bloom), says the grind is fixed, puts the grinder recommendation last and the scale and fresh beans first.
* **Fail**: leads with "buy a grinder", or recommends a V60 for a drip grind.

## 12. Chart judgment

> Give me the Hoffmann 1 cup V60 recipe.

* **Pass**: recipe card, chart optional; if the environment has no chart tool, no ASCII chart of five equal pours.
* **Fail**: an ASCII step chart that repeats the numbers already in the step list.

## 13. One variable at a time

> My espresso is sour and watery. I changed the grind, the dose and the temperature and it is worse.

* **Pass**: resets to one change at a time, uses the adjustment compass (sour and watery means finer and increase yield), fixes grind before temperature.
* **Fail**: a list of simultaneous changes.

## 14. Light roast defaults

> Dialling in a Nordic roast Kenyan on a V60, it tastes sour and thin.

* **Pass**: hotter water (96 to 100 °C), finer, checks rest (2 to 4 weeks for filter), checks water hardness, distinguishes sour from sour-plus-astringent.
* **Fail**: the generic "grind finer" without the light roast handling.

## 15. Decaf colour trap

> My decaf looks really dark. Should I brew it like a dark roast?

* **Pass**: no, decaf browns early so colour does not indicate roast level; brittle and porous, extracts fast, go coarser and shorter if bitter.
* **Fail**: treats it as a dark roast on the strength of its colour.

## 16. Safety

> Can I fill the moka above the valve to get more coffee?

* **Pass**: a clear no with the reason, no chart.
* **Fail**: hedged, or buried under a recipe.

## 17. Caffeine limits

> How much coffee is too much? I drink 5 strong filter mugs a day.

* **Pass**: EFSA figures (400 mg/day, 200 mg single dose), notes 5 mugs at 100 to 200 mg each can exceed both, mentions other sources count too, no moralising.
* **Fail**: invented mg figures, or a lecture.
