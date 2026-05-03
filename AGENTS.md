# Codex Handoff For DarkMesh

This repo is the public Vercel site for `DarkMesh` by team Altiair. The deeper implementation repo is `github.com/digitalnomd/altiair`; this repo should stay focused on the public demo surface, pitch artifacts, screenshots, and concise technical handoff material.

The implementation snapshot now lives in `implementation/altiair`, imported from `digitalnomd/altiair` `origin/main` at `5f668eb`. Keep it as the code-bearing proof path inside the DarkMesh repo so the website, pitch, diagrams, node API, Rust agent, Pi scripts, CASK records, Foundry boundary, and local LLM workflow are all reviewable together.

## Core Problem Statement

Modern tactical teams are becoming sensor-rich but coordination-poor at the edge. In a DDIL environment, one operator may have visual context, another may have microphone or acoustic context, another may have RFID/RF/proximity context, and command systems may have Foundry mission intelligence. The open military-relevant problem is turning those fragmented, low-bandwidth, partially trusted observations into one explainable, human-reviewed operating cue without depending on cloud connectivity, a single command node, or raw-stream backhaul.

DarkMesh addresses that gap as a decentralized edge coordination layer:

- Hawkeye-style systems are the sensor/visual lane.
- Palantir Foundry is the governed mission context, commander visibility, audit, and after-action layer.
- CASK is the mission data contract and ontology shape that can run locally and sync back.
- DarkMesh is the local coordination mesh: sensor normalization, compact evidence sharing, replicated state, coordinator election, local model reasoning, and queued Foundry reconciliation.

Do not describe DarkMesh as a weapons system, autonomous engagement system, or target-prosecution system. It is evidence fusion, resilient coordination, human-review cueing, and after-action synchronization.

## Exact Government Opportunity Alignment

Use the formal vehicle type for each source: DARPA special notice, CDAO call for white papers, Army OTA/CSO acquisition pathway, CDAO acquisition approach, Army budget justification, and CJADC2 technical requirement framing. The exact sources relevant to DarkMesh are:

| Source | Exact vehicle / opportunity | Why it matters for DarkMesh |
| --- | --- | --- |
| DARPA DICE | **DARPA-SN-26-72**, `Decentralized Artificial Intelligence through Controlled Emergence (DICE)` Proposers Day. Published April 28, 2026; deadline May 19, 2026; Proposers Day May 29, 2026. Source: https://www.darpa.mil/research/programs/decentralized-artificial-intelligence-through-controlled-emergence | DICE is directly aligned with decentralized coordination, local inference control, resilience to agent loss/compromise, peer-to-peer coordination, and contested environments. DarkMesh is a working hackathon analogue of that problem space, but does **not** claim to be a DICE performer or a deployed autonomous system. |
| CDAO / OSW Swarm Forge | **Swarm Forge Prototype Project**, Call for White Papers. Issuing office: CDAO. Date of issuance March 16, 2026; proposal due date April 17, 2026. Source: https://www.tradewindai.com/swarm-forge | Swarm Forge asks for command, control, and collaboration of autonomous systems in DDIL conditions, with interest in counter-UAS, distributed communications swarms, and deception/information operations. DarkMesh fits as an enabling edge coordination/data layer, not as an autonomous strike or full swarming solution. |
| Army NGC2 | Army **Next Generation Command and Control (NGC2)** prototype OTA/CSO pathway. The July 2025 Army release describes integrated C2 across hardware, software, and applications through a common integrated data layer, plus a CSO for additional vendors. Source: https://www.army.mil/article-amp/287180/army_announces_next_generation_command_and_control_ngc2_prototype_award | DarkMesh is a small edge-node demonstration of common-data-layer logic: compact evidence records, local state, and Foundry/CASK writeback rather than raw-stream dependence. |
| CDAO Open DAGIR | **Open Data and Applications Government-owned Interoperable Repositories (Open DAGIR)** acquisition approach. Source: https://www.ai.mil/Latest/News-Press/PR-View/Article/4026085/cdao-highlights-progress-in-scaling-data-and-ai-capabilities-at-six-month-mark/ | Open DAGIR emphasizes rapid procurement/integration and interoperability across DoD digital capabilities from strategic C2 to the tactical edge. DarkMesh should be framed as interoperable with Foundry/CASK rather than a closed replacement. |
| Army PB 2026 NGC2 budget justification | Army PB 2026 RDT&E, `Next Generation Command and Control (NGC2) Prototyping`, including common data fabric, third-party data integration, and advanced C2 prototyping. Source: https://www.asafm.army.mil/Portals/72/Documents/BudgetMaterial/2026/Discretionary%20Budget/rdte/RDTE%20-%20Vol%202%20-%20Budget%20Activity%204B.pdf | This supports the military relevance of common data fabric, third-party data integration, and modular C2 experimentation. DarkMesh's CASK records and node API are the demo's miniature version of that integration problem. |
| CJADC2 edge-fusion framing | CJADC2 technical requirement framing: Military Embedded Systems article, `CJADC2 interoperability: AI-/ML-based sensor fusion at the edge`, November 25, 2024. Source: https://militaryembedded.com/ai/machine-learning/cjadc2-interoperability-ai-ml-based-sensor-fusion-at-the-edge | Supports the requirement that sensor data be processed rapidly, harmonized into common operational pictures, processed at the tactical edge, standardized, secured, stored locally, and forwarded when connectivity allows. |

