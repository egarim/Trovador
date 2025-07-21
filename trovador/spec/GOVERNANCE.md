# Governance Model – trovador.io

`trovador.io` is an open source project licensed under the MIT License. While the project encourages community contributions, **the architectural design, technical direction, and long-term roadmap are managed by a central team of maintainers.**

## Core Maintainer

- **Jose Manuel Ojeda Melgar** (nickname: Joche Ojeda)

## Governance Philosophy

- All changes must adhere to the project's clean architecture principles.
- No breaking changes will be accepted without a versioned interface update and migration plan.
- All services must use dependency injection, data contracts, and Entity Framework Core as per design guidelines.
- The system must remain container-friendly and testable using ASP.NET Core Test Host.

## Maintainer Responsibilities

- Review contributions for architectural alignment
- Define and refine system contracts and APIs
- Manage releases and versioning strategy
- Lead roadmap planning and community communication

## Contributor Expectations

- Follow the contribution guidelines (see `CONTRIBUTING.md`)
- Respect the architectural boundaries
- Write tests using the defined strategy
- Avoid introducing external dependencies unless explicitly approved

Maintainers reserve the right to reject contributions that conflict with the vision, structure, or long-term goals of the project.
