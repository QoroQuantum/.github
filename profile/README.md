# Qoro Quantum

We build software for running hybrid workloads across distributed, heterogeneous computing environments.

## About

Qoro Quantum develops infrastructure that connects classical HPC resources, simulators, and quantum hardware into a single execution layer. The goal is to make quantum-classical hybrid workflows actually usable in production — HPC centers, cloud platforms, and future quantum data centers — rather than just in research sandboxes.

## Projects

### [Maestro](https://github.com/QoroQuantum/maestro)

Maestro is our quantum circuit simulator. It puts statevector, matrix product state (MPS), stabilizer, extended stabilizer, density matrix, tensor network, Pauli propagation and other methods behind one API, and runs them on a laptop CPU, NVIDIA GPUs, or an MPI cluster. Write a circuit once, then change one config field to switch methods or move from CPU to GPU. Maestro also picks the engine that suits each circuit's size and structure.

It models realistic noise (Pauli and coherent errors, T1/T2 relaxation, crosstalk, readout and time-correlated noise), integrates with Stim/Sinter for error-correction studies, and can be driven from C/C++ or JSON without Python. It is also the decision layer that feeds scheduling and orchestration in distributed quantum setups.

**Already using Qiskit or PennyLane?** Change one import and keep your code. [`qiskit-maestro`](https://github.com/QoroQuantum/qiskit-maestro) replaces Aer's simulator and Qiskit's Sampler and Estimator, and [`pennylane-maestro`](https://github.com/QoroQuantum/pennylane-maestro) replaces `default.qubit`. On 120–200 qubit MPS workloads, `MaestroEstimator` runs up to 7× faster than Aer's `EstimatorV2` ([benchmarks](https://qoroquantum.github.io/maestro/benchmarks.html)).

```bash
pip install qoro-maestro        # Maestro
pip install qiskit-maestro      # Qiskit: MaestroBackend, MaestroSampler, MaestroEstimator
pip install pennylane-maestro   # PennyLane: the maestro.qubit device
```

GPU backends come as a separate plugin, available on the Qoro cloud (with free starter credits), under a free academic licence, or under an enterprise site licence. See [Get GPU access](https://qoroquantum.github.io/maestro/getting-started/gpu-access.html).

| Repository | Description |
|---|---|
| [maestro](https://github.com/QoroQuantum/maestro) | Core simulator: statevector, MPS, stabilizer, density matrix, tensor network, Pauli propagation and more, on CPU, GPU and MPI clusters ([docs](https://qoroquantum.github.io/maestro/)) |
| [qiskit-maestro](https://github.com/QoroQuantum/qiskit-maestro) | Qiskit provider: `MaestroBackend`, `MaestroSampler` and `MaestroEstimator`, drop-in replacements for Aer and Qiskit's reference primitives |
| [pennylane-maestro](https://github.com/QoroQuantum/pennylane-maestro) | PennyLane device `maestro.qubit`: a drop-in replacement for `default.qubit`, with adjoint gradients and MPS simulation of 1000+ qubit circuits |
| [qoro-pyscf](https://github.com/QoroQuantum/qoro-pyscf) | PySCF solver plugin — quantum chemistry via Qoro's simulation stack |
| [maestro-demos](https://github.com/QoroQuantum/maestro-demos) | Example simulations written in Maestro |

Maestro's CPU engine, [QCSim](https://github.com/QoroQuantum/QCSim), and its [Qiskit Aer](https://github.com/QoroQuantum/qiskit-aer) and [QuEST](https://github.com/QoroQuantum/maestro-quest-interface) backends are developed in their own repositories.

---

### [Divi](https://github.com/QoroQuantum/divi)

Divi is Qoro's Python library for building and running quantum programs at scale. You describe the problem, such as a graph, a QUBO or a molecule, and Divi generates the circuits, batches and parallelizes them, runs them and collects the results, so you can focus on the problem rather than the plumbing. To change where a program runs, you change one backend object: Maestro on your own machine, an HPC cluster or IBM quantum computer through QRMI, or simulators and quantum hardware on the Qoro cloud.

- **Algorithms:** VQE for ground-state energies, QAOA and Pauli correlation encoding (PCE) for combinatorial optimization, constraint-enhanced QAOA for routing problems (TSP and CVRP), Hamiltonian time evolution, and quantum neural networks. Circuits you write in Qiskit or PennyLane can be optimized the same way.
- **Problems bigger than one circuit:** program ensembles split a problem into pieces that fit the backend, run the pieces in parallel and combine their results. They cover partitioned MaxCut and QUBO problems, and LASSQD, which estimates molecular energies for active spaces too large for one circuit using sample-based quantum diagonalization.
- **Error mitigation:** zero-noise extrapolation (ZNE) and Quantum Enhanced Pauli Propagation (QuEPP), which plug into any variational program.
- **Long runs:** checkpoint and resume, live progress reporting, and a choice of optimizers.

```bash
pip install qoro-divi
```

```python
from divi.backends import MaestroSimulator, QoroService

backend = MaestroSimulator()  # simulate locally with Maestro
# backend = QoroService()     # or run the same program on the Qoro cloud
```

New accounts on [dash.qoroquantum.net](https://dash.qoroquantum.net/) get 1,000 of free cloud credits.

Start with the [five-minute tutorial](https://divi.readthedocs.io/en/latest/quickstart.html) and the [docs](https://divi.readthedocs.io). The [demos](https://github.com/QoroQuantum/divi/tree/main/demos) folder has end-to-end applications, including portfolio optimization, the travelling salesman problem and spin dynamics, and [tutorials](https://github.com/QoroQuantum/divi/tree/main/tutorials) has short single-file examples.

---

### HPC integration

For HPC centers: run Maestro as a managed service on your nodes, schedule it through Slurm, and reach it through the same resource interfaces as quantum hardware.

| Repository | Description |
|---|---|
| [maestro-local-server](https://github.com/QoroQuantum/maestro-local-server) | Runs Maestro as a service on a node. Clients open sessions over a Unix socket, queue simulation tasks and fetch results as JSON; each task runs in an isolated worker process, optionally under MPI |
| [qrmi](https://github.com/QoroQuantum/qrmi) | Fork of the Qiskit community's QRMI (Quantum Resource Management Interface) that adds a Maestro resource backed by `maestro-local-server`, so QRMI clients such as Divi's `QRMIBackend` can use it |
| [maestro-spank-plugin](https://github.com/QoroQuantum/maestro-spank-plugin) | Slurm SPANK plugin that sets Maestro simulation options, such as qubits and shots, from Slurm job options |
| [spank-plugins](https://github.com/QoroQuantum/spank-plugins) | Fork of the Qiskit community's Slurm SPANK plugins with a local Maestro resource and example job scripts |
| [maestro-qdmi-device](https://github.com/QoroQuantum/maestro-qdmi-device) | Maestro as a QDMI (Quantum Device Management Interface) device |

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
- Enterprise: [enterprise.qoroquantum.net](https://enterprise.qoroquantum.net)
- Docs: [docs.qoroquantum.net](https://docs.qoroquantum.net)
- Maestro docs: [qoroquantum.github.io/maestro](https://qoroquantum.github.io/maestro/)
- Divi docs: [divi.readthedocs.io](https://divi.readthedocs.io)
- Dash: [dash.qoroquantum.net](https://dash.qoroquantum.net)
- LinkedIn: [Qoro Quantum](https://www.linkedin.com/company/qoro)
