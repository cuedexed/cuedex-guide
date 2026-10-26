# Sharing cues: the public cue repository

CueDex's default source for shared cues is a public GitHub repository,
[cuedexed/cuedex-cues](https://github.com/cuedexed/cuedex-cues). Anyone can add cue sets to it with a pull request.
Every set in it is signed by its author's CueDex key and checked by a robot before it is merged.

## Before you share

- Shared cue sets are released under CC0 1.0 (public domain). Anyone may use, change and share them, without
  asking and without credit.
- Share only your own work. A cue set must contain no audio, no lyrics and no other third-party content: only cue
  positions, lane names, typed cue actions for the shipped target profiles, and the recording's title, artist and
  duration (plus an ISRC or platform ids if you add them).
- Copies shared under CC0 cannot be recalled. You can remove your set from the repository at any time, but copies made
  before stay valid.

CueDex asks you to confirm this once, the first time you publish.

## Add a cue set

1. Fork [cuedexed/cuedex-cues](https://github.com/cuedexed/cuedex-cues) on GitHub and clone your fork to your Mac.
2. In CueDex, open the track and the **Shared** tab (Library → Shared). Set **Source** to `repo:` followed by the path
   of your clone, for example `repo:/Users/you/cuedex-cues`.
3. Fill in the track title and artist (and an optional set title and display name), choose MY or MERGED (and
   **not a fork**, or the shared set yours derives from). The first time, tick **I release this under CC0-1.0, it is
   my own work, and it contains no audio, lyrics or third-party content (asked once)**. Then click
   **Publish (signed, with proof of work)**. CueDex signs the version with your key and writes its files (and the
   recording's fingerprint) into your clone.
4. Commit the new files on a branch and open a pull request against `cuedexed/cuedex-cues`.
5. The *verify* check rebuilds the repository's index with CueDex's own verifier: every signature, every file name
   (it is the content's hash), every set against the published schema and rules. A pull request may change only
   `sets/` and `fingerprints/` (and the files the check derives from them).
6. A maintainer merges. The repository's offline bundle is rebuilt; CueDex users get your set from the next search.

## Update or remove your set

- *A new version:* publish again from the same CueDex install (the same key) and open a pull request with the new
  files. Only your key can add versions to your set.
- *Remove it:* open a pull request that deletes its folder under `sets/`.
- *Flag someone else's set:* open an issue on the repository with the reason (wrong, harmful, lyrics, not the
  author's own, spam), or use **Flag** in CueDex.

## What the repository stores

- `sets/<set>/<version>.json`: one signed version of a cue set, exactly as its author's CueDex signed it, with the
  author's public key (a pseudonym made on their Mac, not an account).
- `fingerprints/<hash>.fp`: the recording's fingerprint, numbers that identify and align a recording. Never audio; they
  cannot be turned back into sound.
- `index.json`, `recordings/` and each set's `set.json`: derived by the check, never edited by hand.

Not stored: e-mail addresses, names other than the display name you choose, accounts, audio, lyrics, IP addresses.
GitHub itself keeps the account that opens a pull request, as on any repository.
