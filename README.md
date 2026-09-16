# tui-releases

The update feed for [Tui](https://github.com/aminosman/tui) and Roost.

`appcast.xml` is a Sparkle-format feed carrying both apps: one item per
release, each naming its product in `<sparkle:channel>` (`tui` or
`roost`), with an Ed25519 signature over the artifact's bytes. Every
installed copy of Tui reads this file hourly, takes anything newer for
either app, verifies it against a public key baked into the binary, and
swaps the bundle — Roost only while it is not running, since it hosts the
agents.

`feed.json` is the source of truth the appcast is regenerated from. Tui's
zips are released here; Roost's stay on the fork they are built from and
the feed points at them.

Cut a release with `scripts/release-tui.sh` (Tui) or
`scripts/release-roost.sh` (Roost). The scheme, the safety properties and
the key are documented in `docs/auto-update.md` in the Tui repo.
