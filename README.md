# LUMEN — PON Optical Assurance (France)

A fleet-scale monitoring dashboard for a French passive optical access network (GPON
and XGS-PON). I built it as a portfolio piece, and its analytics view is driven by my
own research on upstream-delay prediction — that part isn't a mock-up. The
feature-importance figures and the dataset behind it are from my own work.

## The OPTIM view — what this project is really about

OPTIM is a model-driven view of upstream delay. The feature-importance bars are the
actual values from my research (FIR 81.9 %, DR 14.4 %), and the model is trained on
44,213 samples — one every 12 minutes, 88 KPIs per direction. The FMC view then puts
that model to work: a 24-hour chart of predicted vs measured upstream delay with the
model band drawn in, and a warning that fires when a congestion spike pushes delay
across the 1 ms bound. This is the thread that ties the dashboard to real analysis
rather than a wall of gauges.

## The rest of the dashboard

- **Fleet** — fleet-wide health across Île-de-France, Rhône-Alpes, PACA and Occitanie:
  availability against a 30-day SLA, ONTs online, active-alarm counts by severity,
  average optical Rx with headroom, live downstream throughput, and an Rx-power
  distribution across the full ONT base (median around −18.5 dBm). The OLT table
  drills into any of the 12 line terminals.
- **Topology** — the PON tree from OLT through the splitter to the ONTs, animating
  upstream TDMA bursts in grant order.
- **Alerts** — a live, rule-driven alarm feed across critical / major / minor: pre-FEC
  BER over 1e-4 held for 30 seconds, Loss of Signal, and the rest.

## Scale

12 OLTs, roughly 11,440 ONTs, four French regions.

## Tech

Single-file HTML / CSS / JS. Telemetry is simulated in the browser and updates live;
there is no backend or external service — open the file and it runs.

## A note on the data

The device readings and alarms are simulated for demonstration and are not wired to
production hardware. The alarm rules (pre-FEC BER > 1e-4, Loss of Signal, and so on)
are the real ones. The OPTIM figures, as noted above, come from my own dataset and
model.

## Background

I built this off my optical-access and fronthaul work (GPON / XGS-PON, DWDM, FTTA,
transmission) and the upstream-delay modelling behind the OPTIM view — to show a PON
assurance tool end to end, from fleet health down to a model that predicts something
real.
