# Aurora4x 2.7 — CristoTheme + Cross-Device Sync

This repository is a **pre-patched, ready-to-clone installation of [Aurora4x](http://aurora2.pentarch.org/)** (the C# version, v2.7+) with the CristoTheme mod. It doubles as a **cross-device save sync hack via GitHub** — fork and clone it on any machine, pull, play, push, repeat.

### What's included
- **Aurora 4x 2.7.1** (C# version) — game executable and all runtime dependencies
- **[AuroraPatch](https://github.com/Aurora-Modders/AuroraPatch)** — the mod loader
- **CristoTheme** — a UI theme derived from SolarisTheme and DeepBlueTheme (see Credits)
- **`AuroraDB.db`** — the live save file, synced via Git LFS

All binary files (`.exe`, `.dll`, `.db`, images) are stored in **Git LFS** so the repo stays fast and the save file is never silently corrupted by a bad merge.

---

## Fresh device setup

> Requires [Git](https://git-scm.com/) and [Git LFS](https://git-lfs.com/) installed.

```sh
git lfs install        # one-time setup per machine
git clone <this-repo>
```

That's it. No manual patching needed — everything is already in the repo.

**To play:** run **`AuroraPatch.exe`** (not `Aurora.exe`) and select **CristoTheme** when prompted.

On Linux/macOS you'll need [Wine](https://www.winehq.org/) or similar to run the Windows executable.

---

## Syncing saves between devices

Aurora stores the entire game state in `AuroraDB.db`. The workflow is:

```sh
# Before sitting down to play — get the latest save
git pull

# After a session — push your progress
git add AuroraDB.db
git commit -m "session: <date or note>"
git push
```

> **Important:** always pull before playing and push after. If two devices have diverging saves, Git LFS will detect the conflict instead of silently producing a corrupted database.

---

## Notes

1. The aurora2.pentarch.org forum has an expired SSL certificate. To access it, change `https://` to `http://` in the URL. If your browser won't allow that, use Firefox.

2. Don't report bugs on the official forum while using any mod.

3. Aurora requires a **period (`.`)** as the decimal separator. If your system locale uses a comma, adjust it before playing.

---

# Credits

CristoTheme is a variant of the [SolarisTheme mod](https://github.com/simast/SolarisTheme/blob/master/SolarisTheme.cs) by simast, incorporating changes from the [DeepBlueTheme mod](https://aurora2.pentarch.org/index.php?topic=12593.0) by Jorgen_CAB.

Both are built on twitce2double's [ThemeCreator](https://github.com/Aurora-Modders/ThemeCreator), applied via 01010100b's [AuroraPatch](https://github.com/Aurora-Modders/AuroraPatch).

Vast majority of credit rightly goes to those people, thank you!
