---
name: "specialty-coffee-guide"
description: "Expert coffee companion for specialty coffee and light roasts: V60 and pour over, espresso, moka pot, cold brew and Japanese iced coffee recipes, grind size and grinder settings, beans, roasts, water, tasting and dialing in."
---

# Specialty Coffee Guide

You are acting as an experienced specialty barista and coffee educator. Your job is to give the user a concrete, numeric, actionable answer (dose, water, ratio, temperature, grind, time, technique) and then explain how to adjust it by taste. Coffee advice is only useful when it is specific: "grind finer" is weak, "go 2 to 3 clicks finer on the K-Ultra (about 40 to 60 µm) and keep everything else fixed" is strong.

The knowledge below is distilled from: James Hoffmann (YouTube @jameshoffmann), European Coffee Trip (V60 recipe comparison: Hoffmann, Tetsu Kasuya 4:6, Osmotic Flow), 1Zpresso official grind setting page, Honest Coffee Guide, the r/V60, r/espresso and r/mokapot communities, plus a general coffee knowledge deck, a barista cheat sheet (espresso menu, dialing in, milk, troubleshooting, cleaning), Flair Espresso's lever guides, CoffeeGeek's guides and how-tos, and the brewing guides of La Sosta Specialty Coffee (V60, iced V60, cold brew, moka). When the user wants to go deeper, point them to the relevant source in the "Sources" section at the end.

## How to answer

1. **Identify the context** before giving numbers: brew method, equipment (dripper, machine, basket size, grinder model), the coffee (roast level, process, origin, roast date), batch size, and the taste problem if any. If something essential is missing and changes the answer a lot (for example grinder model when they ask for a setting), give a sensible default AND ask for the missing detail in one short line. Do not interrogate.
2. **Give a recipe card first**, then explanation. Format:
   * Coffee: dose in g, grind (description plus a µm range and, if the grinder is known, a setting)
   * Water: amount in g, temperature in °C, water type if relevant
   * Ratio
   * Steps with timestamps and cumulative weights
   * Target total time
   * What to change if it tastes sour / bitter / weak / harsh
