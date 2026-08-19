---
name: bug-investigation-skill
description: Investigate and document reproducible failures in a software project using code, configuration, logs, tests, and runtime evidence. Use for bug reports, exceptions, timeouts, test failures, root-cause analysis, troubleshooting records, or explicitly authorized fixes. Preserve read-only boundaries for diagnosis and write repository records only when the user requests documentation or changes.
---

# Bug Investigation

Build an evidence-backed account of a failure in the target project. Keep confirmed facts, supported inferences, and unverified hypotheses distinct throughout the investigation.

## Repository Sources of Truth

- Read the repository-root `AGENTS.md` before acting when it exists.
- Before creating or updating a bug record, read the project's `doc_template/BUG_INVESTIGATION_RECORD_TPL.md` completely and follow it.
- Before creating a change-plan record, read the project's `doc_template/CHANGE_EXECUTION_RECORD_TPL.md` completely when it exists.
- If either project template is missing, report the missing path and point the user to the corresponding packaged file in `assets/`. Do not copy a template into the project without authorization.
- Packaged templates for manual project integration:
  - `assets/BUG_INVESTIGATION_RECORD_TPL.md`
  - `assets/CHANGE_EXECUTION_RECORD_TPL.md`
- Follow the project's existing bug-record and change-plan locations and naming conventions.
- When the project has no convention, use `bug_list/bug_task_<topic>.md` for durable root-cause history and `docs/change_plans/<timestamp>_<topic>.md` for one write-enabled work batch.
- Continue an existing bug record for the same issue. Create a separate record for an unrelated failure or a distinct root-cause chain.

## Authorization Boundary

Classify the request before changing files or external state:

- For diagnosis, investigation, review, or explanation, perform read-only inspection and report the findings. Do not create or update repository documents unless the user also asks to record or preserve the investigation.
- When the user requests a bug record or repository changes, make the change-plan record the first artifact of that work batch, then create or update the bug record.
- Implement a fix only when the user has explicitly requested or authorized implementation.
- Treat external systems as read-only during diagnosis. Never infer permission to modify user data, production state, a service, or a remote configuration.
- If the user requires an entirely read-only session, do not create or update any repository document; state that no record was written.

## Investigation Workflow

1. Identify the project's language, runtime, build system, test commands, deployment context, and repository conventions. Then inspect relevant source, configuration, tests, log entry points, existing bug records, and recent changes. Prefer `rg` and `rg --files` for repository searches.
2. Define the failure boundary: identify the last verified successful layer, the first failing layer, and downstream layers that were not reached or not tested.
3. Capture the expected behavior, reproduction conditions, actual result, impact, and the minimum sanitized evidence needed to support each claim.
4. Maintain a hypothesis table. Mark each hypothesis as `pending`, `confirmed`, `ruled_out`, or `insufficient_evidence`, and link it to supporting or contradicting evidence.
5. Test hypotheses with the smallest reversible checks that match the problem scope. Preserve failed investigation attempts when they prevent repeated dead ends.
6. If a fix is authorized, record the chosen approach, rejected or failed attempts, deviations from the plan, and a practical rollback path before or alongside implementation.
7. Run reproduction checks, regression tests, and safety checks proportional to the affected surface. Record exact commands, outcomes, and untested areas.
8. Update the applicable records with the current conclusion and remaining uncertainty. Follow repository guidance for diff review, task logging, and commit requirements.

## Evidence Standard

- Prefer reproducible commands, minimally sufficient logs, concrete code paths, configuration provenance, timestamps, and runtime observations.
- Treat a user report or screenshot as evidence of the visible symptom, not proof of the underlying mechanism.
- Do not turn temporal correlation into causation or infer an internal thread, race, or product defect merely because a restart restored service.
- Label mechanisms that the available evidence cannot establish as `unknown` or `insufficient_evidence`.
- Never invent logs, files, test results, API behavior, or documentation conclusions.
- Redact personal data, infrastructure identifiers, API keys, access tokens, cookies, passwords, and complete sensitive payloads from all records and responses.

## Safety and Authorization

- Keep external services, production systems, databases, and user or account state read-only during diagnosis unless the user explicitly authorizes a specific mutation.
- For network or integration failures, separate the local process, intermediary services, upstream dependencies, and response path. Do not conflate observations from different links or ports.
- Do not disable safeguards, broaden permissions, or perform destructive cleanup as a troubleshooting shortcut.

## Naming, Priority, and Status

- When the project has no naming convention, use `bug_list/bug_task_<topic>.md`, where `<topic>` is concise lowercase English joined with underscores.
- Use these default priorities unless the project defines stricter values: `P0` for a critical production, data-loss, or security incident; `P1` for a blocked core function; `P2` for a degraded function with a workaround; and `P3` for low-impact or usability issues.
- Use these lifecycle states when the template does not define stricter values: `investigating`, `root_cause_confirmed`, `fixing`, `verifying`, `resolved`, and `blocked`.
- Mark an issue `resolved` only when evidence supports the root cause, the fix is verified, and no required work remains. Otherwise keep the current investigation state and name the gap.

## Final Response

Summarize:

- paths to the bug record and change-plan record, or why no files were written;
- the confirmed failure boundary and root cause, or the strongest current hypothesis with its confidence limits;
- validation performed and its results;
- remaining unknowns, blockers, untested areas, and any authorization needed from the user.
