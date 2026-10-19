# moonlight-limits

`limits.json` is the agreed ceiling on what each Moonlight instance **other than luna** spends on the strategies
that trade the same thin books luna does.

Every instance fetches it once a day from

    https://raw.githubusercontent.com/dustball/moonlight-limits/main/limits.json

and **lowers** its own live caps to these numbers. It never raises anything, and paper is untouched.

- `default`: limits for every instance that is not `exempt`.
- `instances.<name>`: per-instance overrides, matched to the instance's `MOONLIGHT_INSTANCE_NAME`. `null` removes a default.
- Keys are Moonlight setting keys, in dollars.

The reasoning behind each number, and how the clamp works, is `docs/FLEET-LIMITS.md` in the Moonlight repo.
After editing, check the file with `node scripts/fleet-limits.ts` there.
