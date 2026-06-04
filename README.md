# robomate.mp4

robomate.mp4 is a research and development monorepo for multimodal robotics data collection, analysis, and inference. The repository contains tools, inference code, dataset manifests, and a web frontend used across experiments and mobile/iOS integrations.

## Project overview

- Purpose: collect, process, and analyze sensor/video data from robotic or mobile captures, run inference pipelines (pose, detection, action segmentation), and provide web-based tools for visualization and dataset management.
- Scope: dataset ingestion, preprocessing pipelines, inference runtimes (Modal/Modal Inference), evaluation tooling, and a Next.js frontend for management and visualization.

## High-level architecture

- `backend/` – core Python services, orchestrator, analyzers, and integration with Supabase and Modal inference runners.
- `modal-inference/` & `modal_inference/` – inference entrypoints and helper scripts used when running on Modal or cloud instances.
- `web/` – Next.js application for dataset browsing, results visualization, and lightweight management UIs.
- `iosApp/` & `DataCollector/` – iOS project scaffolding and capture app sources (device-specific capture helpers, configuration files).
- `playground/`, `mediapipe/`, `video_eval/`, `yolo/` – experiments, evaluation code, and supporting scripts for different models and approaches.

## Repo structure (short)

- `backend/` – Python packages, `pyproject.toml`, `modal_app.py`, orchestration and analyzers.
- `web/` – Next.js app, frontend components, scripts and deployment config.
- `iosApp/` – iOS application sources and example config for mobile capture.
- `playground/`, `mediapipe/`, `video_eval/`, `yolo/` – experimental modules and utilities.
- `supabase/` – Supabase functions and DB migration scripts used by backend services.
- `tests/` – integration and unit tests for core Python packages.

## Getting started (developer)

Prerequisites

- Python 3.10+ (or the version targeted by each subpackage's `pyproject.toml`)
- Node.js 18+ and npm or pnpm for the `web/` app
- Optional: Xcode for iOS development

Basic setup

1. Create a Python virtual environment and activate it (example):

```bash
python -m venv .venv
source .venv/bin/activate
```

2. Install Python dependencies per subproject. Many subpackages use `pyproject.toml`; install with pip or your preferred tool. Example for the root `backend` package:

```bash
cd backend
pip install -e .
# or: pip install -r requirements.txt if present
```

3. Install and run the web app locally:

```bash
cd web
npm install
npm run dev
```

4. Run tests (example):

```bash
# run pytest for backend tests
cd backend
pytest -q

# or at repo root to run multiple test suites if configured
pytest -q
```

Notes on subprojects

- Many folders contain their own `pyproject.toml` or `tests/`. Prefer installing and testing per-subproject to avoid cross-dependency issues.
- The `modal_app.py` files are entrypoints for running tasks on Modal or cloud instances; review the `modal_*` and `modal-inference` folders before running on remote infra.

## Common tasks

- Start the Next.js frontend: `cd web && npm run dev`
- Start a local backend worker (example): `cd backend && python modal_app.py` (depends on the entrypoint)
- Run a specific analyzer or evaluation script: `python -m backend.analyzers.gemini_eval` (adjust import path as needed)

## Development workflow and conventions

- Keep each subpackage's dependencies isolated. Use virtual environments per developer or a single workspace venv when convenient.
- Tests live alongside packages; run them for the package you are editing.
- Use `pre-commit` or linters as preferred; none are enforced by this repo by default.

## Contributing

1. Open an issue describing the change or feature.
2. Create a branch: `git checkout -b feat/short-descriptive-name`.
3. Add tests where applicable and run the test suites.
4. Open a pull request describing motivation and changes.

## Pushing this repository

This repository can be pushed to your remote Git host. If you want me to push changes to a remote named `robomate.mp4`, please provide the remote URL (HTTPS or SSH) and confirm that you want me to push. Example remote URLs:

- SSH: `git@github.com:<username>/robomate.mp4.git`
- HTTPS: `https://github.com/<username>/robomate.mp4.git`

I will not push without that URL and your confirmation.

## License & contact

Add a `LICENSE` file to declare the project license. If you want a recommendation, I can add an MIT or Apache-2.0 license for you.

For questions or support, open an issue in this repository or contact the maintainers.

---
Updated README to provide a developer-focused overview and instructions.
