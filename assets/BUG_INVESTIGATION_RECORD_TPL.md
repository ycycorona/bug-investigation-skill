# {{Issue Title}} Investigation and Fix Record

## 1. Metadata

| Field | Value |
|---|---|
| Issue title | {{Concise one-line title}} |
| Current phase | reported / investigating / root cause confirmed / fixing / verifying / complete |
| Status | investigating |
| Priority | P0 / P1 / P2 / P3 |
| Created at | {{YYYY-MM-DD HH:mm:ss and timezone}} |
| Resolved at | Not resolved |
| Environment | {{local / dev / staging / production; operating system, runtime, and key versions}} |
| Related development task | {{Path, or `None`}} |

## 2. Issue Summary

{{In one to three sentences, describe the symptom, failure boundary, and current conclusion. Mark unknown details as `pending verification`.}}

```text
{{Last verified successful layer -> first failing layer -> layers not reached or not tested}}
```

## 3. Expected Behavior

{{Describe the correct behavior, inputs, outputs, and acceptance criteria.}}

## 4. Reproduction

### Environment and Preconditions

- {{Configuration, versions, data, feature flags, or access mode. Redact sensitive values.}}

### Steps

1. {{Step 1}}
2. {{Step 2}}
3. {{Step 3}}

### Actual Result

{{Describe the error, unexpected state, or behavior.}}

### Reproducibility

- Frequency: {{always / intermittent / observed once / unknown}}
- First observed: {{Time or version}}
- Last known working: {{Time or version, or `Unknown`}}

## 5. Impact

- Affected functionality: {{Details}}
- Unaffected functionality: {{Details}}
- Data, service, or security impact: {{Details}}
- Temporary workaround: {{Details, or `None`}}

## 6. Evidence

### Logs and Errors

```text
{{Include only the minimum necessary sanitized logs, or state that none are available.}}
```

### Code and Configuration

- `{{path:line}}`: {{Relevance to the issue}}

### Runtime and External Evidence

- {{Command, screenshot, protocol response, process observation, or network evidence}}

## 7. Investigation Log

| Time | Check | Method | Result | Conclusion |
|---|---|---|---|---|
| {{Time}} | {{What was checked}} | `{{Command or scenario}}` | {{Observed result}} | {{Supports / rules out / pending}} |

## 8. Hypotheses

| Hypothesis | Status | Supporting evidence | Contradicting evidence or next check |
|---|---|---|---|
| {{Possible cause}} | pending | {{Evidence}} | {{Evidence or validation action}} |

Use only these statuses: `pending`, `confirmed`, `ruled_out`, and `insufficient_evidence`.

## 9. Root-Cause Analysis

### Confirmed Direct Cause

{{Describe the first failing layer. Use `Not confirmed` until supported by evidence.}}

### Root Cause

{{Describe the evidence chain. Mark mechanisms that cannot be established as `unknown`.}}

### Ruled-Out Causes

- {{Cause and the evidence that rules it out}}

## 10. Fix Attempts

| Time | Attempt | Result | Retained | Evidence and side effects |
|---|---|---|---|---|
| {{Time}} | {{Action}} | {{succeeded / failed / no change}} | {{yes / no}} | {{Details}} |

> Do not implement a fix without user authorization. During read-only investigation, write `Fix not authorized`.

## 11. Final Solution and Change Scope

- Solution: {{Details, or `Pending`}}
- Modified files: {{Paths, or `None`}}
- Configuration or data migration: {{Details, or `None`}}
- Rollback: {{Details, or `Not applicable`}}
- Plan deviations: {{Details, or `None`}}

## 12. Validation

| Type | Command or scenario | Expected | Actual | Result |
|---|---|---|---|---|
| Reproduction check | `{{command}}` | {{Expected result}} | {{Actual result}} | pending |
| Regression test | `{{command}}` | {{Expected result}} | {{Actual result}} | pending |
| Safety check | {{Read-only, permission, redaction, or data check}} | {{Expected result}} | {{Actual result}} | pending |

Untested areas: {{Details, or `None`}}.

## 13. Safety and Privacy

- [ ] No unauthorized external write was performed.
- [ ] External services, production systems, and user or account state remained read-only unless explicitly authorized.
- [ ] Personal data, infrastructure identifiers, credentials, cookies, and tokens were removed or redacted.
- [ ] No safeguard was disabled and no permission was broadened for troubleshooting.

## 14. References

- {{Project file, authoritative documentation, or related record; use `None` if not applicable}}

## 15. Retrospective and Open Items

### Prevention

- {{Reusable detection, monitoring, testing, or operational rule}}

### Open Items

- [ ] {{Follow-up item; if none, write `- [x] None`}}

### Related Change Execution Records

| Change record | Batch objective | Status |
|---|---|---|
| [`{{timestamp_topic.md}}`](../docs/change_plans/{{timestamp_topic.md}}) | {{investigation / fix / verification}} | in_progress |
