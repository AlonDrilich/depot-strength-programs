# depot.fitness strength-program dataset

The 101 strength-training programs in the [depot.fitness](https://depot.fitness) library, as data: what each one
prescribes (sets, reps, rest), how long it runs, how many days a week it asks for, and how it says to progress. The
programs follow documented templates such as 5/3/1, 5×5, push/pull/legs and upper/lower.

This is what the library *prescribes*, not what people did, and it is not a sample of all training programs.

**Version** 2026.10.13 · **Snapshot** 2026-10-13 · **License** [CC BY 4.0](LICENSE)
**Page with the charts and the method:** https://depot.fitness/data

## Files

| File | Rows | One row per |
|---|---|---|
| [`programs.csv`](programs.csv) | 101 | program: level, type, goals, equipment, length, days per week, weekly prescribed sets, progression note |
| [`exercises.csv`](exercises.csv) | 484 | canonical exercise: programs using it, typical sets, reps and rest, every spelling merged |
| [`prescriptions-free-programs.csv`](prescriptions-free-programs.csv) | 82 | exercise in a training day, for the five programs that are free in full on depot.fitness |
| [`summary.json`](summary.json) | n/a | the headline numbers below |

The other 96 programs are described by `programs.csv` and counted in `exercises.csv` and `summary.json`; their
exercise-by-exercise prescriptions are not in this release.

## Definitions

- **Training day.** A day in the program's weekly schedule that lists at least one exercise. A day with none is a rest
  day. The schedule is one week, repeated for `duration_weeks`.
- **Prescribed sets.** The `sets` value on each exercise. The library does not mark warm-up sets.
  `weekly_prescribed_sets` sums them over one week.
- **Canonical exercise.** Names are slugified, mapped through an alias table (an abbreviation expanded, a parenthetical
  dropped, four barbell pairs merged), and a trailing "s" is merged when the singular also occurs. Names that could
  mean something else stay apart ("Squats", "Back Squat T1"). `exercises.csv` lists every merged spelling in
  `name_variants`. Counts are by exact name after merging, so a lift's labelled variants are not folded in.
- **Reps** are free text in the source. `reps_kind` is one of fixed, range, wave (5/3/1), list (a count per set),
  amrap, time, interval, rounds, effort ("x": one effort per set, the work is in the exercise name) or other.
  `reps_min` and `reps_max` are filled for fixed, range, wave and list; `per_side` marks per-leg, per-arm and per-side
  prescriptions. Rep statistics use the 1,565 rep-count prescriptions.
- **Type** is the library's own label. Counting by structure can differ from counting by label: `ppl-strength-powerbuilding` is a
  push/pull/legs split labelled Powerbuilding, so push/pull/legs is 9 programs by structure and 8 by `type`.
- **Medians** of an even count are the mean of the two middle values (intermediate programs: 59.5).

## Headline numbers

| | |
|---|---|
| Programs / prescriptions / training days | 101 / 1,791 / 390 |
| Levels | 30 beginner, 52 intermediate, 19 advanced |
| Length | 36 programs run 8 weeks, 28 run 12, 15 run 10, 14 run 6, 6 run 4, one 3 and one 16 |
| Training days per week | 3: 42 programs, 4: 40, 5: 10, 6: 9 |
| Weekly prescribed sets | median 58 (12 to 130); beginner 47, intermediate 59.5, advanced 67 |
| One session | median 5 exercises and 16 sets; 92.1% of sessions have 3 to 6 exercises |
| Rest | median 75 s; 180 s where the top of the rep range is 5 or fewer, 120 s at 6 to 8, 90 s at 9 to 12, 60 s at 13 or more |
| Reps (rep-count prescriptions) | top of range 1 to 5: 13.0%, 6 to 8: 10.4%, 9 to 12: 33.4%, 13 to 15: 32.9%, 16 or more: 10.4% |
| Rest days | 38 programs write rest days into the week; 82 leave three or four non-training days |
| Deloads | 10 progression notes mention a deload or reset |
| Exercises | 484 canonical; 98 appear in three or more programs. Back squat and bench press: 56 programs each |

## Limits

- One library, written by depot.fitness. Every count describes these 101 programs, not training programs in general.
- Prescriptions are as written. Progression is free text, and no program prescribes RPE or RIR.
- There is no exercise-to-muscle mapping in the source; `muscle_groups` is program-level.
- A snapshot. The library changes; compare `version`.

## Cite

depot.fitness. (2026). *depot.fitness strength-program dataset* (Version 2026.10.13) [Data set]. https://depot.fitness/data

```bibtex
@dataset{depotfitness_strength_programs_2026,
  author  = {{depot.fitness}},
  title   = {depot.fitness strength-program dataset},
  year    = {2026},
  version = {2026.10.13},
  url     = {https://depot.fitness/data},
  license = {CC BY 4.0}
}
```

## Contact

Corrections and questions: support@depot.fitness

## Changelog

- 2026.10.13: first release.
