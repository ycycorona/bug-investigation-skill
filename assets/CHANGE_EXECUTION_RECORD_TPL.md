# {{Change Topic}} Change Execution Record

## 1. Metadata

| Field | Value |
|---|---|
| Status | in_progress |
| Batch type | planning / feature / bug fix / configuration / documentation |
| Started at | {{YYYY-MM-DD HH:mm:ss and timezone}} |
| Completed at | Not completed |
| Related development task | {{`dev_plan/dev_task_<topic>.md`, or `None`}} |
| Related bug record | {{`bug_list/bug_task_<topic>.md`, or `None`}} |

## 2. Objective

{{Describe the single outcome this work batch must deliver.}}

## 3. Scope

### Included

- {{Files, modules, or behavior allowed to change in this batch}}

### Excluded

- {{Items explicitly outside this batch}}

## 4. Execution Steps

- [ ] {{Step 1}}
- [ ] {{Step 2}}
- [ ] {{Step 3}}

## 5. Validation Plan

| Type | Command or scenario | Passing condition |
|---|---|---|
| Automated or static check | `{{command}}` | {{Expected result}} |
| Functional validation | {{Scenario}} | {{Expected behavior}} |
| Safety check | {{Read-only, permission, or redaction check}} | {{Behavior that must not occur}} |

## 6. Rollback Plan

{{Describe how to reverse this batch safely, or explain why no rollback is needed.}}

## 7. Actual Result

> Before committing, set the status to `done`, add the completion time, and check all completed steps.

- Actual changes: Pending.
- Validation evidence: Pending.
- Plan deviations: None.
- Remaining issues: None.
