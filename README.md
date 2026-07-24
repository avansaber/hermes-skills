# ERPClaw — Hermes Agent tap

Install [ERPClaw](https://github.com/avansaber/erpclaw), the AI-native ERP, on
the Hermes Agent runtime:

```
hermes skills tap add avansaber/hermes-skills
hermes skills install erpclaw
```

ERPClaw runs your whole business in plain English: double-entry accounting,
invoicing, inventory, purchasing, payroll, and more. Self-hosted, open source
(GPL v3), free forever. The primary runtime is OpenClaw; Hermes support is
experimental and best-effort.

The Hermes runtime installs skills from a tap repo whose layout it requires: a
top-level `skills/` directory with one folder per skill. This repo places the
ERPClaw foundation skill under `skills/erpclaw/` so the two commands above work.

## Contents

`skills/erpclaw/` is a generated copy of the ERPClaw foundation skill. The
source of truth, full documentation, issue tracker, and every other module live
in the main repository: **https://github.com/avansaber/erpclaw**.

Do not edit files under `skills/`; they are regenerated on each release. Open
issues and pull requests against the main repository instead.

## License

GPL v3. See `skills/erpclaw/LICENSE.txt`.
