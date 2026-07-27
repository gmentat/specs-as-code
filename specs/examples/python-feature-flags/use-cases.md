# Use cases

## Product understanding

- **Intended clients:** Python application services
- **Problem:** A service needs one consistent answer about whether a named feature is enabled
- **Core value:** A small stable interface hides how flags are stored
- **Client-visible concepts:** Flag name and enabled state

## UC-001: Check a feature flag

- **Priority:** P1
- **Actor:** Python service
- **Trigger:** The service reaches behavior controlled by a feature flag
- **Goal:** Decide whether to enable that behavior
- **Expected outcome:** The service receives `True` or `False`

### Main flow

1. The service calls the interface with a flag name.
2. The interface returns the flag's enabled state.

### Failure path

- The flag name is unknown → the interface raises `UnknownFlagError`.

### Acceptance example

- Given an enabled `new_checkout` flag, when a service checks it, then the result is `True`.
