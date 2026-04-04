# Qoro Quantum

We build software for running hybrid workloads across distributed, heterogenous computing environments.

## About

Qoro Quantum develops infrastructure that connects classical HPC resources, simulators, and quantum hardware into a single execution layer. The goal is to make quantum-classical hybrid workflows actually usable in production — HPC centers, cloud platforms, and future quantum data centers — rather than just in research sandboxes.

## Projects

### [Maestro](https://github.com/QoroQuantum/maestro)

Maestro is our simulation and execution layer. It wraps multiple circuit simulation backends behind a common interface and picks the right one based on circuit size, structure, and available hardware — CPU, GPU, or distributed HPC.

It also acts as the decision layer that feeds scheduling and orchestration in distributed quantum setups.

| Repository | Description |
|---|---|
| [maestro](https://github.com/QoroQuantum/maestro) | Core simulation engine — statevector, MPS, tensor network, Pauli propagation on CPU/GPU/HPC |
| [maestro-examples](https://github.com/QoroQuantum/maestro-examples) | Example simulations and benchmarks written in Maestro |
| [pennylane-maestro](https://github.com/QoroQuantum/pennylane-maestro) | PennyLane device plugin — run PennyLane workflows on Maestro backends |
| [qoro-pyscf](https://github.com/QoroQuantum/qoro-pyscf) | PySCF solver plugin — quantum chemistry via Qoro's simulation stack |
| [maestro-qdmi-device](https://github.com/QoroQuantum/maestro-qdmi-device) | QDMI device interface for Maestro |
| [maestro-spank-plugin](https://github.com/QoroQuantum/maestro-spank-plugin) | SPANK plugin for Slurm-based HPC job integration |
| [maestro-quest-interface](https://github.com/QoroQuantum/maestro-quest-interface) | QuEST simulator backend adapter |

---

### [Divi](https://github.com/QoroQuantum/divi)

Divi is Qoro's Python SDK for quantum application developers. Write your algorithm once and run it across simulators, HPC systems, or real quantum hardware. Divi handles batching, parallelization, and backend routing so you don't have to.

Aimed at researchers, students, and teams who want to focus on the algorithm, not the plumbing.

| Repository | Description |
|---|---|
| [divi](https://github.com/QoroQuantum/divi) | Core SDK — circuit generation, job parallelization, VQE/QAOA, cloud execution |
| [divi-demos](https://github.com/QoroQuantum/divi-demos) | Example programs and tutorials written in Divi |

---

## What We're Working On

- Future datacenter and cluster networking
- Quantum-classical hybrid applications
- Scheduling, routing, and execution across heterogeneous resources
- Plugging quantum into existing HPC and cloud infrastructure

## Work With Us

We collaborate with HPC centers, research groups, and industry partners on quantum computing, simulation, and hybrid workflows. If you're exploring joint research, pilots, or want to add quantum capabilities to your existing stack, reach out.

## Links

- Website: [qoroquantum.net](https://www.qoroquantum.net)
- Docs: [docs.qoroquantum.net](https://docs.qoroquantum.net)
- Dash: [dash.qoroquantum.net](https://dash.qoroquantum.net)
- LinkedIn: [Qoro Quantum](https://www.linkedin.com/company/qoro)
