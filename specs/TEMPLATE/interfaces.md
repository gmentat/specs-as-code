# Interfaces

<!-- Include only stable client-visible boundaries required by current use cases.
     Use the actual public language or format. Callable examples default to Python.
     Keep a small contract inline; otherwise link one canonical file under contracts/.
     If no stable interface exists, say why and remove the unused sections. -->

## Clients

- `[client]` uses IF-001 for UC-001.

## IF-001: [Interface name]

- **Supports:** UC-001
- **Purpose:** [Client outcome this boundary enables]
- **Canonical contract:** Inline below

### Contract

<!-- Replace this with the exact public declaration.
     For a standard or lengthy contract, replace this section with a link such as
     `contracts/service.openapi.yaml`. Do not define the same contract twice. -->

```python
from typing import Protocol


class InterfaceName(Protocol):
    def operation(self, required_value: str) -> str: ...
```

### Semantics

- **Errors:** [Exact error type or value, condition, and client recovery]
- **Side effects:** [Observable state changes, or none]
- **Guarantees:** [Only guarantees not expressed by the declaration]