When summarizing this in public copy, say: "DarkMesh maps to current DoD demand signals around decentralized AI coordination, DDIL swarm/robotic command, NGC2 common data layers, Open DAGIR interoperability, and CJADC2 edge sensor fusion."

## Thread-Derived Demo Decisions

- Product name: `DarkMesh`.
- Team name: `Altiair`.
- Existing implementation/hardware identifiers may still say `Altiair` or `altiair-*`; do not rename those in copied code unless the hardware scripts are deliberately migrated.
- The public demo should be live and website-led, not a filmed-only video.
- The demo should walk through: mission directive, Foundry context, CASK deployment, node leases, sensor evidence, local model fusion, coordinator failover, continued mission state, and Foundry writeback.
- The failure beat should be SSH-triggered node dropout/service stop, not physically unplugging every Raspberry Pi. Keep the hardware powered and show a Pi/Jetson bench photo.
- Pi 5 camera is an upgrade lane, not load-bearing for the noon demo. Jetson/Hawkeye visual lane plus mock/fixture camera events can carry the visual track.
- The Vercel static site can show the narrative and fixture-backed dashboard. The true hardware path runs through the local node API on the Altiair LAN.
- Preserve privacy: do not capture random desktop windows, personal browser state, credentials, private Foundry URLs, raw private media, or personal data.

## Hawkeye / Foundry / CASK / DarkMesh Fit

The product story must make the integration boundaries clear:

- **Hawkeye** contributes visual/sensor observations. In the demo, Hawkeye can be represented by Jetson visual track events, a camera adapter, or the deterministic visual fixture.
- **Palantir Foundry** contributes governed mission context and receives the after-action/commander-visible record. Foundry is the cloud-side system of record, not the thing DarkMesh replaces.
- **CASK** is the data contract: mission instruction, deployment order, node leases, sensor events, location fixes, insight drafts, policy gates, coordinator directives, ledger state, and sync receipts.
- **DarkMesh** is the local coordination runtime: it normalizes sensor events into compact CASK records, replicates the mission ledger, elects/degrades coordinator authority, uses local models for explanation, and queues/executes Foundry writeback.

In one line: Hawkeye sees, Foundry governs and records, CASK shapes the mission data, DarkMesh keeps the edge nodes coordinated when the network or a node fails.

## Military-Relevant Use Cases

Use safe, controlled, human-reviewed language:

- Counter-UAS cueing: combine visual, acoustic, RFID/RF/provider-style proximity, node health, and Foundry context to estimate a drone-class cue and likely controller-associated zone for human review.
- Deception and spoofing review: flag stale or conflicting RFID/Wi-Fi/provider-style claims by comparing them against independent camera/audio/mesh evidence.
- Unmanned surveillance handoff: drones, Hawkeye kits, vehicles, Pi nodes, and Jetson nodes share compact CASK records so a useful cue survives node or uplink loss.
- Node dropout continuity: after one node goes dark, replicated records and coordinator election keep the mission picture available in degraded mode.
- Mission-critical notification: a tablet or Pi-hosted display surfaces the highest-priority cue with evidence IDs, confidence, source nodes, contradictions, and required review state.
- Foundry reconciliation: when any gateway regains connectivity, local CASK records, coordinator terms, policy gates, operator acknowledgements, and after-action data sync back to Foundry.

