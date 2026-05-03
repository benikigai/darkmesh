# darkmesh

darkmesh is Altair's live demo site for tactical edge mesh coordination in DDIL environments. It shows how Hawkeye-style sensors, Palantir Foundry, CASK-shaped mission data, and decentralized local nodes fit together for resilient human-reviewed cueing.

- Site: [darkmesh.us](https://darkmesh.us)
- Project repo: [github.com/digitalnomd/altiair](https://github.com/digitalnomd/altiair)
- Team: Altair (Sarah Hatcher, Benjamin Shyong, Rob Grossman, Katherine Lambert)

## What the site shows

- Mission premise and military benefit.
- Where Hawkeye, Foundry, CASK, and darkmesh sit in the workflow.
- Live-demo sequence: mission directive, Foundry context, CASK deployment, node leases, sensor fan-in, local model fusion, coordinator failover, Foundry writeback.
- SSH-triggered node-dropout narrative so the Pi bench can stay powered while the coordinator/failover proof remains live.
- UML-style architecture view with policy gates, encrypted payloads, signed records, replicated ledger, and Rust durable-agent path.

## Local preview
```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Auto-deployed via Vercel on push to `main`.
