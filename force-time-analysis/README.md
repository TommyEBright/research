# Force-Time Analysis

Browser-based analysis of force platform data for normal, band-assisted and band-resisted countermovement jumps (CMJs) and squat jumps (SJs).

Developed by Dr Tommy Bright ([ORCID 0000-0001-8089-817X](https://orcid.org/0000-0001-8089-817X), [ResearchGate](https://www.researchgate.net/profile/Thomas-Bright-4)).

**Live tool:** https://tommyebright.github.io/research/force-time-analysis/force-time-analysis.html

## Using it

Open `force-time-analysis.html` in any modern browser. No installation or internet connection is needed, and data are processed locally and never uploaded.

1. Load the raw Kinvent CSV exports (files or a whole folder). Participant, jump type (CMJ or SJ) and condition are read from the file name and can be edited.
2. Load each participant's normal (body weight) trials, which are used for body weight and body mass.
3. Inspect each trial. Movement onset, take-off and landing can be moved to the next detected candidate if the first is a false detection. No events can be placed by hand.
4. Export the results as CSV. Every row records the software version, the full settings used (including custom metrics) and any skipped events.

## Phases

Phases are defined from the ground reaction force relative to a reference weight (by default the trial's own standing weight, optionally body weight from the normal trials):

- **Unweighting phase** (CMJ only): movement onset until force returns to the reference weight
- **Active phase**: force above the reference weight (in SJs, from movement onset)
- **Pre-take-off deceleration phase**: force back below the reference weight until take-off
- **Landing loading phase**: landing to peak landing force

CMJ onset is detected when force falls below the quiet-stance mean.

For squat jumps, the recording starts in the squat hold. Onset is the start of the straight-up push, namely the last time force rises above the squat hold before peak force, so small movements during the hold are ignored. Any drop in force below the squat hold before the push is reported as countermovement depth, and the trial is flagged when it exceeds the set threshold. By default the SJ standing weight (and so the phase reference) comes from the steadiest window of quiet standing after landing, because with bands the force in the squat hold differs from standing.

In a normal CMJ with a system-weight reference, the active phase spans the braking phase and the propulsion phase up to peak upward velocity, and the pre-take-off deceleration phase is the remainder of the propulsion phase (McMahon et al., 2018).

## What it measures

Only metrics taken directly from the ground reaction force, which stay valid when an elastic band acts on the athlete. These are phase durations and impulses, minimum, mean and peak force, rates of force development, time to take-off, flight time, flight time : time to take-off, and landing peak force, time to peak and loading rate. Times are in seconds.

Every force-based metric is reported in absolute terms and relative to body mass (per kg) and body weight (BW), using body weight from the normal trials.

Centre-of-mass velocity, displacement, power and jump height are deliberately not reported, because the band force is not measured by the platform.

## Settings and calculations

All thresholds, windows and reference weights can be changed in Settings, alongside the take-off and landing detection method (fixed or flight-phase noise thresholds) and the optional 4th-order zero-lag Butterworth filter (with Winter's dual-pass correction and residual analysis). Calculation methods (impulse integration rule, average RFD definition, RFD window) can be changed, and custom metrics can be defined as a statistic between any two detected events with optional time offsets. Settings can be saved and reloaded as JSON.

## Citation

See `CITATION.cff`, or the "How to cite" section in the tool.

## Reference

McMahon, J. J., Suchomel, T. J., Lake, J. P., & Comfort, P. (2018). Understanding the key phases of the countermovement jump force-time curve. *Strength and Conditioning Journal*, 40(4), 96–106.
