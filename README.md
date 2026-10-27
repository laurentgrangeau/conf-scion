# Your LLMs work as a team, but who manages them? Orchestrate the chaos with Scion

45-minute technical conference slide deck (49 slides across 10 sections) powered by **[Reveal.js](https://github.com/hakimel/reveal.js/)** and written in Markdown (`slides.md`), presenting **[Google Cloud Scion](https://github.com/GoogleCloudPlatform/scion)** ([Documentation](https://googlecloudplatform.github.io/scion/overview/)).

## Abstract

> We’ve all written that slightly cobbled-together Python script at some point to get two LLMs to chat with each other. It’s fun locally, but for a real production pipeline, it’s a nightmare! The era of DIY GenAI is over: make way for distributed multi-agent systems.
>
> But when your agents generate, test, and execute code in parallel, who manages the chaos? How can you ensure security, isolate workspaces, and scale from your laptop to a Kubernetes cluster without rewriting everything?
>
> Discover Scion, Google Cloud’s open-source orchestration framework. Gone are the days of simple prompt engineering—we’re now entering the realm of true architecture with a Manager-Worker model.
>
> In this highly technical session, we’ll see how Scion containerizes and strictly isolates your agents’ execution. We’ll explore scaling to switch an execution graph from Docker to Kubernetes with a simple configuration change. We’ll also discuss built-in security, which is essential for controlling credential injection when dealing with AIs that dynamically generate code. Finally, a live demo will deploy a “task force” of specialized agents working in parallel to tackle a complex codebase.
>
> Come discover how to truly equip and operate your AI fleets!

---

## 45-Minute Talk Pacing & Structure (49 Slides)

| Section | Slides | Duration | Topics Covered |
| --- | --- | --- | --- |
| **Intro & Roadmap** | 2 | ~2 min | Title & 45-minute session breakdown |
| **Part 1: The DIY Multi-Agent Trap** | 4 | ~5 min | Why `while True` loops fail, `.git/index.lock` collisions, credential sprawl, Prompting $\rightarrow$ Systems Architecture |
| **Part 2: Scion Philosophy** | 5 | ~5 min | Agent Agnosticism, **Isolation over Constraints** (`--yolo` inside sandboxes), Multiplayer Collaboration, Kubernetes mental model |
| **Part 3: Core Concepts, Template Roles & Skills** | 12 | ~8 min | Deep dive into Groves (`.scion/`), **Template Roles** (`scion-agent.yaml`, `system-prompt.md`, `agents.md`, `home/`), **Agent Skills** (`SKILL.md`, progressive disclosure, `git-sandbox` platform skills), Agents, Runtime Brokers, Hub, Profiles, Messaging & Credentials, Manager-Worker graph |
| **Part 4: Harnesses & Worktrees** | 5 | ~5 min | 9 supported harnesses, deep dive on Google's built-in **`antigravity`** & **`gemini-cli`**, declarative `config.yaml` + `provision.py` bundles, unified capabilities, Git worktree + OCI + `tmux` isolation |
| **Part 5: Choosing a Run Mode** | 5 | ~4 min | **Workstation Mode**, **Single-Node Hosted Mode** (SQLite), **HA Hosted Mode on GCP**, comparison matrix |
| **Part 6: GCP HA Architecture** | 5 | ~4 min | Cloud Run + Cloud IAP + Cloud SQL (Postgres) + Cloud Filestore (RWX NFS) + GKE Autopilot, Two-Root Terraform (`shared-infra` & `hub`), switching via `--profile gcp-ha` |
| **Part 7: Security & Credentials** | 4 | ~4 min | Indirect prompt injection threat model, keyless **Vertex AI** via GKE Workload Identity, GCP Secret Manager, locked-down `scion-agent.yaml`, IAP & K8s `NetworkPolicy` |
| **Part 8: Live Demo on GCP HA** | 7 | ~6 min | 4-agent `antigravity` & `gemini-cli` Task Force on GKE Autopilot (`scion login --iap`, `scion start`, `scion list`, `scion msg`, `scion attach`, OTel events, automated branch merge) |
| **Part 9: Wrap-Up & Q&A** | 2 | ~2 min | Architecture comparison & official links |

---

## Running the Presentation

Because Reveal.js loads external Markdown (`slides.md`), serve the directory over a local HTTP server:

```bash
# Using Python 3
python3 -m http.server 8000

# Or using Node.js
npx serve -l 8000
```

Then open **[http://localhost:8000](http://localhost:8000)** in your browser.

---

## Presenter Shortcuts

| Key | Action |
| --- | --- |
| `→` / `↓` / `Space` | Next slide (horizontal / vertical) |
| `S` | Open **Speaker Notes** view (every slide includes detailed presenter notes) |
| `ESC` or `O` | Slide Overview mode |
| `F` | Fullscreen mode |
| `Alt + Click` | Zoom in on code blocks or architecture diagrams |
