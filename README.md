# ParticleDynamics
### GPU-Accelerated Nonlinear Dynamical Systems for Unreal Engine 5.8

**ParticleDynamics** is a GPU-accelerated particle simulation plugin developed for Unreal Engine 5.8. It provides a real-time environment for exploring and visualizing nonlinear dynamical systems through configurable mathematical models, numerical integration methods, and GPU-based particle computation.

The plugin is designed around a modular simulation architecture, allowing users to switch between different mathematical systems and adjust simulation parameters at runtime through an integrated control interface.

The project combines numerical methods, GPU compute programming, shader development, and real-time visualization within Unreal Engine.

---

## Overview

ParticleDynamics brings mathematical dynamical systems into Unreal Engine through a dedicated GPU simulation pipeline.

Rather than relying entirely on CPU-based particle updates, the simulation uses GPU compute shaders to perform particle state calculations and numerical integration. The resulting simulation data is then used by the rendering pipeline to visualize particle trajectories and dynamic behavior.

The system is designed to support multiple mathematical models through a shared simulation architecture, reducing the need for separate simulation implementations for each model.

## Key Features

- **GPU-Accelerated Simulation** – Particle state calculations are performed using GPU compute shaders.
- **Multiple Dynamical Systems** – Eight implemented nonlinear mathematical models.
- **Numerical Integration** – Support for Euler and fourth-order Runge–Kutta (RK4) integration.
- **Runtime Parameter Control** – Adjust mathematical parameters and simulation settings while the simulation is running.
- **Dynamic Model Switching** – Select between different dynamical systems through the control interface.
- **Particle Visualization** – Real-time visualization of simulated particle trajectories.
- **Velocity-Based Coloring** – Particle appearance can be driven by velocity information.
- **GPU Data Readback** – Dedicated asynchronous GPU readback infrastructure for accessing simulation data.
- **Simulation Reset** – Restart simulation states through runtime controls.

## Supported Dynamical Systems

The plugin currently implements eight nonlinear dynamical systems:

| System | Mathematical model |
|---|---|
| Lorenz | Lorenz attractor |
| Aizawa | Aizawa attractor |
| Thomas | Thomas cyclically symmetric attractor |
| Rössler | Rössler attractor |
| Chen | Chen chaotic system |
| Halvorsen | Halvorsen attractor |
| Dadras | Dadras system |
| Rabinovich–Fabrikant | Rabinovich–Fabrikant system |

Each model has its own mathematical parameters and behavior, while sharing the underlying simulation infrastructure.

## Technical Architecture

ParticleDynamics is organized around several cooperating systems.

### 1. Simulation Management

The simulation manager coordinates GPU simulation resources, particle state buffers, and compute dispatch operations.

Its responsibilities include managing simulation initialization, execution, and GPU resource handling.

### 2. Numerical Integration

The numerical integration system evaluates particle state evolution using two integration methods:

- **Euler Integration:** A first-order numerical integration method.
- **Runge–Kutta 4 (RK4):** A fourth-order integration method offering improved numerical accuracy for many simulation conditions.

The integration method can be selected at runtime.

### 3. GPU Compute Pipeline

The computational workload is implemented using Unreal Engine's shader infrastructure.

Compute shaders handle particle state updates and numerical calculations, while GPU buffers maintain simulation data between dispatches.

The architecture uses alternating GPU buffers to support iterative simulation updates.

### 4. Particle Rendering

The rendering system visualizes the computed particle states through a dedicated rendering pipeline.

Particle positions and associated simulation data are used to generate the visual representation of the dynamical systems.

### 5. Runtime Control Interface

An integrated Unreal Engine Widget Blueprint provides runtime access to simulation controls.

Users can interact with:

- Dynamical system selection
- Mathematical model parameters
- Integration method
- Simulation Delta Time
- Simulation reset
- Visualization settings

The interface is designed to expose simulation controls without requiring users to modify the underlying C++ implementation.

## Technology Stack

| Technology | Application |
|---|---|
| Unreal Engine 5.8 | Real-time simulation and visualization |
| C++ | Simulation architecture and resource management |
| HLSL / Unreal Shaders | GPU computation |
| Render Dependency Graph (RDG) | GPU resource and compute scheduling |
| RHI | GPU resource management |
| Compute Shaders | Particle state calculations |
| Blueprint / UMG | Runtime interaction and controls |
| Numerical Methods | Euler and RK4 integration |

## Development Highlights

Some of the main engineering challenges addressed during development include:

- Designing a reusable GPU simulation architecture for multiple mathematical models.
- Managing persistent GPU particle buffers across simulation updates.
- Implementing numerical integration directly within the GPU computation pipeline.
- Handling asynchronous GPU readback.
- Connecting C++ simulation systems with Blueprint-based runtime controls.
- Coordinating GPU simulation output with real-time particle rendering.
- Supporting dynamic mathematical parameter updates.

The project emphasizes modularity, separation of responsibilities, and real-time computational workflows.

## Demonstration

*Screenshots and demonstration videos will be added here.*

Recommended demonstrations:

1. Switching between the eight dynamical systems.
2. Comparing Euler and RK4 integration.
3. Modifying mathematical parameters at runtime.
4. Visualizing different attractor structures.
5. Demonstrating the runtime control interface.

## System Requirements

- Unreal Engine 5.8
- Windows 64-bit
- DirectX 12-compatible graphics hardware
- GPU support for the required shader and rendering features

Actual performance depends on particle count, GPU hardware, simulation settings, and rendering configuration.

## Commercial Availability

**ParticleDynamics is a proprietary commercial Unreal Engine plugin.**

This GitHub repository serves as a technical portfolio and project showcase. The complete implementation, source code, shaders, and distributable plugin are not publicly included in this repository.

The commercial product is intended for distribution through the Unreal Engine Fab marketplace.

For licensing, product availability, and distribution information, please refer to the official product listing when available.

## License

Copyright © 2026.

All rights reserved.

The software implementation, proprietary source code, shaders, and associated commercial assets are not licensed for redistribution, modification, or commercial reuse through this portfolio repository.

Please refer to the commercial product's license and applicable Fab marketplace terms for usage rights.

---

**ParticleDynamics — Exploring nonlinear dynamics through real-time GPU computation.**
