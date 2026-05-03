# Claude Handoff For darkmesh

Use this file as the technical and narrative source of truth when improving the public `darkmesh` site, pitch copy, or evaluator-facing explanation.

## One-Sentence Product Definition

`darkmesh` by Altair is a decentralized edge-coordination layer that fuses local sensor evidence, coordinates surviving nodes, and syncs CASK-shaped mission records back to Palantir Foundry when connectivity allows.

## The Open Military Problem

The relevant open problem is not simply "detect a drone." The harder problem is resilient edge intelligence under DDIL conditions:

- Sensors are distributed across people, robots, small devices, vehicles, and local kits.
- Each sensor sees only a fragment: vision, audio, RFID/RF/proximity, location, human report, or command context.
- Raw sensor streams are too expensive or impossible to backhaul reliably.
- Cloud and command systems may be unreachable.
- A single coordinator, gateway, or display may fail.
- Operators still need one useful, explainable, current, human-reviewed cue.

darkmesh demonstrates the missing layer between sensors and command software: local evidence normalization, compact record sharing, local model-assisted explanation, coordinator election, replicated mission state, and Foundry/CASK reconciliation.

## Exact Government Opportunity Sources

Use these exact references and name the source vehicle precisely.

1. **DARPA DICE, DARPA-SN-26-72**  
   Title: `Decentralized Artificial Intelligence through Controlled Emergence (DICE)` Proposers Day.  
   Published: April 28, 2026. Deadline: May 19, 2026. Proposers Day: May 29, 2026.  
   Source: https://www.darpa.mil/research/programs/decentralized-artificial-intelligence-through-controlled-emergence  
   Fit: decentralized coordination, local inference control, peer-to-peer agent teams, resilience to failure/compromise, contested environments, and commander-aligned behavior. darkmesh is a practical demo analogue, not a DICE contract claim.

2. **CDAO / OSW Swarm Forge Prototype Project CFWP**  
   Issuing office: Chief Digital Artificial Intelligence Office. Date of issuance: March 16, 2026. Proposal due: April 17, 2026.  
   Source: https://www.tradewindai.com/swarm-forge  
   Fit: command, control, and collaboration of autonomous systems; DDIL operation; counter-UAS; distributed communications swarms; deception/information operations. darkmesh fits as edge coordination/data fabric for human-reviewed cueing, not as a full autonomous swarm package.

3. **Army NGC2 prototype OTA / CSO acquisition path**  
   Source: https://www.army.mil/article-amp/287180/army_announces_next_generation_command_and_control_ngc2_prototype_award  
   Fit: integrated/scalable C2 suite across hardware, software, and applications through a common integrated data layer. The Army release also notes additional vendor competition through a CSO. darkmesh shows commodity edge nodes writing and sharing interoperable mission records.

4. **CDAO Open DAGIR**  
   Source: https://www.ai.mil/Latest/News-Press/PR-View/Article/4026085/cdao-highlights-progress-in-scaling-data-and-ai-capabilities-at-six-month-mark/  
   Fit: competitive acquisition for interoperable DoD data/app repositories, spanning strategic C2 to tactical edge. darkmesh should be framed as interoperable with Foundry/CASK, not as a silo.

5. **Army PB 2026 NGC2 Prototyping budget justification**  
   Source: https://www.asafm.army.mil/Portals/72/Documents/BudgetMaterial/2026/Discretionary%20Budget/rdte/RDTE%20-%20Vol%202%20-%20Budget%20Activity%204B.pdf  
   Fit: common data fabric, third-party data integration, modular C2, cloud/AI/cybersecurity-enabled C2. darkmesh maps to the edge proof of that common data fabric.

6. **CJADC2 edge sensor-fusion technical requirement framing**  
   Source: https://militaryembedded.com/ai/machine-learning/cjadc2-interoperability-ai-ml-based-sensor-fusion-at-the-edge  
   Fit: edge processing, data standardization, security, scalability, storing data at the edge and forwarding when connectivity allows. Use as a technical requirement and rationale source.

Best compact formulation: "darkmesh aligns with DICE-style decentralized AI coordination, Swarm Forge DDIL command/collaboration needs, NGC2 common-data-layer modernization, Open DAGIR interoperability, and CJADC2 edge sensor-fusion requirements."

## Where Existing Tech Fits

Use this framing:

