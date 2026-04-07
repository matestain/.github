## What changed and why

<!-- The "why" is not optional. Explain the motivation — what problem this solves or what decision it implements. -->

---

## Related issue

Closes #

---

## Type of change

- [ ] Bug fix
- [ ] New feature
- [ ] Refactor (no behavior change)
- [ ] Documentation
- [ ] Chore (deps, tooling, config)
- [ ] Breaking change — describe impact below

---

## Testing

- [ ] Unit tests added or updated
- [ ] Integration tests added or updated
- [ ] Manually tested — describe scenario below
- [ ] No tests needed — explain why

<!-- Describe what you tested and how -->

---

## Industrial safety checklist

_Check N/A if this PR does not touch industrial protocols, field devices, or SCADA systems._

- [ ] N/A — this PR has no industrial protocol surface
- [ ] Read-only posture maintained — no writes to PLCs or field devices without explicit operator confirmation
- [ ] No silent failures — all error states are surfaced explicitly
- [ ] Timeouts are defined — no unbounded blocking calls
- [ ] Safe state on connection loss is handled

---

## Notes for reviewers

<!-- Anything that needs extra attention, known trade-offs, or follow-up work deferred to a separate issue -->
