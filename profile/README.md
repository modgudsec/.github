# Modgud

A local-first malware triage and reverse-engineering workbench that runs on your NPU. No sample, hash, or string ever leaves your machine.

> Móðguðr guards the bridge into the realm of the dead and lets no soul cross without stating its name and its business. Modgud does the same to every binary you hand it.

---

## Why it exists

SOC and DFIR analysts triage a lot of suspicious files, and cloud AI assistants are off the table for the job that would benefit most. You can't upload a possible malware sample, a customer artifact, or an internal hash to a third-party API. So the analysis that could be sped up by an assistant is exactly the analysis that has to stay offline.

Modgud runs the whole triage loop on one machine. Static analysis, community detection rules, reverse engineering, and an AI assistant that explains what it finds, with the AI running locally on an AMD Ryzen AI NPU. Nothing is sent anywhere. The tool works with the network cable unplugged.

## What it does

- **Expert static triage.** Parses PE, ELF, and Mach-O; maps sections and entropy; extracts and categorizes strings (ASCII and UTF-16); surfaces network indicators corroborated by import capabilities; tags MITRE ATT&CK techniques.
- **Community rules, first pass.** Scans with YARA Forge out of the box. Maps inferred behaviors to the Sigma rules that would catch them at runtime, and shows where coverage is missing.
- **Reverse engineering built in.** Bundles Rizin and the rz-ghidra decompiler. Browse functions, read pseudo-C, jump from a suspicious string to the code that uses it. No separate install.
- **A local analyst, not a cloud one.** An on-device LLM summarizes findings, explains a function, and drafts detection rules, grounded only in what the deterministic analysis found. It runs on your NPU, so your CPU stays free for the heavy work.
- **Offline by design.** Network clients are loopback-only. There is no telemetry and no code path that reaches a remote service. You can verify this from how the tool behaves, not just from this README.

## Status

Modgud is in active development as a solo project. The current release covers static triage, rule scanning, and reverse engineering. Dynamic analysis (via CAPE) and a local KQL detection-authoring module are on the roadmap.

Issues and feature requests are welcome through GitHub Issues. This is a one-person project, so they're reviewed periodically rather than in real time.

## Staying updated

Watch the project or give it a star to follow along — releases and write-ups on how the harder parts work land here first.

## License

Modgud's core is proprietary; the released binary is covered by its EULA. The SDK, schemas, documentation, and community rule repositories are open under permissive licenses. See each repository for details.
