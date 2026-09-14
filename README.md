# Awesome Sleep Tracking [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Curated list of tools, devices, datasets and open-source software for tracking and analyzing sleep: pulse oximetry, PAP therapy, wearables, EEG, and the metrics behind them.

Sleep data is scattered across proprietary apps that each report their own numbers with their own undocumented definitions. This list collects the software, formats, datasets and reference material that let you work with the raw signals yourself.

## Contents

- [Analysis Software](#analysis-software)
  - [PAP Therapy](#pap-therapy)
  - [Pulse Oximetry](#pulse-oximetry)
  - [EEG and Polysomnography](#eeg-and-polysomnography)
  - [Actigraphy and Wearables](#actigraphy-and-wearables)
  - [Automatic Sleep Staging](#automatic-sleep-staging)
- [File Formats and Libraries](#file-formats-and-libraries)
- [Device Protocols and Reverse Engineering](#device-protocols-and-reverse-engineering)
- [Datasets](#datasets)
- [Metrics and Definitions](#metrics-and-definitions)
- [Standards and Clinical References](#standards-and-clinical-references)
- [Hardware](#hardware)
- [Vendor APIs](#vendor-apis)
- [Communities](#communities)
- [Contributing](#contributing)

---

## Analysis Software

### PAP Therapy

- [OSCAR](https://www.sleepfiles.com/OSCAR) — Open Source CPAP Analysis Reporter. Reads SD-card data from most CPAP, APAP and BiLevel machines and renders it down to breath-by-breath detail. The reference tool for anyone titrating their own therapy. Windows, macOS, Linux.
- [OSCAR on Flathub](https://github.com/flathub/com.sleepfiles.OSCAR) — Flatpak packaging for Linux distributions.
- [SleepHQ](https://sleephq.com) — Web-based PAP data hosting and analysis with shareable links. Commercial with a free tier; widely used for asking forums to review a night.

### Pulse Oximetry

- [o2ring-analyzer](https://github.com/nighttimecf/o2ring-analyzer) — Command-line analyser for Wellue/Viatom O2Ring CSV exports. Computes ODI under both the 3% and 4% definitions side by side, enumerates desaturation events with onset, nadir, duration and recovery, and exports CSV/JSON/Excel. Baseline and event-duration rules are documented rather than implicit.
- [SpO2 Assistant / Viatom desktop tools](https://getwellue.com) — Vendor software for exporting recordings from Wellue and Viatom oximeters. Export is the useful part; the built-in reporting hides its definitions.

### EEG and Polysomnography

- [MNE-Python](https://mne.tools) — The standard Python library for EEG and MEG processing. Includes sleep-staging tutorials and readers for most clinical formats.
- [Luna](https://zzz.bwh.harvard.edu/luna/) — C++/R toolkit from Harvard for large-scale polysomnography analysis: spectral analysis, spindle and slow-oscillation detection, artifact handling. Built to process whole cohorts.
- [Visbrain — Sleep](https://visbrain.org) — GUI for visualising, scoring and analysing polysomnography recordings. Handles large multichannel files without loading everything into memory.
- [EDFbrowser](https://www.teuniz.net/edfbrowser/) — Free multiplatform viewer for EDF/EDF+, BDF and other biosignal formats. The quickest way to look at a raw recording.

### Actigraphy and Wearables

- [CareClinic](https://careclinic.io/sleep-tracker/) — Sleep diary that imports compatible wearable data and exports user logs as CSV.
- [pyActigraphy](https://github.com/ghammad/pyActigraphy) — Reads actigraphy data from seven device formats and computes non-parametric rest-activity variables (IS, IV, RA), fragmentation metrics and the Sleep Regularity Index. Well documented with interactive tutorials.
- [HypnosPy](https://github.com/HypnosPy/HypnosPy) — Device-agnostic Python library for circadian rhythm and sleep analysis, handling acceleration, actigraphy and heart rate at different sampling rates in one framework.
- [GGIR](https://github.com/wadpac/GGIR) — R package for raw accelerometer data, the most widely cited tool in accelerometer-based sleep and physical-activity epidemiology.
- [SleepPy](https://github.com/elyiorgos/sleeppy) — Processes multi-day raw accelerometer streams into per-day sleep reports and visualisations, implementing several published algorithms in a modular pipeline.
- [wearipedia](https://github.com/Stanford-Health/wearipedia) — Unified Python interface for extracting data from consumer wearables, including several sleep-capable devices.

### Automatic Sleep Staging

- [YASA](https://github.com/raphaelvallat/yasa) — Sleep analysis toolbox in Python: automatic staging, spindle and slow-wave detection, spectral analysis, hypnogram utilities. Open models, actively maintained.
- [U-Time / U-Sleep](https://github.com/perslev/U-Time) — Fully convolutional network for sleep staging that generalises across cohorts and channel configurations. Strong published accuracy.
- [TinySleepNet](https://github.com/akaraspt/tinysleepnet) — Compact deep-learning model for single-channel EEG sleep staging.
- [AutoSleepScorer](https://github.com/skjerns/AutoSleepScorer) — Sleep stage classification package. The README is also an unusually honest comparison of its own accuracy against newer alternatives.
- [SleepECG](https://github.com/cbrnr/sleepecg) — Sleep staging from ECG and heart-rate variability, useful when EEG is unavailable.

---

## File Formats and Libraries

- [EDF / EDF+ specification](https://www.edfplus.info) — The European Data Format, the lingua franca of polysomnography. Read this before writing any parser.
- [pyEDFlib](https://github.com/holgern/pyEDFlib) — Python reader and writer for EDF/EDF+ and BDF files.
- [Sleep as Android CSV export format](https://docs.sleep.urbandroid.org/services/csv.html) — Documented export schema for one of the largest consumer sleep-tracking datasets in existence.

---

## Device Protocols and Reverse Engineering

- [wellue-o2ring-protocol](https://github.com/farolone/wellue-o2ring-protocol) — Reverse-engineered Bluetooth Low Energy protocol documentation for the Wellue O2Ring, for reading data live rather than via vendor export.
- [Sleep as Android forum — hardware integration](https://forum.urbandroid.org) — Long-running discussions on integrating oximeters, rings and EEG headbands, including protocol changes between device revisions.

---

## Datasets

- [National Sleep Research Resource (NSRR)](https://sleepdata.org) — The largest open repository of polysomnography data. Hosts SHHS, MESA, MrOS, CHAT and many other cohorts, with full PSG signals and scored annotations. Requires a data-use agreement.
- [PhysioNet](https://physionet.org) — Open archive of physiological signal databases with permissive licensing and a stable citation model.
- [Sleep-EDF Expanded](https://physionet.org/content/sleep-edfx/) — Classic annotated PSG dataset, the default benchmark for staging algorithms.
- [CAP Sleep Database](https://physionet.org/content/capslpdb/) — Cyclic alternating pattern recordings with expert annotation, useful for arousal and microstructure work.
- [ISRUC-Sleep](https://sleeptight.isr.uc.pt) — Annotated PSG recordings from healthy subjects and patients, freely downloadable.
- [MIT-BIH Polysomnographic Database](https://physionet.org/content/slpdb/) — Older but well-annotated recordings combining EEG, ECG and respiration.

---

## Metrics and Definitions

The single biggest source of confusion in consumer sleep data is that different tools compute the same-named metric differently.

- [Oxygen Desaturation Index explained](https://www.nighttimecomfort.com/oxygen-desaturation/) — Why ODI3 and ODI4 give different numbers from identical data, how baseline choice changes event counts, and how to read an overnight oximetry trace.
- **AHI** — Apnea-Hypopnea Index. Events per hour of sleep. Depends entirely on the hypopnea definition used (1.1A vs 1.1B in the AASM manual), which is why numbers differ between labs.
- **RDI** — Respiratory Disturbance Index. AHI plus RERAs, so always greater than or equal to AHI.
- **RERA** — Respiratory Effort Related Arousal. The event type that defines UARS and is invisible to oximetry alone.
- **ODI** — Oxygen Desaturation Index. Desaturations per hour, defined against either a 3% or 4% drop from baseline.
- **Nadir SpO2** — Lowest sustained saturation in a recording. Sensitive to artifact, so minimum-duration rules matter.
- **T90 / T88 / T85** — Time spent below the named saturation, usually reported in minutes and as a percentage of valid recording time.
- **WASO** — Wake After Sleep Onset, total wake time between first sleep and final awakening.
- **Sleep Efficiency** — Total sleep time divided by time in bed.

---

## Standards and Clinical References

- [AASM Scoring Manual](https://aasm.org/clinical-resources/scoring-manual/) — The official rules for scoring sleep stages, arousals and respiratory events. The source of truth every other definition is derived from.
- [ICSD-3](https://aasm.org/clinical-resources/international-classification-sleep-disorders/) — International Classification of Sleep Disorders, the diagnostic reference.
- [PhysioNet Challenges](https://physionet.org/about/challenge/) — Annual open competitions, several on sleep staging and arousal detection, with published baselines.

---

## Hardware

### Pulse Oximeters
- **Wellue O2Ring / Checkme O2** — Ring-form continuous overnight oximeter with CSV export. The most commonly used consumer device for self-screening.
- **Wear O2 / PO1** — Cheaper alternative with similar continuous logging.
- **Go2Sleep** — Ring oximeter with its own cloud app.

### EEG
- [Hypnodyne ZMax](https://hypnodynecorp.com) — Consumer-priced EEG headband with genuine raw-signal access, the closest thing to research-grade in the consumer tier.
- **Muse S** — EEG headband marketed for meditation and sleep. Signal quality depends heavily on skin contact; verify before trusting staging output.
- [OpenBCI](https://openbci.com) — Open-source biosensing boards for building your own EEG rig.

### Rings, Watches and Straps
- **Oura Ring** — Sleep staging and temperature trends with a documented cloud API.
- **Samsung Galaxy Ring**, **Whoop**, **Apple Watch**, **Garmin** — Mainstream trackers with varying degrees of data export.

### Contactless
- **Withings Sleep Analyzer** — Under-mattress mat measuring movement, heart rate and breathing disturbances.
- **Emfit QS** — Ballistocardiography mat with detailed HRV output.

### Home Sleep Apnea Tests
- **WatchPAT One** — Peripheral arterial tonometry HSAT, disposable, prescription-dependent by region.
- **Belun Ring**, **Onera STS** — Newer HSAT devices with clinical validation studies.

---

## Vendor APIs

- [Oura API](https://cloud.ouraring.com/docs/) — Documented REST API for sleep, readiness and activity data.
- [Withings Developer API](https://developer.withings.com) — Includes sleep summaries and raw sleep data endpoints.
- [Fitbit Web API](https://dev.fitbit.com/build/reference/web-api/) — Sleep logs and stage-level data.
- [Garmin Health API](https://developer.garmin.com/gc-developer-program/health-api/) — Requires programme approval.

---

## Communities

- [Apnea Board](https://www.apneaboard.com/forums/) — The most technically serious patient forum for PAP therapy and machine data. Also hosts the OSCAR project.
- [Sleep as Android forum](https://forum.urbandroid.org) — Active Discourse community around sleep tracking hardware integration, sensor data and export formats.
- [r/CPAP](https://www.reddit.com/r/CPAP/), [r/SleepApnea](https://www.reddit.com/r/SleepApnea/), [r/UARS](https://www.reddit.com/r/UARS/) — Large patient communities; UARS in particular is where flow-limitation discussion happens.

---

## Contributing

Pull requests welcome. Please keep entries to one line, describe what the tool
actually does rather than what it claims, and prefer projects that are
maintained or at least documented. Commercial tools are acceptable where no open
alternative exists, but say so in the description.

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
