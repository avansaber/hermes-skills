# ERPClaw — Hermes Agent tap

[ERPClaw](https://github.com/avansaber/erpclaw) is an AI-native open-source ERP
you self-host and run in plain English: double-entry accounting, invoicing,
inventory, purchasing, payroll, and more. Free forever (GPL v3). The primary
runtime is OpenClaw; Hermes support is experimental and best-effort.

This repository packages the ERPClaw foundation skill for the Hermes runtime,
under `skills/erpclaw/`.

## Installing on Hermes

Add this tap, then install with `--force`:

```
hermes skills tap add avansaber/hermes-skills
hermes skills install avansaber/hermes-skills/skills/erpclaw --force
```

Why `--force`: the Hermes security audit rates ERPClaw "caution" because its
accounting engine runs local commands by design (every action is local Python
invoked through a command router; nothing leaves your machine). The flag
acknowledges that caution rating. Use the tap-qualified name shown above; a
bare `install erpclaw` may resolve to a stale listing elsewhere.

Then point ERPClaw at a data directory and initialize its database:

```
export ERPCLAW_HOME=~/.hermes/erpclaw-home
python3 ~/.hermes/skills/erpclaw/scripts/erpclaw-setup/db_query.py --action initialize-database
```

Prefer not to use `--force`? The manual install works identically:

```
git clone https://github.com/avansaber/erpclaw ~/.hermes/skills/erp/erpclaw
export ERPCLAW_HOME=~/.hermes/erpclaw-home
python3 ~/.hermes/skills/erp/erpclaw/scripts/erpclaw-setup/db_query.py --action initialize-database
```

Then talk to it, keeping `ERPCLAW_HOME` exported:

```
hermes chat -s erpclaw --yolo -q "Set up my company"
```

Recommended: `hermes curator pin erpclaw` so the skill stays exactly as
installed. Credential values never pass through the agent on any runtime:
lookups return existence plus a redacted preview only, and high-impact actions
(restores, credential changes, master-key operations) always require an
explicit confirmation flag. Hermes support overall remains experimental and
best-effort.

## Contents

`skills/erpclaw/` is a generated copy of the ERPClaw foundation skill. The source
of truth, full documentation, issue tracker, and every other module live in the
main repository: **https://github.com/avansaber/erpclaw**. Do not edit files
under `skills/`; open issues and pull requests against the main repository.

## License

GPL v3. See `skills/erpclaw/LICENSE.txt`.
