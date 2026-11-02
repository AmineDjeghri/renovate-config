# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) base config for my repos. It holds the common managers, grouping
rules, 7-day release-age cooldown and age/confidence badges in [`default.json5`](default.json5).

## Use it

In a repo's `.github/renovate.json5`:

```json5
{
  extends: ["github>AmineDjeghri/renovate-config:default.json5"],
  packageRules: [
    // repo-specific rules go here and override the shared ones (later rules win)
  ],
}
```

The `:default.json5` suffix is required: without it Renovate only looks for `default.json`.

## Validate

Check a config with the latest Renovate (syntax and option names; no network needed):
```bash
npx --yes --package renovate@latest -- renovate-config-validator --strict default.json5
```

or in your repo with:
```bash
npx --yes --package renovate@latest -- renovate-config-validator --strict .github/renovate.json5
```

Run it on `default.json5` too before pushing a change here, since every repo that extends it picks the change up.