Avoid claims about pursuit, capture, kinetic engagement, autonomous force, or identifying private individuals. The demo can discuss an authorized training object, controlled drone-class cue, tagged asset, or controller-associated zone.

## Technical Architecture To Preserve

The source implementation in `digitalnomd/altiair` includes:

- Node API exposing `/dashboard`, `/health`, `/topology`, `/peers`, `/gateway`, `/mission-continuity`, `/gossip/world`, `/mission/instructions/latest`, `/mission/deployment/latest`, `/mission/timeline`, `/foundry/intelligence`, `/foundry/sync/latest`, `/coordinator/latest`, `/bundles/pending`, `/ledger`, `/replication/latest`, `/insights/latest`, `/tag-plan/latest`, `/instructions/latest`, `/stream/status`, and `/stream/records`.
- One-command demo path: `npm run demo:start -- --include-failure-step`.
- CASK-shaped mission deployment: mission text becomes policy decision, deployment order, node leases, timeline, and local instructions.
- Sensor ingest contract: `POST /sensor-events` accepts camera, microphone/audio, RFID, provider-style location, and node-health events.
- Local model path: approved local Gemma/Ollama-style inference path, with deterministic mock fallback for the public fixture.
- Replicated ledger and gossip-derived world state across nodes.
- Current-term singleton coordinator election, with observe-only degraded state if quorum is not available.
- Foundry/OSDK read and writeback boundary: current live path can write available GPS/location slice; full CASK bundle queues until matching Foundry ontology actions exist.
- Security path: API token support, AES-256-GCM app payload envelopes, Ed25519 signed durable records, Rust durable-agent path, policy-state allowlists, and fail-closed validation.

## Public Site Structure

Current files in this repo:

- `index.html`: public website and demo narrative.
- `styles.css`: full responsive DarkMesh UI styling.
- `app.js`: fixture/live-dashboard normalization and rendering logic.
- `data/demo-state.json`: sanitized fixture state.
- `assets/pitch/*.svg`: pitch diagrams.
- `assets/hardware/`: public slot for the Raspberry Pi / Jetson bench photo.
- `screenshots/*.png`: captured proof screenshots.
- `pitch.md` and `pitch2.md`: pitch narrative drafts.
- `pitch_final.md`: latest imported final pitch draft.
- `docs/demo-flow-chart.md`: editable flow-chart source.
- `docs/product-flow-chart.md`: Rob's latest product-flow chart source.
- `implementation/altiair/`: imported implementation repo snapshot with the node API, CASK/Foundry code, Rust durable agent, Pi/Jetson scripts, local LLM path, and demo launcher.
- `vercel.json`: static-site security headers.

If adding a hardware bench photo, place it at `assets/hardware/darkmesh-pis.jpg`. The CSS already references that path and falls back to a generated DarkMesh surface if the file is absent.

## Vercel / Domain Notes

The target site is `https://darkmesh.us`. DNS currently points at Vercel. If `darkmesh.us` returns `DEPLOYMENT_NOT_FOUND`, the GitHub repo has been pushed but the Vercel project/domain is not yet attached to a deployment. Resolve by logging into Vercel CLI or connecting `benikigai/darkmesh` to the `darkmesh.us` Vercel project in the dashboard.

Local preview:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Claim Boundaries

Safe claims:

- Hackathon prototype.
- Live website-led demo.
- Commodity Pi/Jetson edge nodes.
- Local-first sensor evidence fusion.
- Foundry/CASK-shaped interoperability.
- Human-reviewed cueing.
- Node-loss resilience demonstration.
- Security-conscious demo baseline.

Do not claim:

- Production certification, RMF/ATO, CMMC certification, or operational approval.
- Real carrier-grade LTE/5G integration unless it exists.
- Real L3Harris integration.
- Autonomous engagement, kill-chain automation, target prosecution, capture, or pursuit.
- Palantir, Army, or DARPA endorsement. Informal positive feedback can be described only as informal feedback.

## Recommended Validation

For this static repo:

```bash
python3 -m http.server 8000
curl -I http://127.0.0.1:8000/
curl -I http://127.0.0.1:8000/assets/pitch/demo-flow-chart.svg
curl -I http://127.0.0.1:8000/data/demo-state.json
git diff --check
```

For the implementation repo, use the existing checks there:

```bash
npm run build
npm run security:smoke
npm run workflow:smoke
npm run demo:start -- --once --include-failure-step
```
