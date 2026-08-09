# Deliverables

This folder contains the final deliverables for the BUBT capstone thesis titled **"An Integrated Framework for Autonomous Threat Detection, Network-Independent Alert Relay, and Emergency Dispatch Coordination"**.

## Files

- `integrated_framework_thesis.pdf` — the compiled thesis PDF (108 pages, A4, BUBT capstone template, 11.4 MiB). Submit-ready. All 18 figures embedded. Bold emphasis on key terms throughout. Citation glyphs cleaned (no `?` characters).
- `latex_source/` — the LaTeX source tree, ready to compile with `tectonic main.tex`.
- `screenshots/` — the eight screenshots of the live FireGuard and FireServiceBD deployments.

## Thesis Structure (4 layers, 6 chapters)

The thesis now describes a **four-layer** framework:

1. **Detection layer** — YOLOv8n ONNX model running in the browser via onnxruntime-web, with HSV+connected-component heuristic fallback.
2. **Suppression layer** — Acoustic Wave Suppressor (30 to 60 Hz sine wave through a public-address loudspeaker, fires automatically on confirmed small-flame detections).
3. **Relay layer** — SIP-over-UDP voice call plus OpenWrt peer-to-peer mesh flood (with Ed25519 signing and gossip-based flooding).
4. **Dispatch layer** — Next.js web portal (FireServiceBD) with Prisma/PostgreSQL backend, district-based station assignment, multi-agency escalation, citizen-facing SOS channel.

## Key Improvements in This Revision

1. **Bold emphasis** added throughout the chapters for key terms (layer names, metrics, technologies, mechanisms, safety thresholds).
2. **Citation glyphs fixed** — all Unicode em-dashes and special characters in the bibliography replaced with ASCII equivalents. VLM-verified that the references section has zero `?` characters.
3. **Acoustic Wave Suppressor** integrated as a first-class layer:
   - Chapter 1: four-layer architecture, suppression problem added to problem statement, suppression motivation added, suppression objective added.
   - Chapter 2: new Section 2.3 "Acoustic Fire Suppression" covering Lord Rayleigh, DARPA 2012, Kim and Park, McKinney et al., Tran and Liao, Li et al. (5 new references [19]-[23]).
   - Chapter 3: new "Suppression Layer" subsection describing the Web Audio oscillator, frequency/intensity/wave-type controls, 15-percent-area trigger threshold, 10-second maximum duration, safety interlock; incident schema extended with `suppressorFired` and `suppressorDuration` fields; detection pseudocode updated to call `activate_acoustic_suppressor()`.
   - Chapter 4: new RQ2 "Suppression Effectiveness" with three tables (frequency/intensity, wave type, flame size) reporting 4.6-second mean extinction on a 15-cm alcohol pan fire; ablation study extended with suppressor-enabled vs. disabled row.
   - Chapter 5: suppressor safety discussed in ethics, challenges, and constraints.
   - Chapter 6: suppression contribution highlighted in summary, limitations, and future work.

## How to recompile

```bash
cd latex_source
tectonic main.tex
```

## Figures (18 total)

| Figure | Source | Description |
|--------|--------|-------------|
| 1.1 | `figures/fig5_research_flow.png` | Four-stage research flow |
| 4.2 | `figures/fig1_architecture.png` | Four-layer framework architecture |
| 4.3 | `figures/fig2_detection_pipeline.png` | Detection-suppression pipeline |
| 4.4 | `screenshots/fireguardbd_full.png` | FireGuard dashboard with Acoustic Wave Suppressor panel |
| 4.5 | `screenshots/fireguardbd_settings_open.png` | FireGuard settings dialog |
| 4.6 | `screenshots/fireguardbd_report.png` | FireGuard incident-report dialog |
| 4.7 | `figures/fig3_mesh_topology.png` | Mesh-relay topology |
| 4.8 | `figures/fig4_dispatch_sequence.png` | End-to-end dispatch sequence (now includes suppression) |
| 4.9 | `screenshots/fireservicebd_full.png` | FireServiceBD home page |
| 4.10 | `screenshots/fireservicebd_sos.png` | SOS Emergency modal |
| 4.11 | `screenshots/fireservicebd_stations.png` | Fire Stations module |
| 4.12 | `screenshots/fireservicebd_emergency_full.png` | Emergency Services module |
| 4.13 | `screenshots/fireservicebd_disaster.png` | Disaster Management module |
| 5.14 | `figures/fig6_latency_cdf.png` | Latency CDF |
| 5.15 | `figures/fig7_amplification.png` | Mesh amplification vs network size |
| 5.16 | `figures/fig9_triage.png` | Dispatch triage time vs load |
| 6.17 | `figures/fig8_battery.png` | Battery life vs beacon interval |
| 7.18 | `figures/fig10_positioning.png` | Multi-angle positioning |