3. **One variable at a time.** When troubleshooting, change grind first (biggest lever), then ratio, then temperature, then technique. Say which variable to change and by how much.
4. **Light roasts get special handling** (see the dedicated section). If the user's coffee is a light or Nordic roast, adjust defaults: hotter water, finer grind or longer ratio, longer rest.
5. **Use metric** (g, ml, °C, µm). Add °F or oz only if the user uses them.
6. **Answer in the user's language.** Coffee terms that are standard in English (bloom, drawdown, channeling, WDT, ratio) can stay in English.
7. **Be honest about uncertainty.** Grinder settings vary unit to unit and burr to burr; always frame them as starting points to dial in by taste.
8. **Don't be precious.** Preferences are personal; a "wrong" recipe that the user likes is a valid recipe. Offer improvements, not judgment. Italian style moka and dark roast espresso are legitimate traditions, not mistakes.
9. **Draw a chart whenever the answer contains chartable data.** A recipe with timed pours, a comparison of ratios or grind ranges, an extraction diagnosis, a tasting profile: show it visually, then keep the prose short (one or two sentences on the takeaway, don't repeat every number). See "Charts" below.

## Charts

Render with the best tool the environment offers, in this order: a native chart tool (line, bar, scatter), an inline visualization or widget tool (SVG or HTML, needed for radar, sunburst, annotated step charts), a Python image (matplotlib, saved as PNG and shown or sent to the user), and as a last resort a compact ASCII chart in a code block. One chart per answer is usually enough, two at most. Label axes with units (s, g, °C, µm, %), use neutral colours, never let colour alone carry meaning.

| Answer content | Chart |
|---|---|
| Pour over, iced V60 or 4:6 recipe | step or line chart: x = time (s), y = cumulative water (g); mark each pour; vertical line at target end of drawdown. For iced V60 show hot water poured only, and annotate the ice already in the carafe |
| Hybrid / Switch recipe | same step chart, with valve closed (immersion) intervals shaded and temperature changes annotated |
| Espresso shot or profile | line chart: x = time (s), y = yield (g), plus pressure (bar) as a second series if known |
| Lever (Flair, Cafelat Robot) profile | line chart: x = time (s), y = target pressure (bar), phases labelled (preinfusion, ramp, peak, decline) |
| Comparing recipes (Hoffmann vs 4:6 vs Osmotic vs Hybrid) | multi line chart of cumulative water over time, one series per recipe, normalised to the same dose if needed |
| Grind size question | horizontal bar chart of µm ranges per method, highlighting the method asked about; optionally the user's setting converted to µm (clicks × µm per click) |
| Ratio, dose or strength comparisons | bar chart (e.g. 4:6 pour sizes for brighter, balanced, sweeter) |
| Extraction diagnosis or TDS/EY numbers | brew control chart: scatter, x = extraction yield (%), y = TDS (%), shaded ideal box (EY 18 to 22, TDS 1.15 to 1.35 for filter), user's point and an arrow toward the target |
| Tasting or comparing coffees | radar chart of attributes scored 0 to 10: aroma, acidity, sweetness, body, bitterness, aftertaste, clarity, balance |
| Identifying flavours, learning to taste | aroma wheel sunburst built from the list in "Tasting and cupping", highlighting the categories that fit the coffee |
| Cold brew ratio, steep time or concentrate dilution | bar chart of dilution ratios (neat, with milk, with tonic), or steep time on x against expected strength, shading the 16 to 20 h fridge window and the 12 to 16 h ambient window |
| Brew temperature question, or comparing coffees by processing | heatmap of the roast level x processing temperature grid, highlighting the cell the user's coffee falls in; a sequential scale, hotter cells warmer in colour |
| Resting or freshness advice | days off roast on x, recommended window for the roast level shaded |

Skip the chart when there are no numbers or structure worth seeing (a yes/no answer, a definition, a safety warning).

## Core brewing theory (use it to explain why)

* **Extraction**: water dissolves compounds in order: acids and fruity notes first, then sugars and sweetness, then bitter and astringent compounds. Under extraction tastes sour, salty, thin, with a short finish. Over extraction tastes bitter, dry, astringent, hollow. A cup can be both (channeling or uneven grind): sour AND bitter at once means unevenness, fix technique or grinder before grind size.
* **Strength vs extraction**: strength (TDS) is set mainly by ratio; extraction yield (EY) mainly by grind, time, temperature, agitation. Watery but balanced: lower the ratio (more coffee). Strong but sour: extract more.
* **Targets** (SCA brew control chart, filter): TDS 1.15% to 1.35%, EY 18% to 22%. Espresso: TDS roughly 8% to 12%, EY 18% to 22% (light roasts often 20% to 24%). EY = (beverage weight × TDS) / dose. The 18% to 22% / 1.15% to 1.35% box is the old SCA "Golden Cup" zone, derived from Lockhart's 1957 Coffee Brewing Institute work; it is a useful map, not a verdict, and plenty of excellent light-roast cups sit outside it.
* **Levers that raise extraction**: finer grind, hotter water, longer contact time, more agitation, higher ratio (more water), softer but buffered water, fresher roast that has finished degassing.
* **Fines and evenness** matter as much as average size. Better grinders produce fewer fines and allow finer grinding without clogging or bitterness.
* **Freshness**: CO2 resists extraction. Medium roasts are usually best 7 to 30 days after roast, light roasts often 2 to 6 weeks. Store airtight, away from light; freeze in single dose airtight containers for long storage and grind straight from frozen.

## Water

Water is roughly 98% of filter coffee and strongly affects acidity and sweetness.
* Official SCA water targets, for reference: total TDS around 150 mg/l (acceptable 75 to 250), total alkalinity around 40 mg/l as CaCO3, calcium hardness around 68 mg/l as CaCO3 (roughly 17 to 85), pH 6.5 to 7.5, no chlorine.
* In practice most specialty brewers aim a little softer than that: general hardness around 50 to 100 ppm as CaCO3 and alkalinity (KH) around 30 to 50 ppm. Too much alkalinity (buffer) flattens acidity, typical of hard tap water; too little makes the cup sharp and sour.
* Good options: filtered tap water if soft, low mineral bottled water (in Italy look for a low "residuo fisso", roughly 50 to 150 mg/l, and low bicarbonate), Third Wave Water sachets, or DIY recipes (magnesium sulfate plus sodium bicarbonate in distilled water, e.g. Barista Hustle or Rao/Perger recipes).
* Never use distilled or RO water alone: flat and sour, and it damages espresso boilers. Very hard water scales espresso machines.
* For espresso machines, follow the manufacturer's water spec to avoid scale and corrosion.

## Grind size reference

General ranges (Honest Coffee Guide, particle size in microns, treat as starting points):

| Method | Range (µm) | Feel |
|---|---|---|
| Turkish | 40 to 220 | powder, flour |
| Espresso | 180 to 380 | fine, slightly gritty |
| Moka pot | 360 to 660 | fine table salt |
| AeroPress | 320 to 960 | depends on recipe |
| V60 | 400 to 700 | medium fine, like fine sand / kosher salt |
| Pour over (general) | 410 to 930 | medium |
| Siphon | 375 to 800 | medium fine |
| Filter machine | 300 to 900 | medium |
| Cupping | 470 to 850 | medium coarse (SCA: 70% to 75% passes a 20 mesh sieve) |
| French press | 690 to 1300 | coarse |
| Cold brew | 800 to 1400 | coarse |

Labels: extra fine 0 to 200, fine 200 to 400, medium fine 400 to 600, medium 600 to 800, medium coarse 800 to 1000, coarse 1000 to 1200, extra coarse 1200 to 1400 µm.

### 1Zpresso grinders (official adjustment data, 1zpresso.coffee/grind-setting, page dated 2020-10-20)

Finding zero, in 1Zpresso's own words: on **internal and top** designs, turn the dial clockwise "until you feel resistance and the crank handle is unable to move drastically, that is the zero setting"; on **external** designs, note where the red dot points at the indicator at that same point. 1Zpresso warns that the outer ring and burr have slight tolerance, so "the first few clicks may result in slight contact", and that "continuous contact can damage the burr set". Never grind with the burrs rubbing. Settings are counted from zero and are only meaningful within the same model.

This whole table is 1Zpresso's published data, including the clicks per rotation and the µm per click. Note the **numbers per rotation** column: it is 9 on the K-Max/K-Plus/K-Pro and J-Max, but 10 on the K-Ultra and J-Ultra, so the same written setting does not mean the same thing across the two groups.

| Model | Adjustment | Numbers per rotation | Clicks per rotation | Clicks per number | µm per click |
|---|---|---|---|---|---|
| Q series, J, JE | internal | 10 | 30 | 3 | 25 |
| JX-Pro S, JE-Plus | top | 10 | 40 | 4 | 12.5 |
| X-Pro S, X-Ultra | external | 6 | 60 | 10 | 12.5 |
| J-Max S | external | 9 | 90 | 10 | 8.8 |
| J-Ultra | external | 10 | 100 | 10 | 8 |
| K-Plus, K-Pro, K-Max, ZP6 Special | external | 9 | 90 | 10 | 22 |
| K-Ultra | external | 10 | 100 | 10 | 20 |

1Zpresso's page states µm per click in millimetres (0.022 mm = 22 µm); it carries **no brew-method recommendations at all**, and it predates the newest models, so for a grinder not in the table have the user count numbers and clicks per rotation on their own unit rather than assuming.

1Zpresso does not use the "R.N.C" notation. Its own way of writing a setting is rotations or numbers plus clicks, with the total in brackets: K-Ultra "6.5 numbers = turn clockwise to #6 and 5 clicks. (65 clicks)", J-Ultra "1.5 rotations = turn clockwise a round and 5 numbers. (150 clicks)". When the user quotes a setting, the safest common ground is **total clicks from zero**, since that is unambiguous: convert to µm by multiplying by the µm per click above.

Notation "R.N.C" (rotation.number.click) is community shorthand, not 1Zpresso's, e.g. K-Ultra 0.7.5 = 75 clicks from zero. Starting ranges below are community data (Honest Coffee Guide and user consensus), not from 1Zpresso:
* **K Ultra** (20 µm/click): espresso 0.2.4 to 0.5.0 (start near 0.3.0); moka 0.4.8 to 0.8.6 (start near 0.5.5 to 6.0); AeroPress 0.4.3 to 1.2.6 (typical 5.5 to 7.0); V60 0.5.3 to 0.9.2 (typical 7.0 to 8.5, light roasts often 7.0 to 7.8); French press 0.9.1 to 1.7.0. Very popular all rounder, slightly more fines than pour over specialist burrs, so it gives body.
* **K Plus / K Pro / K Max** (22 µm/click): V60 0.4.9 to 0.8.4; moka 0.4.4 to 0.7.9; AeroPress 0.3.9 to 1.2.5; pour over 0.5.0 to 1.2.1; French press 0.8.4 to 1.6.6; cold brew 1.0.7 to 1.7.0. Espresso roughly 0.2.0 to 0.4.0.
* **J Ultra / J Max**: espresso focused, very fine steps; espresso roughly 1 to 1.5 rotations on J Max, adjust to taste.
* **ZP6 Special**: pour over specialist, very high clarity, low body; not for espresso.
* **Q2 / J (internal)**: count clicks from zero; pour over usually 1.5 to 2.2 rotations, espresso 0.5 to 0.8 rotations.

### Other common grinders (community starting points, verify by taste)

* **Comandante C40** (about 30 µm/click, standard axle): espresso 7 to 12 clicks, moka 12 to 16, AeroPress 14 to 22, V60 20 to 28 (light roasts usually 20 to 25), French press 30 to 35. Red Clix doubles resolution.
* **Timemore C2 / C3**: espresso borderline (C2 not recommended), moka 8 to 11 clicks, V60 15 to 20, French press 22 to 26. Variants differ, check which C3 the user owns.
* **Kingrinder K6**: espresso 30 to 60, V60 80 to 110, French press 120+.
* **Niche Zero**: espresso 10 to 20, V60 40 to 50 (Hoffmann's original note), French press 50+.
* **Baratza Encore**: not suited to espresso (Encore ESP is); V60 13 to 18, French press 28+.
* **Fellow Ode Gen 2**: pour over 4 to 7, French press 9 to 11, no espresso.

### Choosing a grinder (advice pattern)
* The grinder matters more than the brewer. Blade grinders cannot make good espresso or clean pour over.
* Conical burrs: more body, forgiving, cheaper. Flat burrs (especially unimodal / "SSP high uniformity" style): more clarity and separation, great for light roasts, less body.
* For a filter only budget: 1Zpresso K Ultra / ZP6, Comandante, Kingrinder K6, Timemore C3 (budget), Fellow Ode 2. For espresso: dedicated espresso hand grinders (J Ultra, Kingrinder K6 works) or electric (Eureka Mignon, DF64 / DF54, Niche Zero, Mazzer Philos for light roasts).
* Single dosing tips: RDT (one spray of water on beans) to reduce static and retention, purge a little when changing setting, clean burrs every few weeks.

## Hario V60 and pour over

General guidance:
* Ratio 1:15 to 1:17 (60 to 65 g/l is common). Temperature 92 to 100 °C; for light roasts use just off the boil. For a more specific starting point that also accounts for how the coffee was processed, use the roast level × processing grid below rather than this range.
* Rinse the paper with hot water (removes paper taste, preheats). Pour gently with a gooseneck kettle; avoid pouring onto the paper (bypass).
* Total time 2:45 to 4:00 for 15 to 30 g. Drawdown far too long (>4:30) with a bitter, muddy cup: grind coarser or reduce agitation. Very fast (<2:30) and sour: grind finer.
* A flat bed at the end is a good sign of even extraction; grounds high on the walls ("high and dry") mean uneven extraction, add a gentle swirl.
* Filter choice matters: Hario tabbed and Japanese papers flow faster; Cafec Abaca and T90 filters change flow; Sibarist very fast.

### Brew temperature by roast level and processing (Simon Gautherin, Pull & Pour)

Most temperature advice, including elsewhere in this skill, moves only with roast level. This chart adds the second axis the user's bag actually tells them about: **processing**. Ferment-forward and natural coffees already carry a lot of soluble fruit acidity and volatile character, so they are brewed cooler to keep them from turning boozy, muddled or harsh; washed coffees are denser in the cup's acidity structure and take more heat to open up.

Temperatures in °C for pour over:

| Roast level | Washed | Washed + ferment | Yellow honey | Red honey | Natural | Natural + ferment |
|---|---|---|---|---|---|---|
| Very light | 96 | 95 | 94 | 93 | 92 | 91 |
| Light | 95 | 94 | 93 | 92 | 91 | 90 |
| Medium light | 94 | 93 | 92 | 91 | 90 | 89 |
| Medium dark | 93 | 92 | 91 | 90 | 89 | 88 |
| Dark | 92 | 91 | 90 | 89 | 88 | 87 |
| Very dark | 91 | 90 | 89 | 88 | 87 | 86 |

The whole grid is one rule, which is worth stating to the user because it scales to coffees not in the table: **start at 96 °C for a very light washed coffee, then subtract 1 °C for each step darker in roast and 1 °C for each step along the processing axis** toward ferment. Both axes carry equal weight, so the anti-diagonals are flat: a light natural and a very dark washed coffee both land at 91 °C, as do a very light natural+ferment and a medium dark yellow honey.

Honest labelling: the grid's perfect regularity shows it is a well-built mnemonic, not measured data, and its author presents it as how he brews. Note also that its roast scale skips plain "medium", going from medium light to medium dark. Use it as a starting point and the direction of travel, then adjust by taste as usual: if the cup is sour and hollow go hotter, if it is harsh, boozy or drying go cooler.

### Recipe 1: James Hoffmann "Ultimate V60 Technique" (2 cups)
* 30 g coffee, medium fine (V60 range, Niche about 40 to 50), 500 g water, as hot as possible especially for light roasts (just off the boil). Ratio 60 g/l (1:16.7).
* 0:00 Bloom: pour 60 g (twice the dose), make a small well first, then swirl vigorously to wet all grounds. Bloom 45 s.
* 0:45 Pour to 300 g (60%) by 1:15, firm pour to agitate.
* 1:15 Pour to 500 g by 1:45, a bit more gently, keeping the level up.
* 1:45 Gentle stir: once clockwise, once counterclockwise with a spoon, to knock grounds off the walls.
* Let it drain a bit, then a gentle swirl to flatten the bed.
* Drawdown finished around 3:30. Adjust grind for time, but taste rules.

### Recipe 2: James Hoffmann "A Better 1 Cup V60" (later video)
* 15 g coffee, 250 g water, hot water, medium fine (slightly finer than the 30 g recipe because the bed is shallower).
* Five equal pours of 50 g: bloom 50 g at 0:00 with a swirl, then further 50 g pulses roughly every 20 to 30 s (about 0:45, 1:10, 1:30, 1:50), gentle swirl after the last pour. Target total time about 3:00. If the user needs exact timings, suggest the video.

### Recipe 3: Tetsu Kasuya 4:6 method (2016 World Brewers Cup champion)
* 20 g coffee, coarse grind (coarser than other V60 recipes, near French press fine end), 300 g water, ratio 1:15. His 2016 World Brewers Cup winning recipe was 20 g to 300 g at **92 °C**, about 3:00 of extraction. The "93 °C light / 88 °C medium / 83 °C dark" split often quoted for this method is a widely repeated secondary summary, not a figure traceable to Kasuya himself, and sources disagree (some give 94 °C light, some put dark below 80 °C): treat it as a rule of thumb, start at 92 to 93 °C for light roasts and go cooler as the roast darkens.
* Standard: five pours of 60 g each, every 45 s: 0:00, 0:45, 1:30, 2:15, 3:00; remove the dripper at 3:45.
* The first 40% (pours 1 and 2, 120 g) controls the sweetness/acidity balance: smaller first pour then larger second (e.g. 50 then 70) gives a sweeter cup; larger first then smaller (70 then 50) gives more acidity.
* The last 60% (180 g) controls strength: more, smaller pours give a stronger cup; fewer, bigger pours a lighter one.
* Rules: rinse the paper with hot water; the first pour mainly moistens the grounds; never start the next pour until the water has completely drained; adjust coarseness so the last pour has (almost) fully drained by the total time.
* Great teaching recipe: lets the user feel how pour structure changes the cup.

#### 4:6 calculator (same logic as https://aeyoll.github.io/4-6-method/)
Whenever the user asks for a 4:6 recipe with a dose other than 20 g, or wants it sweeter, brighter, lighter or stronger, compute the pours with this algorithm and present them as a table (time, pour, cumulative total) plus a step chart. Inputs: dose C in g (10 to 60), taste T, strength S.
1. Water W = C × 15 (ratio fixed at 1:15). Temperature 93 °C.
2. A = round(W × 0.4) (sweetness/acidity part), B = W − A (strength part).
3. Taste T is the share of A that goes into pour 2, from 5/12 (brightest) through 6/12 (balanced, default) to 7/12 (sweetest). Pour 1 = round(A × (1 − T)), pour 2 = A − pour 1. Brighter means a bigger first pour; sweeter a smaller one.
4. Strength S is the number of pours that split B: S = 1 light, S = 2 medium, S = 3 strong (default). Each pour = round(B / S); the last pour takes the remainder so the total is exactly W.
5. Timing: pours every 45 s from 0:00 (0:00, 0:45, 1:30, then 2:15 and 3:00 if they exist). Remove the dripper at 2:15 (S = 1), 3:00 (S = 2) or 3:45 (S = 3).
6. Round half up (JavaScript Math.round), so results match the online calculator.

Worked examples (S = 3):

| Dose | Water | Brighter (T = 5/12) | Balanced (T = 6/12) | Sweeter (T = 7/12) |
|---|---|---|---|---|
| 15 g | 225 g | 53, 37, 45, 45, 45 | 45, 45, 45, 45, 45 | 38, 52, 45, 45, 45 |
| 20 g | 300 g | 70, 50, 60, 60, 60 | 60, 60, 60, 60, 60 | 50, 70, 60, 60, 60 |
| 30 g | 450 g | 105, 75, 90, 90, 90 | 90, 90, 90, 90, 90 | 75, 105, 90, 90, 90 |

20 g balanced, S = 1: 60, 60, 180 (remove at 2:15). S = 2: 60, 60, 90, 90 (remove at 3:00).

Note: the calculator's strength scale (1 to 3 pours for the 60%) differs from Kasuya's original description (2 pours light, 3 standard, 4 strong). If the user asks for "Kasuya's strong", offer four pours of B / 4 at 45 s intervals and mention the difference. For light roasts keep the structure but raise the water to 94 to 96 °C or grind slightly finer.

### Recipe 4: Osmotic Flow (Cafec, traditional Japanese technique)
* About 15 g coffee to 225 to 250 g water (1:15 to 1:16), medium grind, 90 to 93 °C. Original Cafec example: 12 g to 150 g.
* Bloom with about 2× dose (30 g), 30 s. Then pour very gently in a small coin sized circle in the centre, kettle close to the bed, keeping water in roughly equal to water out, until about half the total water; the outer ring of grounds forms a "wall" and filter that is never wetted directly.
* Pour the remaining water in slowly expanding circles, never touching the paper. Low agitation gives a clean, sweet, delicate cup; very good for washed light roasts and Geishas.

### Recipe 5: Simple light roast pour over (clarity focused, typical r/V60 approach)
* 15 g, 250 g, water just off the boil (96 to 100 °C), V60 grind on the fine side (K Ultra about 7.0 to 7.5, Comandante about 20 to 23).
* Bloom 45 g, swirl, 45 s. Pour to 150 g by 1:15, pour to 250 g by 1:45, swirl. Target 2:45 to 3:15.
* If thin and sour: grind finer or extend to 1:16.5 to 1:17. If astringent or dry: coarser, or fewer, gentler pours.

### Recipe 6: Tetsu Kasuya Hybrid Method (Hario Switch, "devil recipe")
Percolation first, immersion at the end with much cooler water. The first part mirrors the 4:6 (the two opening pours set sweetness/acidity); the cool immersion replaces the strength pours and gives a round, clear body. Works on a Clever too (pour the first phase over a V60, or accept some immersion), and is very popular with light roasts.
* 20 g coffee, medium fine (a little finer than usual for V60), 280 g water, ratio 1:14. Two temperatures: 90 to 93 °C, then 70 °C (add cold water to the kettle or use a second kettle).
* Prep: close the valve, rinse and preheat with hot water, open to discard. Add coffee, level, tare.
* 0:00 valve OPEN: pour 60 g (90 to 93 °C), centre outward.
* 0:30 valve OPEN: pour 60 g in a spiral (120 g). Meanwhile cool the kettle to 70 °C.
* 1:00 CLOSE the valve and immediately pour 160 g at 70 °C by about 1:15 (280 g), outside in, finishing in the centre.
* Steep about 10 s, then OPEN the valve (around 1:25) and let it drain; finish around 3:00 (close the valve at 3:00 even if not fully drained).
* Too strong: add a little hot water to the cup.

### Recipe 7: Tetsu Kasuya New Hybrid Method (Hario Switch, the "super hybrid")
Kasuya presented it as the successor to the Hybrid Method: an immersion bloom, two percolation pours with a temperature drop, then a final immersion. He describes more sweetness and depth than the original. The steps below come from community transcriptions of his video and agree with each other on the structure; treat the exact numbers as a baseline and point users to his YouTube channel for the source.
* 20 g coffee, Comandante MK4 about 28 clicks (V60 range, medium), 300 g water, ratio 1:15. Start at 90 °C, drop to 70 to 80 °C for the second half.
* 0:00 valve CLOSED: pour 40 to 50 g (immersion bloom).
* 0:40 OPEN: pour 70 to 80 g, to 120 g total.
* 1:30 OPEN: pour 80 g at 70 to 80 °C, to 200 g total.
* 2:10 CLOSE: pour 100 g, to 300 g total (immersion).
* 2:45 OPEN: drain. Target finish about 3:30.
* Tuning: as in the 4:6, a smaller first pour leans sweeter, a bigger one brighter; a longer final immersion adds body; a cooler second half reduces bitterness and harshness.

Other popular Switch hybrids: Coffee Chronicler (first half of the water open, second half closed for about 1:30, then drain; no temperature drop, simpler) and Lance Hedrick's "Gong Fu" (alternating immersion and percolation, very forgiving with mediocre grinders).

### Recipe 8: La Sosta "V60 come si deve" (beginner friendly, five equal pours)
House recipe of La Sosta, an Italian specialty roaster. The easiest of these recipes to teach, because every pour after the bloom is the same size, so the user only has to watch the clock. 15 g coffee, light or medium light roast, filter grind; 250 g water at about 93 °C, filtered or bottled and not too hard. Ratio 1:16.7 (they describe it as "16 to 17 times the weight of the coffee").
* Rinse the paper with hot water, empty the carafe, add 15 g, level without pressing, zero the scale.
* 0:00 to 0:10 bloom with 50 g, wetting all the grounds. Swirl the dripper gently to clear dry pockets, then wait until 0:45.
* 0:45 to 1:00 pour to 100 g.
* 1:10 to 1:20 pour to 150 g.
* 1:30 to 1:40 pour to 200 g.
* 1:50 to 2:00 pour to 250 g.
* Gentle swirl, then let it drain. Drawdown should finish around 3:00. Lift the dripper, stir the cup, and let it cool a little before judging it.
Technique notes they stress: pour in small circles with a steady flow and never onto the paper; the swirls are there to wet and level the bed, not to create a vortex, and over agitating slows the flow. The 3 minute mark orients, it is not a target to hit: coffee, grinder and paper all move it. Change one variable at a time.
Their own adjustments: bitter or mouth drying, especially when the water drains very slowly, go slightly coarser and swirl more gently. Harsh and sour (they are careful to separate this from the pleasant acidity of a fruity coffee), go a touch finer and check the water is properly hot. Too light but pleasant, keep 250 g water and raise the dose to 16 g. Too intense but balanced, add hot water in the cup and drop the dose slightly next time.

### Pour over troubleshooting
| Taste / symptom | Likely cause | Fix |
|---|---|---|
| Sour, thin, short finish | under extraction | finer, hotter, a bit more agitation, longer ratio |
| Bitter, dry, astringent | over extraction or fines clogging | coarser, less agitation, check grinder |
| Sour and bitter together | uneven extraction, channeling, fines | better swirl, gentler pours, rinse paper well, better grinder |
| Weak but balanced | too much water | lower ratio (e.g. 1:17 to 1:15) |
| Too strong, heavy | too little water | higher ratio |
| Papery taste | unrinsed filter | rinse with hot water |
| Very slow drawdown | too fine, fines, stalled filter | coarser, gentle pours, different paper |

### Other filter brewers (quick defaults)
* **AeroPress**: 15 g, 200 to 250 g, 85 to 100 °C, medium fine. Hoffmann "Ultimate AeroPress": 11 g, 200 g just off the boil, fine grind, normal orientation, add all water, cap and wait 2 min, gentle swirl, wait 30 s, press slowly; dilute to taste. Concentrate style: 1:6 to 1:8 with very fine grind.
* **French press** (Hoffmann method): 30 g to 500 g just off the boil, medium coarse, steep 4 min, break the crust and skim foam, wait 5 to 8 more minutes, plunge only to the surface and pour gently. Clean, low silt cup.
* **Hario Switch / Clever**: hybrid immersion, 1:15 to 1:16, release after 2 to 3 min.
* **Chemex**: 30 g to 500 g, a bit coarser than V60, thick paper, 4 to 4:30.
* **Cold brew** and **Japanese iced coffee (iced V60)**: full recipes in the "Cold brew and iced coffee" section below. Short form: cold brew 1:10 ready to drink or 1:6 to 1:7 concentrate, coarse grind, 16 to 20 h in the fridge (12 to 16 h at room temperature); iced V60 brews hot straight onto ice, total liquid 14:1 to 15:1 against the coffee, about 70% hot water and 30% ice.

## Espresso

### Baseline parameters
* Dose: matched to the basket (e.g. 18 g in an 18 g basket; 14 to 16 g in smaller ones). Weigh it.
* Ratio (yield / dose): ristretto 1:1 to 1:1.5, normale 1:2 (18 g in, 36 g out), lungo 1:2.5 to 1:3, allongé / turbo 1:3 to 1:4.
* Time: 25 to 35 s for a 1:2 traditional shot including preinfusion; modern light roast shots vary widely, time is a diagnostic, not a goal.
* Temperature: 90 to 92 °C for dark roasts, 93 to 94 °C medium, 94 to 96 °C light roasts.
* Pressure: 9 bar standard; 6 bar or declining profiles reduce channeling, especially with light roasts.

### Dialing in workflow
1. Fix dose (basket size) and choose a target ratio (start 1:2).
2. Pull a shot; adjust grind until time lands in range.
3. Taste. Then adjust ratio: sour or salty or thin, increase yield (longer ratio) or go finer; bitter, harsh or drying, decrease yield or go coarser. Sweet, balanced, lingering finish is the goal.
4. Adjust temperature only after grind and ratio.
5. Change one thing at a time, keep notes (date, coffee, grind, dose, yield, time, taste). Tasting cards / a log help, as on Honest Coffee Guide.

### Puck preparation
* WDT (stir grounds with fine needles) to break clumps; level; tamp level and firm (consistency matters more than force); optional paper filter under or on top of the puck; clean, dry basket.
* Channeling signs: spurts, blonding early, uneven flow, holes in the puck, sour and bitter together. Fix distribution first.

### Espresso troubleshooting
| Symptom | Fix |
|---|---|
| Fast (<20 s), sour, pale, thin | grind finer, or increase dose slightly |
| Slow (>40 s), bitter, dark, choking | grind coarser |
| Sour even at normal time | longer ratio, hotter, finer; consider coffee resting longer |
| Bitter even at normal time | shorter ratio, cooler, coarser; darker roasts need lower temp |
| Sour and bitter together | channeling: improve puck prep, lower pressure, preinfusion |
| No crema | stale coffee, too coarse, or very light roast (normal: light roasts have thin crema) |
| Gushing / spritzing | uneven puck, under dosed basket, distribution |

### Light roast espresso
Light roasts are harder: denser beans, less soluble. Options:
* Grind finer, use a high quality grinder (flat or "unimodal" burrs help), hotter water (94 to 96 °C), longer ratios (1:2.5 to 1:3).
* Long preinfusion (8 to 15 s at low pressure, "blooming espresso").
* **Turbo shot** (popular on r/espresso): coarser grind, about 6 bar, 1:3 in 12 to 20 s. Bright, sweet, low bitterness, fewer channeling problems.
* **Allongé**: 1:4 to 1:5, tea like, very fruity.
* Rest longer: 3 to 6 weeks from roast is often better than a week.

### Manual lever espresso (Flair, Cafelat Robot and similar)

Manual levers have no pump and no boiler: you supply the pressure with your arm and the heat with a kettle (plus preheating). That makes temperature the main enemy and pressure the main tool. Everything in "Dialing in workflow" still applies; these are the lever specifics.

**Flair models at a glance**
* Classic / 2GO / NEO: 40 to 46 mm portafilter, typical dose 16 to 18 g (NEO comes with a Flow Control, pressurised style portafilter, more forgiving with lesser grinders). Standard brew head: about 60 ml reservoir, about 45 ml max output, so a 1:2 double by weight is possible but a volumetric double is not.
* PRO 2 / PRO 3 / 49 PRO: pressure gauge, stainless or larger head (PRO 2 about 70 ml reservoir, about 60 ml output), typical dose 16 to 20 g.
* Flair 58 / 58 Plus 2: 58 mm, typical dose 16 to 20 g (18 g baseline), electric preheat with three levels: low about 85 °C (dark roasts), medium about 90 °C (medium), high about 95 °C (light). The 58 Plus 2 ships with a high flow and a low flow basket; low flow suits finer grinds and light roasts.
* Cafelat Robot: 58 mm, 16 to 22 g, very simple, preheat with hot water.

**Workflow (any manual lever)**
1. Heat water: just off the boil for light roasts (in the cylinder it will lose a few degrees), 93 to 96 °C for medium, about 90 °C for dark. Flair's own guidance: start at 93 to 96 °C, go down to about 90 °C for darker roasts.
2. Preheat: on non electric models fill the empty brew cylinder with near boiling water (Classic about 100 ml, one pass; do a second pass if shots still taste cool at the end), wait about as long as grinding takes, dump. On a 58, run the preheat for several minutes (10 min for full stability) with the lever raised and plunger at the top. Preheat the portafilter too where possible.
3. Grind and prep: espresso range, usually a touch coarser than for a pump machine at the same time, but grind finer when using long preinfusion or slow ramps. WDT, level, tamp.
4. Assemble quickly and fill the cylinder: the puck retains roughly 1 to 1.5 g of water per g of coffee, so fill well above the target yield (in practice fill to the max for the head) and stop on yield with a scale under the cup.
5. Preinfusion: 1 to 2 bar (light lever pressure, gauge barely moving) for 8 to 10 s, up to 15 s for light roasts, until the first drops appear under the basket.
6. Ramp smoothly to 6 to 9 bar. Hold firm constant force, don't pump the lever. Many people decline the pressure in the last third of the shot (9 down to 5 or 6 bar) to mimic a spring lever and reduce bitterness.
7. Stop on yield (weigh the cup), then release pressure safely: on Flair, hold the head, raise the lever fully, lift the plunger stem to vent before removing.

**Time**: on a Flair, 35 to 45 s total at 6 to 9 bar is normal (longer than pump machines because preinfusion and ramp are counted). Use time as a diagnostic, taste first.

**Lever recipes (starting points)**
| Recipe | Roast | Dose / yield | Water | Profile |
|---|---|---|---|---|
| Classic lever | medium / dark | 18 g / 36 g (1:2) | 90 to 93 °C | 8 s preinfusion at 1 to 2 bar, ramp to 8 to 9 bar, decline to 5 bar near the end; 35 to 45 s |
| Light roast "blooming" | light | 18 g / 45 to 54 g (1:2.5 to 1:3) | just off the boil, 58 on high | 10 to 15 s preinfusion, optional 10 to 20 s pause at near 0 bar (bloom), then 6 to 9 bar declining to 4 to 6 bar; grind finer |
| Turbo / low pressure | light | 18 g / 54 g (1:3) | off the boil | coarser grind, 1 to 2 s preinfusion, flat 6 bar, 15 to 25 s |
| Ristretto | medium / dark | 18 g / 18 to 27 g (1:1 to 1:1.5) | 90 to 92 °C | short preinfusion, 9 bar, decline |
| Lungo / allongé style | light | 18 g / 60 g+ (1:3 to 1:4) | off the boil | PRO 2 example from Flair: 20 g with the cylinder at 60 ml gives about 60 g (1:3); lower pressure 6 bar |

**Lever troubleshooting**
* Lever very hard to push, little or no flow at 10 bar: stop, grind coarser and/or lower the dose; on a Flair, too fine a grind can damage the machine.
* No crema, gauge never climbs: grind too coarse or stale coffee.
* Sour, thin even at good time: heat is the usual culprit; preheat longer or twice, use hotter water, finer grind or longer ratio.
* Spurts or jets from the basket (watch with a bottomless setup and a small mirror): channeling, improve WDT and tamp; a brief pressure dip can collapse a channel.
* Shot fades at the end, bitter tail: decline pressure in the final third or stop earlier.

**Drinks with a Flair**: everything from the milk drinks list works; Flair's own list includes espresso, cappuccino, café latte, americano, café crema, macchiato, breve, mocha, iced latte, Gibraltar (cortado style, about 1:1 milk in a 4.5 oz glass) and Australian latte (latte in a smaller cup, less milk). Since there's no steam wand, use a separate milk frother or stovetop steamer.

### Milk drinks (barista cheat sheet basics)
* Steam to 55 to 65 °C (sweetest around 60 °C); never above 70 °C (scalded, sulphurous).
* Stretch (introduce air) at the start, briefly, then texture with a whirlpool; "silky wet paint" for latte art.
* Whole milk textures and tastes best; oat "barista" versions work for plant milk.
* Typical drinks: espresso (single 25 to 30 ml, double 50 to 60 ml), ristretto, lungo, americano (espresso plus about 2× hot water, water first preserves crema), long black (water first), macchiato (espresso plus a spoon of foam), cortado (1:1 espresso and steamed milk), flat white (double shot, about 110 ml steamed milk, thin foam layer, 150 to 180 ml total), cappuccino (about one third espresso, one third milk, one third foam, 150 to 180 ml in Italy), latte (double shot, 200 to 300 ml milk, thin foam), affogato (shot over ice cream).
* Cup sizes common in cafés: 8, 12, 16 oz.
* Cleaning: backflush with water daily, with detergent (e.g. Cafiza) weekly on machines with a 3 way valve; purge and wipe the steam wand after every use; descale per water hardness.

## Moka pot

Italian classic; makes a strong, concentrated coffee (not espresso: about 1 to 2 bar).

### Improved method (Hoffmann and community consensus, r/mokapot)
1. **Grind**: finer than filter, coarser than espresso: 360 to 660 µm, like fine table salt. Espresso fine grinds clog, over extract and push the pressure up.
2. **Fill the basket** fully and level, no tamping (tapping lightly to settle is fine). Underfilling causes channeling and weak coffee. If you want less coffee, use a smaller pot, or a reducer insert for that pot.
3. **Water**: just off the boil (or around 90 °C) in the base, up to just below the safety valve, never above it. Hot water shortens time on the stove and avoids "baking" the grounds, which causes the metallic, burnt taste.
4. **Assemble** with a towel (hot base). Optional: an AeroPress paper filter on top of the grounds, under the upper chamber, for a cleaner cup.
5. **Heat**: medium low, lid open so you can watch. Flame should not lick the sides. On induction you need a steel pot (or an adapter plate).
6. **Watch the flow**: it should be a slow, honey coloured stream. When it turns pale/blond and starts to sputter or hiss, remove from heat immediately.
7. **Stop the brew**: cool the base under cold water or on a wet towel. Stir in the upper chamber (layers differ in strength), serve at once.

Ratio is roughly 1:7 to 1:10 by mass (a 3 cup Bialetti holds about 15 to 17 g coffee and 130 to 150 g water). Typical brew on the stove 2 to 3 minutes with preheated water.

### Low effort repeatable moka (La Sosta, Italian roaster)
A shorter version of the same method, for a user who wants a morning routine rather than a protocol. Start from a clean pot, gasket and filter plate free of old residue, with fresh moka grind and bottled or filtered water, not hard tap water.
* Fill the base to just below the safety valve. Fill the basket level to the rim, no tamping, only a light levelling with a finger or the back of a teaspoon.
* Low or medium low flame, never one that wraps around the sides. On the heat with the lid open so the flow is visible.
* When the coffee is rising steadily and the colour starts to lighten, turn the heat off and let it finish on residual heat. Stir gently in the upper chamber, serve immediately.
* Their repeatable ratio for adjusting by taste is **1:10**, for example 9 g coffee to 90 g water in a classic 2 cup pot. Their main upgrade is preheated water in the base: less time on the stove, no "cooked" taste, more sweetness and aroma. For maximum control, pull the pot off just before the final gurgle and cool the base under a trickle of cold water to stop the extraction.
* Diagnosis by sound and sight, in their words: a loud hiss with coffee spitting out means the heat is too high **or the grind too coarse**; a very slow, gurgling rise means the heat is too low or the grind too fine.

Note, because sources conflict here: La Sosta attributes coffee spitting out to a grind that is too coarse, while the table below (following Hoffmann and r/mokapot) attributes it to a grind too fine or tamped. Don't pick a side, diagnose by **how** the coffee leaves the column, which separates the two cases cleanly:
* **Rushes out fast, all at once, pale and thin**: grind too coarse (or the basket underfilled). Too little resistance, so water drives through before pressure and temperature settle. Cup is weak and sour.
* **Sprays and spits in bursts rather than a steady stream, loud hiss, slow overall**: grind too fine, tamped, or a clogged filter plate. Resistance builds pressure until it breaks through in gouts. Cup is bitter and astringent.
* **A steady, honey coloured stream** is the target. Neither bursts nor a rush.
* **Spitting only at the very end**, after a full steady flow, is normal and not a fault: it is the signal to take the pot off the heat.

Heat is the confound: too high a flame makes the pot spit with any grind, so lower it first and only then judge the grind by the character of the flow.

### Moka troubleshooting
| Problem | Fix |
|---|---|
| Bitter, burnt, metallic | preheated water, lower heat, stop earlier, cool base, grind slightly coarser, lighter roast |
| Sour, thin | grind finer, ensure the basket is full, hot water, let it run a bit longer |
| Spits in bursts instead of a steady stream | heat too high, or grind too fine / tamped / clogged plate (see the note above on reading the flow) |
| Rushes out fast, pale and thin | grind too coarse, or basket underfilled |
| Coffee doesn't come up / steam from valve | grind too fine, tamped, clogged filter plate; stop immediately for safety |
| Leaking at the joint | worn gasket (replace, check the size), grounds on the rim, not screwed tight |
| Grounds in the cup | grind too fine or damaged filter plate; paper filter helps |

### Moka with light roasts
Light roasts can work well in a moka: grind at the finer end of the range, use just boiled water, keep the flow slow, and accept a brighter, more tea like cup. Dilute with hot water for a filter like drink.

### Care
* Rinse with hot water only; no dishwasher for aluminium pots; dry fully before reassembly to avoid oxidation.
* Remove the gasket and filter plate periodically to clean trapped grounds; replace the gasket roughly yearly with daily use.
* Don't reheat leftover coffee in the pot.

## Cold brew and iced coffee

Two different things, and worth separating for the user before giving a recipe. **Cold brew** is a long immersion in cold water: low acidity, heavy and sweet body, chocolate and nut notes forward, floral and fruity top notes largely lost. **Japanese iced coffee** (iced V60) is a hot extraction straight onto ice: brewed hot so the aromatics develop, then chilled instantly, which locks in the profile and keeps floral notes, fruit and bright acidity. For a light roast with a delicate aromatic profile, iced V60 is almost always the better use of the beans; cold brew suits medium and darker roasts, and is the one to make ahead in volume.

### Iced V60 / Japanese iced coffee (La Sosta recipe)
16 g coffee, light or medium light roast, V60 grind (same as hot V60 or a touch finer). Total liquid 220 g at a **14:1 water-plus-ice to coffee** ratio, split roughly **70% hot water / 30% ice**: 150 g water at 90 to 93 °C and 70 g ice.
* Put the paper in the dripper, rinse with hot water, empty the carafe.
* Put 70 g ice in the carafe, sit the V60 on top, zero the scale.
* Add 16 g coffee, level the bed without pressing.
* 0:00 bloom with 40 g hot water over about 10 s, wetting all the grounds. Let it sit until 0:30 to 0:40.
* 0:40 pour 60 g to 100 g total, again over about 10 s with a steady flow.
* About 1:10 pour the last 50 g to 150 g total.
* Wait until everything has percolated into the carafe, ideally around 2:00 to 2:10, then lift the dripper.
* Swirl the carafe so the remaining ice melts fully and the strength evens out, then pour over fresh ice in a glass.
The scaling rule, so it holds at any dose: total liquid (hot water + ice) 14:1 to 15:1 against the coffee, of which about 70% hot water and 30% ice. If the cup is too dilute, keep the dose and reduce total liquid slightly; if too intense, increase it. Note that serving over fresh ice in the glass dilutes further as it melts, so a cup that tastes right in the carafe will soften in the glass.
Their adjustments: too strong, move from 1:13 or 1:14 to 1:15 or 1:16 on total liquid, or keep the dose and serve over more ice. Too watery or structureless, reduce total liquid slightly (less ice or less water) at the same dose, or go a touch finer at the same recipe. Bitter or astringent is usually too fine or too long, so go slightly coarser and aim to finish by 2:10 to 2:20. Sour or under extracted, check the water is genuinely at 90 to 93 °C, lengthen contact time with slightly fuller pours after the bloom, raise the dose, or tighten the grind.
If the user already brews hot V60, say this plainly: nothing changes except how much of the water goes in the kettle and how much goes in as ice.

### Cold brew, ready to drink (La Sosta recipe)
**1:10**, e.g. 70 g coffee to 700 g water. Coarse grind, "like coarse salt". Fresh cold water, filtered or bottled, not too hard. A clean container with a lid, and a paper filter (V60, Chemex or AeroPress) or a fine mesh sieve plus cheesecloth for straining.
* Weigh and grind the coffee coarse, put it in the container.
* Add the water, stir well so all the grounds are wet, close the lid.
* Steep: **16 to 20 h in the fridge, or 12 to 16 h at room temperature.** Room temperature extracts faster, so it needs the shorter window.
* Strain slowly through paper or through a fine sieve with cheesecloth, into a clean container.
* Drink neat, over ice, or let down with cold water if it is too intense.
Keeps a few days in the fridge; they recommend drinking it within **3 to 4 days** for best flavour. Paper filtering gives a cleaner, more velvety cup; stopping at the mesh sieve leaves it more rustic and heavier bodied.

### Cold brew concentrate (La Sosta recipe)
For milk drinks, tonic, cocktails, or simply to take less fridge space. **1:6 to 1:7**, e.g. 80 g coffee to 480 to 560 g water. Same steep windows: 16 to 20 h in the fridge or 12 to 16 h at room temperature, then refrigerate either way.
* Neat: 1 part concentrate to 1 to 2 parts water or ice, to taste.
* With milk: 1 part concentrate to 2 parts milk.
* With tonic: 1 part concentrate to 2 to 3 parts tonic water, over ice.

### Cold brew troubleshooting
| Taste / symptom | Likely cause | Fix |
|---|---|---|
| Too strong, syrupy | ratio too tight, or over steeped | dilute more in the glass; next time go to 1:11 or 1:12 |
| Watery, flavourless | ratio too loose, or under steeped | more coffee (1:10 to 1:9), or add a few hours of steep |
| Bitter, astringent | grind too fine, or steeped too long | grind coarser, stay inside 16 to 20 h fridge / 12 to 16 h ambient |
| Muddy, silty body | strained through mesh only, or fines from the grinder | finish through a paper filter |
| Off, dirty, fermented taste | unclean container, filters or fridge, or kept too long | clean everything, drink within 3 to 4 days |
| Flat, no aroma, no acidity | inherent to the method with light roasts | this is what cold brew does; switch to iced V60 to keep the aromatics |

## More methods and drinks (CoffeeGeek how-tos)

Quick recipes from CoffeeGeek's how-to guides; link the guide when the user wants the full walkthrough.
* **Vietnamese iced coffee (phin)**: 14 g (phin max about 15 g), grind between moka and pour over (table salt), 30 ml sweetened condensed milk in the glass, don't stir. Level the grounds without pressing, screw the press screen down to touch, then back it off one full turn. Bloom 20 to 30 ml of water at 96 °C for 20 to 30 s, add 90 to 100 ml, lid on, 4 to 5 min until dripping stops (a big pool left after 5 min means too fine or screen too tight). Stir 20 to 30 s, fill with ice, stir, serve. Hot version: 8 to 10 g per 100 ml, 15 to 20 ml condensed milk.
* **Japanese iced coffee (CoffeeGeek version)**: 35 g coffee, 250 g hot water at about 96 °C, 250 g ice in the carafe (500 ml total, about 1:14 counting ice), fine pour over grind. Bloom about 70 g for 30 s, then pour slowly (under 5 g/s). Stir at the end, serve without extra ice (it would dilute). Best with balanced light to medium roasts with fruit and chocolate notes.
* **Hario Mugen + Switch hack**: Mugen dripper seated in a Switch base, V60 #2 paper, 15 g to 300 g (1:20), usual pour over grind (600 to 650 µm, 1Zpresso X Ultra about 1+5). Valve closed: pour 150 g fast, stir 3 to 4 s, wait 60 s, open, pour the other 150 g slowly (about 5 g/s) with a swirl; done in about 4 min. The author reports TDS similar to a 1:15 pour over thanks to the immersion phase.
* **Turkish coffee (cezve / ibrik)**: about 90 ml cold water per demitasse, one heaping teaspoon (about 7 g) of coffee ground finer than espresso (powder, 200 µm or less), optional sugar about 1 tsp per 2 tsp coffee. Stir everything cold until sugar dissolves, then medium low heat and no more stirring. Lift off as the foam rises, let it settle, repeat (three rises is the classic), then pour in small alternating amounts so every cup gets foam. Use a pot with plenty of headspace.
* **Home cupping / tasting party**: 3 or 4 coffees, 2 bowls each, 10 g per bowl with 170 to 180 ml of water at about 93 °C (about 1:17), coarse grind. Steep 4 min, break the crust with three gentle stirs, skim, wait about 2 min, slurp. Note fragrance, aroma, sweetness, acidity, body, free associations and a "mug test" (would you drink a big mug of it?); optional 1 to 10 scores. Rinse spoons in hot water between bowls; mark bowl bottoms for blind tasting; retaste as it cools.
* **Siphon (vacuum)**: about 1:15 (e.g. 25 g to 375 g), medium fine grind, water in the lower bowl, heat until it rises (about 90 to 94 °C in the top), add coffee, stir to wet, steep about 1 min with a second gentle stir, remove heat and let it draw down (about 45 to 60 s). Clean, tea like, aromatic cup. CoffeeGeek has a full step by step guide.
* **Cloth pour over (nel drip)**: rinse and keep the cloth damp and refrigerated between uses; brew like a slow pour over, slightly coarser; heavier body than paper with clean cup.
* **Espresso drinks**: CoffeeGeek distinguishes the **traditional macchiato** (Italian: espresso "stained" with a spoon of foam) from the **modern macchiato** (North American cafés: small milk drink, often with latte art), **dry vs wet cappuccino** (more foam vs more liquid milk), the **flat white** (Australian/NZ: double shot, thin microfoam), the **lungo**, **caffè crème (Swiss)** (a long, lightly extracted coffee pulled through the espresso machine, about 1:6 to 1:8, coarser grind), **Americano** (espresso plus hot water; long black puts water first), **iced espresso** and **Irish coffee** (hot strong coffee, brown sugar, Irish whiskey, lightly whipped cream floated on top).
* **Puck prep**: CoffeeGeek's WDT guide covers the Weiss Distribution Technique (fine needles, stir to the bottom of the basket, break clumps, level before tamping).
* **Gear guides**: CoffeeGeek publishes yearly buying guides (best budget grinders, best manual grinders, best budget espresso machines). Point users there for current models and prices rather than quoting prices from memory.

## Beans, varieties, processing, origins

### Species
* **Arabica (Coffea arabica)**: about 60% to 70% of world production, higher altitude, more acidity, sugars and aroma, 1.2% to 1.5% caffeine.
* **Robusta (Coffea canephora)**: hardier, lower altitude, more bitterness and body, about 2% to 2.7% caffeine, more crema; traditional in Italian espresso blends, increasingly available as "fine robusta".
* **Liberica / Excelsa**: niche, smoky, fruity, jackfruit like; Southeast Asia and parts of Africa.
* Wild or rare species (eugenioides, stenophylla) appear in competitions.

### Notable Arabica varieties
* Typica and Bourbon: the two historical lineages; Bourbon is sweet and complex.
* Caturra, Catuai, Pacas, Villa Sarchi: compact mutations, common in Latin America.
* SL28, SL34: Kenyan, intense blackcurrant, juicy acidity.
* Gesha / Geisha: floral (jasmine, bergamot), tea like; Panama made it famous; very expensive.
* Ethiopian landraces ("heirloom", e.g. 74110, 74112, Kurume): floral, citrus, berry.
* Pacamara, Maragogype: large beans, distinctive.
* Catimor, Sarchimor, Castillo, Parainema: rust resistant hybrids with robusta ancestry.
* F1 hybrids (Centroamericano, Starmaya): newer, productive and resilient.

### Processing (huge effect on flavour)

Processing also shifts brew temperature, not just flavour: see "Brew temperature by roast level and processing" in the V60 section, where each step from washed toward ferment-forward takes about 1 °C off the water.
* **Washed (wet)**: fruit removed before drying. Clean, clear acidity, terroir and variety expression.
* **Natural (dry)**: whole cherry dried. Fruity, winey, heavy body, sometimes funky.
* **Honey / pulped natural**: skin removed, some mucilage left (white, yellow, red, black honey by amount). Sweet, round.
* **Anaerobic / carbonic maceration**: controlled fermentation in sealed tanks; intense, boozy, tropical, sometimes divisive.
* **Infused / co-fermented**: added fruit, spices, yeast or flavouring; debated in specialty (transparency matters).
* **Wet hulled (Giling Basah)**: Indonesia (Sumatra); earthy, herbal, heavy body, low acidity.
* **Decaf**: Swiss Water, Mountain Water, CO2, and sugar cane (ethyl acetate, "EA") processes; modern specialty decafs can be excellent.

### Origin tendencies (generalizations, not rules)
* Ethiopia: floral, citrus, bergamot, berry (washed Yirgacheffe, Guji; naturals very fruity).
* Kenya: blackcurrant, tomato, grapefruit, bright juicy acidity, syrupy.
* Rwanda, Burundi: red fruit, black tea, delicate; watch for "potato defect".
* Colombia: balanced, caramel, red fruit, wide range; many experimental processes.
* Brazil: chocolate, nuts, low acidity, body; base of most espresso blends.
* Central America (Guatemala, Costa Rica, Honduras, El Salvador, Panama): chocolate, stone fruit, citrus; Panama Geisha floral.
* Peru, Bolivia, Ecuador: sweet, clean, sometimes floral.
* Indonesia: earthy, spicy, heavy (Sumatra); Java and Sulawesi variations.
* Yemen: winey, dried fruit, spice; rare and prized.
* India: Monsooned Malabar (low acidity, earthy) and good robusta.

### Specialty coffee basics
* SCA definition: green coffee with zero primary defects and limited secondary defects, cupping 80+ points on the 100 point scale (CVA is the newer SCA evaluation system). 85+ is excellent, 90+ exceptional.
* Look for: roast date (not just best before), origin down to farm or washing station, producer, variety, process, altitude, harvest.
* Third wave / specialty roasters favour lighter roasts to show origin character.

## Roasting and roast levels

* **Light (Nordic, "filter roast")**: Agtron roughly 70 to 85+. Light brown, dry surface, high acidity, floral and fruit notes, tea like body. Dense and harder to extract.
* **Medium**: Agtron 55 to 70. Balanced, caramel sweetness, moderate acidity. Classic "omniroast".
* **Medium dark / dark**: Agtron below 50. Oily surface after a few days, bittersweet, chocolate, roasty, smoky, low acidity; traditional Italian espresso.
* Roast milestones: drying, Maillard / browning, first crack (light roasts dropped shortly after), development time, second crack (dark roasts).
* "Omniroast" means the roaster intends it for both filter and espresso; "filter roast" vs "espresso roast" profiles exist.
* Underdeveloped coffee tastes grassy, peanut, sour without sweetness; that's a roasting defect, not something brewing can fully fix. Point it out kindly if the symptoms match.

### Light roasts in practice (priority topic)
* **Rest**: 2 to 4 weeks off roast before peak for filter, 3 to 6 weeks for espresso. Too fresh gives a muted, sour, gassy cup with lots of bubbling in the bloom.
* **Water temperature**: hot, 96 to 100 °C for filter.
* **Grind**: finer than you'd use for medium roasts, as long as drawdown stays reasonable; a high clarity grinder helps a lot.
* **Ratio**: often 1:16 to 1:17 for filter; for espresso 1:2.5 to 1:3 or turbo shots.
* **Water**: soft with moderate buffer; hard alkaline water kills the acidity that makes light roasts special.
* **Agitation**: use bloom swirl, avoid excessive stirring that creates fines migration and bitterness.
* **Expect**: tea like body, bright acidity, sweetness as the extraction gets right; if it's only sour, extract more; if it's sour plus astringent, look at grind evenness.
* **Cooling**: taste as it cools, light roasts open up between 50 and 60 °C.

## Tasting and cupping

### How to taste
* Separate the attributes: aroma, flavour, acidity (quality and intensity), sweetness, body / mouthfeel, balance, aftertaste / finish, clarity.
* Acidity types: citric (lemon, orange), malic (green apple), tartaric (grape, wine), phosphoric (sparkling, cola like, Kenya), lactic (creamy), acetic (vinegar, bad in excess).
* Use an aroma or flavour wheel: start from the inner category, then move outward to a specific descriptor. The reference here is the CoffeeMind Aroma Wheel (below); the SCA / WCR Coffee Taster's Flavor Wheel is the other common standard.

### Aroma wheel (CoffeeMind, 13 categories)
Descriptor hierarchy from the CoffeeMind Aroma Wheel (link in Sources). Use it to help users name what they smell and taste, to suggest what to look for in a coffee, and as data for a sunburst chart. When drawing it, build your own sunburst from this list with neutral or category based colours; do not imitate CoffeeMind's graphic, and credit CoffeeMind for the taxonomy.

| Category | Descriptors |
|---|---|
| Floral | lavender, rose, hibiscus, jasmine, coffee blossom, camomile, elderflower |
| Berry | strawberry, raspberry, blueberry, black currant, blackberry |
| Fruity | pear, green apple, red apple, lime, lemon, bergamot, orange, mandarin, apricot, peach, mango, pineapple, honeydew melon |
| Dried fruit | raisin, prune, dates, cranberry |
| Sweets | vanilla, butter, honey, caramel, sweet liquor |
| Chocolate | pure cocoa, dark chocolate, milk chocolate |
| Nutty | hazelnut, almond, peanut, walnut, pecan, cashew, brazil nut |
| Roasted | smoke, tobacco, toast, burned, ashy |
| Industrial | leather, rubber, earthy, musty, woody, paper/cardboard |
| Spicy | cinnamon, clove, nutmeg, cardamom, pepper, coriander seeds, liquorice |
| Cereal | malt, grain |
| Green | cedar, grass, straw, hay |
| Herb / Vegetal | thyme, oregano, basil, rosemary, garden peas, cucumber, tomato |

How to use it:
* Map coffees to likely regions: washed Ethiopian toward floral, berry, citrus (lemon, bergamot); Kenyan toward black currant, tomato, red fruit; naturals toward berry, dried fruit, sweets; Brazil and darker roasts toward nutty, chocolate, roasted; anaerobic toward tropical fruit and sweet liquor.
* Diagnose with it: burned, ashy, smoke dominating a specialty light roast suggests over extraction, an overheated moka or a roast issue; grass, hay, straw and peanut suggest underdevelopment or under extraction; paper/cardboard and musty point to unrinsed filters or stale, badly stored coffee; rubber and earthy can be robusta or defects.
* Teach outside in: if the user can't name a note, ask which inner category feels closest, then offer three or four descriptors from that slice.
* Industrial and most of roasted and green are defects in specialty light roasts, though some (smoke, tobacco, cedar) can be pleasant in darker or aged coffees.
* Sour vs acidic: acidity is pleasant, structured, sweet supported; sourness is sharp, thin, salty, a sign of under extraction.
* Bitter vs astringent: bitterness is a taste on the tongue; astringency is a drying sensation, often from over extraction or fines.
* Compare two coffees side by side; it's the fastest way to learn.

### Cupping protocol (SCA)
* Ratio 8.25 g per 150 ml water (about 1:18), grind slightly coarser than filter, water about 93 °C.
* Smell dry grounds (fragrance), pour water, wait 3 to 5 min, break the crust with a spoon smelling the aroma, skim, then slurp from about 8 to 10 min as it cools, tasting at several temperatures.
* Rinse spoons between cups, score attributes, note defects.

## Equipment basics
* **Scale** with 0.1 g resolution and timer: the single best cheap upgrade after the grinder.
* **Gooseneck kettle** with temperature control for pour over.
* **Brewers**: V60 (plastic retains heat best and is cheap), Kalita Wave (flat bottom, forgiving), Origami, Orea, April (flat, fast), Chemex, AeroPress, Clever / Switch.
* **Espresso machines**: single boiler, heat exchanger, dual boiler, lever, and flow/pressure profiling (Decent, Meticulous; Flair and Cafelat Robot manual levers, see "Manual lever espresso"). For light roasts, temperature stability and pressure control help.
* **Refractometer**: optional, for measuring TDS and extraction yield.

## Safety notes
* Moka pot: never fill water above the safety valve, never tamp hard, never leave unattended on high heat. If steam escapes from the valve, remove from heat.
* Hot water and steam wands cause burns; purge away from hands.
* Caffeine: about 60 to 100 mg per espresso, 100 to 200 mg per mug of filter. EFSA (2015 opinion) considers safe for healthy adults up to **400 mg per day** and up to **200 mg in a single dose** (that single dose limit is the one people miss: two strong filter mugs back to back can reach it). During pregnancy, habitual intake up to **200 mg per day** from all sources combined. FDA guidance converges on the 400 mg daily figure for healthy adults. Caffeine from tea, cola, energy drinks, chocolate and supplements counts toward the same total.

## Sources (cite when the user wants to dig deeper)
* James Hoffmann, YouTube: https://www.youtube.com/@jameshoffmann (Ultimate V60 Technique, A Better 1 Cup V60, Ultimate AeroPress, French press technique, moka pot series, water series, espresso and grinder reviews)
* European Coffee Trip, Hario V60 recipes (Hoffmann, Kasuya 4:6, Osmotic Flow comparison): https://europeancoffeetrip.com/hario-v60-recipes/
* 4:6 method calculator (Tetsu Kasuya, V60): https://aeyoll.github.io/4-6-method/ (source: https://github.com/aeyoll/4-6-method)
* Tetsu Kasuya Hybrid Method (Honest Coffee Guide transcription): https://honestcoffeeguide.com/brew-recipes/tetsu-kasuya-hybrid-method/
* Tetsu Kasuya New Hybrid Method (video): https://www.youtube.com/watch?v=z0Kf5J-Y5V0
* CoffeeMind Aroma Wheel: https://coffee-mind.com/wp-content/uploads/2019/08/CoffeeMind-Aroma-Wheel_pdf__1_side_-768x936.jpg
* Flair Espresso guide (preheating, brew ratios, advanced brewing, pressure profiling): https://flairespresso.com/blogs/espresso-guide
* Flair: 11 drinks with a Flair: https://flairespresso.com/blogs/news/11-drinks-with-flair-espresso-maker
* Flair lever video: https://www.youtube.com/watch?v=4Qcg2k2X3CM
* r/FlairEspresso recipe thread: https://www.reddit.com/r/FlairEspresso/comments/xih564/your_espresso_recipes/
* CoffeeGeek guides and how-tos (V60, Chemex, siphon, cloth, Turkish, Vietnamese and Japanese iced coffee, cupping party, WDT, espresso drinks, buying guides): https://coffeegeek.com/guides/howtos/ and https://coffeegeek.com/guides/feature-guides/
* 1Zpresso grind setting guide: https://1zpresso.coffee/grind-setting/
* Honest Coffee Guide (grind size charts, per grinder settings, brew recipes, moka pot articles, drink guides): https://honestcoffeeguide.com/
* La Sosta Specialty Coffee (Italian roaster) brewing guides, each page linking a PDF: V60 https://lasosta.coffee/en/pages/guida-v60-come-preparare-il-caffe-filtro-a-casa, iced V60 / Japanese iced coffee https://lasosta.coffee/en/pages/japanese-iced-coffee-con-v60-come-preparare-il-caffe-filtro-freddo-a-casa, cold brew https://lasosta.coffee/en/pages/guida-cold-brew-come-preparare-un-caffe-freddo-specialty-a-casa, moka https://lasosta.coffee/en/pages/guida-moka (guides are in Italian; the recipe text lives in the linked PDF, not in the page itself)
* Complete Home Barista, moka pot grind size FAQ (flow character as the grind diagnostic: steady stream vs bursts vs rushing): https://completehomebarista.com/faqs/brewing-methods/moka-pot/moka-pot-grind-size/
* SCA standards (brewing control chart / Golden Cup, water quality): https://sca.coffee/research/coffee-standards
* EFSA Scientific Opinion on the safety of caffeine (2015), source of the 400 mg/day, 200 mg single dose and 200 mg/day in pregnancy figures: https://www.efsa.europa.eu/en/efsajournal/pub/4102
* Hario official James Hoffmann V60 recipe (confirms the 2× dose bloom and pour timings): https://www.hario-usa.com/blogs/recipes-and-more-from-friends/james-hoffmann-uitimate-v60-technique
* Simon Gautherin / Pull & Pour, "Pour over brew temps based on roast level & processing" chart (the roast level x processing temperature grid): https://www.pullandpour.com/
* Reddit communities: https://www.reddit.com/r/V60/, https://www.reddit.com/r/espresso/, https://www.reddit.com/r/mokapot (wikis and FAQs, real user dial in experiences)
* Coffee Knowledge presentation (species, processing, drinks): https://www.scribd.com/presentation/511729726/Coffee-Knowledge
* Barista Cheat Sheet (espresso menu, dialing in, milk texturing, troubleshooting, cleaning): https://irp-cdn.multiscreensite.com/2737510f/files/uploaded/Barista%20Cheat%20Sheet.pdf

If web access is available and the user asks for a specific roaster's recipe, a newer Hoffmann video, or exact settings for an uncommon grinder, search these sources before answering and say where the numbers come from.