- **Hawkeye**: visual or sensor lane. It contributes observations such as drone-class visual tracks, camera frames, or visual confidence.
- **Palantir Foundry**: governed mission context and commander-side system of record. It provides mission data, policy context, asset/tag mappings, audit trail, and after-action replay.
- **CASK**: mission ontology and data contract. CASK-shaped records let the same evidence bundle exist locally at the edge and later reconcile into Foundry.
- **darkmesh**: decentralized edge runtime. It runs when the network is degraded, keeps the mesh coordinated, elects or degrades coordinator authority, and presents the operator with a cue instead of raw feeds.

Do not pitch darkmesh as replacing Foundry, Hawkeye, radios, IVAS, Nett Warrior, or certified tactical systems. Pitch it as a low-cost, interoperable edge layer beside them.

One-line integration story: Hawkeye sees, Foundry governs and records, CASK shapes the mission data, and darkmesh coordinates the edge when the uplink or a node fails.

## Demo Flow

The website should make this path obvious:

1. Mission directive appears in the browser.
2. Foundry/Atlas context and operator intent become a CASK deployment order.
3. CASK creates node leases and per-node responsibilities.
4. Edge nodes emit compact evidence:
   - RFID/provider-style proximity.
   - Hawkeye/camera/visual track.
   - Microphone/acoustic context.
   - Node-health and mesh state.
5. Local model path summarizes evidence into an explainable cue.
6. Current-term coordinator publishes per-node instructions.
7. A node dropout is triggered over SSH so the hardware bench remains stable.
8. The dashboard shows degraded state, coordinator transition or observe-only mode, preserved evidence, and continued cue visibility.
9. Foundry writeback is accepted if a gateway is connected or queued if offline.

## Use Cases To Emphasize

Keep all examples controlled, defensive, and human-reviewed:

- Counter-UAS cueing for a drone-class event.
- Controller-associated zone estimation for review, not targeting.
- RFID/Wi-Fi/provider-style proximity as a coarse signal, not carrier-grade truth.
- Spoofing/deception detection by cross-checking stale or conflicting signals.
- Node-loss and uplink-loss continuity.
- Shared evidence across drones, Hawkeye kits, Pi nodes, Jetson nodes, and operator displays.
- Mission-critical tablet/Pi notification with evidence provenance and uncertainty.
- After-action record sync to Foundry.

Avoid: autonomous engagement, pursuit, capture, restraint, harm, kill-chain automation, or identifying private persons.

## Technical Details Worth Preserving

The implementation repo has already built the important path:

- TypeScript node API for health, peers, gateway selection, congestion, CASK bundle queue, mission deployment, local model insight, tag/cue plan, replication, ledger, and dashboard snapshot.
- Deterministic mock scenario matching the live adapter contract.
- Live sensor event adapter contract for camera, microphone, RFID, provider-style location, and node health.
- Local LLM path through approved local models such as Gemma/Ollama, with deterministic fallback for demos.
- CASK ontology proposal and local deployment model.
- Foundry OSDK read/write boundary, with current live write slice and queued full-bundle path.
- Gossip world state and Raft-style singleton coordinator election.
- Replicated mission ledger so a failed node does not own the only copy of the evidence.
- Always-on Kafka-shaped stream envelope for future broker/Foundry forwarding.
- Security baseline: API token, AES-256-GCM app envelopes, Ed25519 durable records, Rust durable agent, policy-state validation, and fail-closed behavior.

The public repo is a static Vercel shell around this deeper implementation. It should not duplicate secrets, raw logs, Foundry URLs, private access details, or private media.

## Safe Pitch Language

Strong language to use:

- "sensor coordination under constraint"
- "human-reviewed cue"
- "controller-associated zone"
- "degraded but useful mission picture"
- "compact CASK evidence records"
- "local-first, Foundry-compatible"
- "survives node and uplink loss"
- "not one smarter sensor, but coordination across weak signals"

Language to avoid:

- "shoot/no-shoot decision" unless explicitly framed as not produced by the system.
- "targeting" unless replaced with "cueing" or "human-reviewed zone estimate."
- "enemy operator identification" unless replaced with "controlled training controller-associated zone."
- "autonomous action," "kill chain," "capture," "pursuit," "engage," "neutralize," or similar.

## Deployment Notes

The site repo is `benikigai/darkmesh`; the deeper project repo is `digitalnomd/altiair`.

Target domain: `darkmesh.us`.

If Vercel returns `DEPLOYMENT_NOT_FOUND`, GitHub has been pushed but Vercel project/domain linking still needs to be fixed by a Vercel-authenticated user.

Local static preview:

```bash
python3 -m http.server 8000
```

Implementation repo live demo proof:

```bash
npm run demo:start -- --include-failure-step
```

Use SSH-triggered failure for the pitch rather than physically power-cycling Pi nodes. The point is the coordinator/failover proof, not risking the power/network bench.
