# Qoro Quantum

Software infrastructure for hybrid quantum-classical workloads across HPC clusters, simulators, and quantum hardware.

## Core Projects

### [Maestro](https://github.com/QoroQuantum/maestro)
High-performance quantum circuit simulator supporting statevector, MPS, stabilizer, density matrix, tensor network, and Pauli propagation backends across CPUs, NVIDIA GPUs, and MPI clusters. Up to 100× faster than Qiskit Aer 120–200 qubit MPS workloads ([benchmarks](https://qoroquantum.github.io/maestro/benchmarks.html) · [docs](https://qoroquantum.github.io/maestro/)).

```bash
pip install qoro-maestro
```

**Ecosystem adapters:** [`qiskit-maestro`](https://github.com/QoroQuantum/qiskit-maestro) · [`pennylane-maestro`](https://github.com/QoroQuantum/pennylane-maestro) · [`deltakit-maestro`](https://github.com/QoroQuantum/deltakit-maestro) · [`qoro-pyscf`](https://github.com/QoroQuantum/qoro-pyscf) · [`maestro-demos`](https://github.com/QoroQuantum/maestro-demos)

---

### [Divi](https://github.com/QoroQuantum/divi)
Python framework for building and scaling hybrid quantum programs — problem-to-circuit generation, automatic batching and partitioning, error mitigation (ZNE, QuEPP), and backend-agnostic execution across Maestro, HPC clusters (QRMI), and quantum hardware ([docs](https://divi.readthedocs.io) · [quickstart](https://divi.readthedocs.io/en/latest/quickstart.html)).

```bash
pip install qoro-divi
```

---

### HPC Integration
Tooling for running Maestro as a managed service on HPC nodes and scheduling it alongside classical workloads:

- [`maestro-local-server`](https://github.com/QoroQuantum/maestro-local-server) — Node-level simulation daemon with Unix socket sessions and MPI worker isolation
- [`maestro-spank-plugin`](https://github.com/QoroQuantum/maestro-spank-plugin) — Slurm SPANK plugin for configuring simulations via job options
- [`qrmi`](https://github.com/QoroQuantum/qrmi) & [`maestro-qdmi-device`](https://github.com/QoroQuantum/maestro-qdmi-device) — QRMI and QDMI resource interfaces

---

## Links

[Website](https://www.qoroquantum.net) · [Enterprise](https://enterprise.qoroquantum.net) · [Cloud](https://dash.qoroquantum.net) · [Docs](https://docs.qoroquantum.net) · [LinkedIn](https://www.linkedin.com/company/qoro)
