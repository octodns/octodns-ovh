# Developer Agent Guide for octoDNS OVH Provider

This repository contains the OVH provider for octoDNS. It enables planning, syncing, and applying DNS record states directly to the OVH DNS API using the official `ovh` Python client.

> [!IMPORTANT]
> **Core Workflow and Guidelines**
>
> All agents working on this repository must read and follow the general instructions and workflow guidelines defined in the core octoDNS `AGENTS.md` file.
> - **Local check**: Look for the file at `../octodns/AGENTS.md`.
> - **Remote check**: If the local file is not available, fetch it from GitHub: [octoDNS Core AGENTS.md](https://github.com/octodns/octodns/raw/refs/heads/main/AGENTS.md).
>
> You must align your code structure, style, pull request guidelines, and overall development workflows with the instructions specified there.

## Repository & Module Information

### Key Components

- **Provider Class**: [OvhProvider](file:///home/ross/octodns/octodns-ovh/octodns_ovh/__init__.py#L21-L460) (defined in [octodns_ovh/__init__.py](file:///home/ross/octodns/octodns-ovh/octodns_ovh/__init__.py)). This is the core provider communicating with the OVH API.
- **Client & SDK**: Uses `ovh.Client` to interact with OVH DNS API endpoints.
- **Authentication**: Authenticates using four configuration keys: `endpoint`, `application_key`, `application_secret`, and `consumer_key`.
- **Special Conditions**:
  - `ZONE_NOT_FOUND_MESSAGE = 'This service does not exist'`: Handles this specific `ResourceNotFoundError` return payload to cleanly flag if a zone does not exist yet.

### Key Workflows & Features

1. **Supported Record Types**: `A`, `AAAA`, `CAA`, `CNAME`, `DKIM`, `HTTPS`, `MX`, `NAPTR`, `NS`, `PTR`, `SRV`, `SSHFP`, `SVCB`, `TXT`.
2. **Subdomain Mapping**: Maps record names to the `subDomain` attribute and record type to the `fieldType` attribute in the OVH API data structure.
3. **Root Name Server Support**: Fully supported (`SUPPORTS_ROOT_NS=True`).
4. **Dynamic Routing**: Not supported (`SUPPORTS_DYNAMIC=False`, `SUPPORTS_GEO=False`).
5. **Dynamic Subnets**: Not supported (`SUPPORTS_DYNAMIC_SUBNETS=False`).
6. **Pool Value Status**: Not supported (`SUPPORTS_POOL_VALUE_STATUS=False`).

## Development & Testing

- **Setup Script**: Run `./script/bootstrap` to create a virtual environment, install dependencies (including `black`, `isort`, `pyflakes`, and `pytest`), and configure pre-commit hooks.
- **Test Suite**: Run unit tests using `pytest` via `./script/test` (or `pytest tests/`). Test files are located in [tests/](file:///home/ross/octodns/octodns-ovh/tests).
- **Code Coverage**: Verify code coverage using `./script/coverage`.

## Key Constraints & Behaviors

- **Python Version**: Targets Python `>=3.9`.
- **Formatting**: Code formatting is enforced via `black` (version `>=26.0.0,<27.0.0`) and `isort`.
