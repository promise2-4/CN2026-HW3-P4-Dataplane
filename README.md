# P4 Data Plane — Homework Starter

Starter environment for a Computer Networks assignment at Sharif University of Technology. It provides Docker, P4/BMv2, Mininet, a six-host topology, a warmup P4 program, and scripts for compiling, running, capturing packets, and cleanup.

**This is not a completed P4 router or firewall.** Students implement forwarding, filtering, classification, and QoS logic in their own assignments.

## Quick start

```bash
git clone https://github.com/promise2-4/CN2026-HW3-P4-Dataplane.git
cd CN2026-HW3-P4-Dataplane
git checkout v1.0
docker buildx build --platform linux/amd64 --load -t p4-dataplane-hw .
docker run --rm -it --platform linux/amd64 --privileged -v "$PWD":/workspace p4-dataplane-hw
```

Inside the container:

```bash
docker/verify-env.sh
starter/scripts/compile.sh starter/p4/warmup_example.p4
starter/scripts/smoke_test.sh
starter/scripts/run_mininet.sh starter/p4/warmup_example.json
```

The smoke test checks the development environment, not the full homework behavior. `--privileged` is required for Mininet's networking namespaces and virtual interfaces. On Apple Silicon, the amd64 image runs through emulation.

## Included

- `Dockerfile` and `docker/`: development environment and checks
- `starter/p4/`: minimal warmup program
- `starter/topology/`: one BMv2 switch and six hosts
- `starter/scripts/`: compile, run, capture, smoke test, cleanup

For final homework requirements, use the course handout. The starter alone does not include route tables, a finished IPv4 pipeline, or tested firewall/QoS implementations.
