# Orarium

Orarium is a Windows desktop application (Greek user interface) for building and printing a primary school's
weekly timetable, duty rotas, the all-day programme rota and substitutions. It works fully offline.

**This repository does not contain the application or its source code.** It only hosts the signed *patch*
releases that installed copies of Orarium download by themselves. The full installer is distributed privately.

## How updates work

- A copy of Orarium checks this repository's Releases a few minutes after it starts and then every few hours.
- Every release is a **patch**: a small setup that contains only the files that changed since the *base build*
  the installation was made from (`Orarium-patch-<version>.exe`) together with its signed manifest
  (`Orarium-patch-<version>.update`).
- Patches are **cumulative against the base build**, not against the previous patch. The newest patch can be
  applied to the base build or to any earlier patch of the same base, so there is never a chain to walk.
- The patch setup refuses to run unless the folder it is pointed at is an installation of the base build it was
  made for, and unless the files it does not touch still match that base.
- The manifest is signed (Ed25519). The application only accepts a patch whose signature, size and SHA-256 match,
  and only downloads from this repository's release assets.
- The setup backs up what it replaces, starts the new version and waits for it to report that it is healthy;
  otherwise it restores the previous version automatically.

## Releases

`v<version>` releases contain exactly two assets: the patch setup and its `.update` manifest.

## License

© 2026 Fotis P. All rights reserved. The patches are provided for use with the matching Orarium installation only.
