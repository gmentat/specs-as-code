# Interfaces

## Clients

- Python application services use IF-001 for UC-001.

## IF-001: Feature flag reader

- **Supports:** UC-001
- **Purpose:** Read one named flag without exposing its storage
- **Canonical contract:** Inline below

### Contract

```python
from typing import Protocol


class UnknownFlagError(LookupError):
    ...


class FeatureFlags(Protocol):
    def is_enabled(self, flag_name: str) -> bool: ...
```

### Semantics

- **Errors:** `UnknownFlagError` when `flag_name` does not identify a flag.
- **Side effects:** None.
