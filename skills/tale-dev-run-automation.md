---
name: tale-run-automation
description: Start a deployed Tale automation run, poll it to completion, and cancel it if needed.
api: tale-dev:tale-platform-api
operations: [listAutomations, startAutomationRun, getRun, cancelRun]
generated: '2026-10-09'
method: generated
source: openapi/tale-dev-openapi.yml
---
1. `listAutomations` to find the automation name.
2. `startAutomationRun` with an `Idempotency-Key` header so a retry does not start a second run.
3. Poll `getRun` with the returned runId; on `429` wait at least `Retry-After` seconds.
4. `cancelRun` to stop an in-flight run.
