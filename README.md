# ERPClaw — Hermes Agent tap

[ERPClaw](https://github.com/avansaber/erpclaw) is an AI-native open-source ERP
you self-host and run in plain English: double-entry accounting, invoicing,
inventory, purchasing, payroll, and more. Free forever (GPL v3). The primary
runtime is OpenClaw; Hermes support is experimental and best-effort.

This repository packages the ERPClaw foundation skill for the Hermes runtime,
under `skills/erpclaw/`.

## Installing on Hermes

The one-command `hermes skills install` is not available yet. The Hermes runtime
audits skills and blocks any that run system commands, which ERPClaw does by
design: its accounting engine is local Python invoked through a command router.
A verified publish that clears this audit is planned.

Until then, install manually by cloning the skill and initializing its database:

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
installed. Credential and encrypted-backup features are outside the experimental
Hermes scope for now; avoid them there.

## Contents

`skills/erpclaw/` is a generated copy of the ERPClaw foundation skill. The source
of truth, full documentation, issue tracker, and every other module live in the
main repository: **https://github.com/avansaber/erpclaw**. Do not edit files
under `skills/`; open issues and pull requests against the main repository.

## License

GPL v3. See `skills/erpclaw/LICENSE.txt`.
