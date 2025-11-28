---
description: Post-Onboarding Checks
sidebar_position: 5
---

#  Post-Onboarding Checks
After activation, verify everything is operating normally:
- **Attestation Resumption:** Confirm validators are attesting (can take up to ~3 epochs).
- **Funding Top-up:** Set reminders at least 14 days before depletion.
- **Backups:** Secure operator password and private key files separately and offline (How‑to: [Backup Node guide](/operators/operator-node/maintenance/node-migration.md#node-backup)).
- **Monitoring:** [Use dashboards](/operators/operator-node/monitoring/dashboard-runbook.md) and logs for proactive health checks.

---

### Handling Issues
In case you encountered issues during Onboarding, you will need to rollback to your Previous Setup:
- Remove Migrated  Keys (How‑to: Remove Validators. guide).
- Restore Originals: Re-import original keystores into your previous validator instances.
- Restart Validators: Ensure services resume attestations normally.
- Validation: Check monitoring dashboards and logs.
- Remove Operators: If the rollback is permanent, remove operators (How‑to: Remove Operator guide).