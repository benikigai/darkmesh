# DarkMesh

DarkMesh is Altiair's live demo site for tactical edge mesh coordination in DDIL environments. It shows how Hawkeye-style sensors, Palantir Foundry, CASK-shaped mission data, and decentralized local nodes fit together for resilient human-reviewed cueing.

- Site: [DarkMesh.us](https://darkmesh.us)
- Project repo: [github.com/digitalnomd/altiair](https://github.com/digitalnomd/altiair)
- Team: Altiair (Sarah Hatcher, Benjamin Shyong, Rob Grossman, Katherine Lambert)
- Implementation snapshot: [implementation/altiair](implementation/altiair), imported from `digitalnomd/altiair` `origin/main` at `5f668eb`.

## What the site shows

- Mission premise and military benefit.
- Where Hawkeye, Foundry, CASK, and DarkMesh sit in the workflow.
- Live-demo sequence: mission directive, Foundry context, CASK deployment, node leases, sensor fan-in, local model fusion, coordinator failover, Foundry writeback.
- SSH-triggered node-dropout narrative so the Pi bench can stay powered while the coordinator/failover proof remains live.
- UML-style architecture view with policy gates, encrypted payloads, signed records, replicated ledger, and Rust durable-agent path.
- Rob's latest product-flow chart and pitch artifacts from the implementation repo.

## Hardware image

The Raspberry Pi / Jetson setup photo should be committed at [assets/hardware/darkmesh-pis.jpg](assets/hardware/darkmesh-pis.jpg). The site has a dedicated hardware section that uses this image when present, while the demo narrative makes clear the Pis remain on the bench and are accessed by SSH.

## Government opportunity alignment

DarkMesh maps to current DoD demand signals around decentralized AI coordination, DDIL swarm/robotic command, NGC2 common data layers, Open DAGIR interoperability, and CJADC2 edge sensor fusion:

- DARPA special notice: [DARPA-SN-26-72, Decentralized Artificial Intelligence through Controlled Emergence (DICE)](https://www.darpa.mil/research/programs/decentralized-artificial-intelligence-through-controlled-emergence)
- CDAO call for white papers: [Swarm Forge Prototype Project](https://www.tradewindai.com/swarm-forge)
- Army OTA/CSO acquisition pathway: [Next Generation Command and Control (NGC2) prototype award](https://www.army.mil/article-amp/287180/army_announces_next_generation_command_and_control_ngc2_prototype_award)
- CDAO acquisition approach: [Open DAGIR](https://www.ai.mil/Latest/News-Press/PR-View/Article/4026085/cdao-highlights-progress-in-scaling-data-and-ai-capabilities-at-six-month-mark/)
- Army budget justification: [PB 2026 NGC2 Prototyping](https://www.asafm.army.mil/Portals/72/Documents/BudgetMaterial/2026/Discretionary%20Budget/rdte/RDTE%20-%20Vol%202%20-%20Budget%20Activity%204B.pdf)
- CJADC2 technical requirement framing: [AI-/ML-based sensor fusion at the edge](https://militaryembedded.com/ai/machine-learning/cjadc2-interoperability-ai-ml-based-sensor-fusion-at-the-edge)

See [AGENTS.md](AGENTS.md) and [CLAUDE.md](CLAUDE.md) for the full evaluator-facing handoff, thread-derived demo decisions, and Hawkeye / Palantir Foundry / CASK integration story.

## Local preview
```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Auto-deployed via Vercel on push to `main`.
