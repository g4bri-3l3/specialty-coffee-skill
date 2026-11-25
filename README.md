# ☕ Specialty Coffee Guide: a Claude Skill

A [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that turns Claude into an experienced specialty barista and coffee educator.

Ask a question about brewing and you get a **recipe card** back: dose, grind (in µm *and* clicks on your grinder), water and temperature, ratio, timed pour steps with cumulative weights, total time. Then what to change if the cup comes out sour, bitter, weak or harsh. One variable at a time, in the order grind → ratio → temperature → technique.

## What it covers

| Area | Contents |
| --- | --- |
| **Pour over** | V60 recipes: Hoffmann (1- and 2-cup), Tetsu Kasuya 4:6 with its calculator logic, Osmotic Flow, a light-roast clarity recipe, Kasuya Hybrid / New Hybrid for the Hario Switch, La Sosta's five-equal-pours beginner recipe |
| **Other brewers** | Chemex, Kalita Wave and Switch/Clever full immersion each with their own defaults rather than a reshaped V60 recipe, plus AeroPress, French press and batch brew on a filter machine (ratio, basket fill, why half a basket tastes thin) |
| **Espresso** | Baseline recipe, dialing-in workflow, puck prep, the adjustment compass, pump-machine preinfusion and profiling (blooming shots, declining pressure, flow control, OPV), lever and Flair profiling, milk drinks and plant milks |
| **Moka pot** | Italian-style and specialty-leaning approaches, a low-effort repeatable 1:10 version, plus valve and overfilling safety |
| **Cold & iced** | Why cold brew and Japanese iced coffee are different choices, then full recipes for each: iced V60 brewed onto ice, cold brew ready-to-drink and as a concentrate with dilution ratios for milk and tonic |
| **Grind** | General µm reference table, then per-grinder data with µm-per-click so settings convert between grinders (1Zpresso settings in `R.N.C` notation) |
| **Beans** | Varieties, processing methods, origins, roast levels, and a dedicated light-roast section |
| **Water** | Target mineral content, why it matters, what to do with what comes out of your tap, and a DIY recipe given as arithmetic (g/l per salt and a 100x concentrate) so you can check it rather than trust it |
| **Decaf** | Decaffeination processes, why the colour of a decaf bean lies about its roast level, and how it changes grind and extraction |
| **Preground** | The supermarket-coffee case: which levers are left when the grind is fixed, how stale coffee behaves, and why the grinder recommendation comes last |
| **Tasting** | SCA cupping protocol, the 13-category aroma wheel, brew control chart targets |
| **Other** | Siphon, Turkish cezve, Vietnamese phin, home cupping parties, espresso drink definitions, equipment basics, caffeine limits (EFSA/FDA) |

It also draws charts when there is chartable data: step charts for pour schedules, the brew control chart for TDS/extraction yield, radar plots for tasting notes, horizontal bars for grind-size ranges.

Every number is a **range plus a starting point**, never a bare figure, and data tables are labelled by provenance: official manufacturer data, community starting points, or explicit generalizations. Grinder settings are flagged as starting points to be verified by taste.

It is also told, at length, **not to make things up**. A coffee recipe is dangerously easy to fabricate: dose, pours and timings in a confident table look identical whether they came from a world champion or from nowhere, and the person reading it has no way to tell. So the skill names the four cases where that happens (a recipe attributed to someone, a setting for a grinder that is not in the tables, equipment specs, claims about a specific bag of coffee), tells Claude to say so and search instead, and repeats that instruction next to the tables where the temptation actually arises. `evals/prompts.md` is the hand-run check that it still works.

## Install

The whole skill is one file, `SKILL.md`. There is nothing to build and nothing to unpack.

**On claude.ai (web).** Download `SKILL.md` and upload it under Customize → Skills → `+` → `+ Create skill` → `Upload a skill`. It needs "Code execution and file creation" enabled in Settings → Capabilities, otherwise the upload option is hidden. Skills are account-wide: once uploaded it is available in every conversation, including inside Projects, and can be toggled off individually.

**In Claude Code.** Drop the file into your skills directory, in a folder matching the skill name:

```
~/.claude/skills/specialty-coffee-guide/SKILL.md
```

It is live immediately, no restart. Note that skills enabled on your Claude account also sync down into Claude Code on their own, read-only and one way, so if you install both ways you will see two entries.

Then invoke it with `/specialty-coffee-guide`, or just ask a coffee question and let Claude trigger it on its own.

## Sources

The knowledge is distilled from James Hoffmann, European Coffee Trip's V60 recipe comparison, the 1Zpresso official grind setting page, Honest Coffee Guide, Flair Espresso's lever guides, CoffeeGeek's guides and how-tos, the brewing guides of the Italian roaster La Sosta Specialty Coffee, and the r/V60, r/espresso and r/mokapot communities. The full attribution list lives in the `Sources` section at the end of `SKILL.md`, and the skill is instructed to say where its numbers come from.

## Contributing

Corrections and additions are welcome, especially grinder data (µm per click, with the grinder model and how you measured it) and recipes with a named, linkable source. Please edit `SKILL.md` and keep the provenance labelling intact. If you add a topic area, run the prompts in `evals/prompts.md` against the edited skill first: reference data added low in the file has a way of quietly weakening the behavioural rules at the top.

## License

[CC BY 4.0](LICENSE). Reuse, adapt and redistribute freely, including commercially, as long as you give credit.

This covers the text of the skill as written here. The underlying brewing data is attributed to its sources in the `Sources` section of `SKILL.md`: recipes and figures from James Hoffmann, Tetsu Kasuya, 1Zpresso, La Sosta Specialty Coffee and the others belong to them, and the license on this repo does not change that.
