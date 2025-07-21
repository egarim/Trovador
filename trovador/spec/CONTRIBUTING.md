# Contributing to trovador.io

Thank you for your interest in contributing to `trovador.io`!

This project welcomes contributions, but follows a structured and opinionated architecture. Please review the following before submitting changes.

## Getting Started

- Fork the repository
- Run the solution using Docker or local dev mode
- Follow the code structure in `/Trovador.Domain`, `/Trovador.Application`, etc.
- All services must use dependency injection and must not break existing contracts

## Requirements

- All code must compile with .NET 8
- All new features must be tested using ASP.NET Core Test Host (`WebApplicationFactory`)
- Database changes must include EF Core migrations
- Do not introduce external libraries without prior approval
- Follow C# coding conventions and use meaningful commit messages

## Submitting a Pull Request

1. Fork the repository and create a new branch
2. Make your changes and commit with clear message
3. Write or update tests
4. Open a pull request and describe your changes

All pull requests will be reviewed by **Jose Manuel Ojeda Melgar** and **Jose Javier Columbie** or delegated maintainers.

## Code of Conduct

Be respectful, collaborative, and focused on building a high-quality project.
