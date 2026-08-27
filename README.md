# DO NOT USE THIS BRANCH TO COMPILE {PROTON,WINE}-TKG
<sub>You've been warned! But you can if you want, just I won't be able to fully assist 🐸</sub>

This is my personal base branch for rebases and/or action workflows for testing patches that I do not personally use and/or do not have the capacity to utilize them fully. A lot of bad and silly stuff will go on here, including but not limited to: forced pushes, broken patches, missing files, dirty repo tree, messed up file structure and so on. Basically expect a lot of frogging up to happen here 🐸

<sub>Let me know if I accidentally opened a pr with this branch, it most definitely is a mistake in that case</sub>

Although I doubt anyone will want to pick this repo and branch one up for themselves and work off of that, the general workflow for this branch is:

1. Branch off from here, aka `DO_NOT_USE_BREAKAGES_HAPPEN_HERE`
2. Rebase a patch and/or make other changes
3. Trigger a CI/CD (see `.github/workflows` directory for available ones) or fire it manually and see if it applies patches correctly and compiles (although there may be limitations wrt compilation)
4. Amend changes if applicable by force pushing or adding more commits to a branch on top fixing up a broken change (doesn't matter really but force push will result in a cleaner tree)
5. Go back to point 3 and repeat until stuff works
6. Branch off from the main branch, aka `master`
7. Save a patch from a branch based on `DO_NOT_USE_BREAKAGES_HAPPEN_HERE`, or pick commit(s) and insert into the branch that is branched off of main branch
8. Submit changes upstream
9. ???
10. Profit!

---

# Wine to rule them all !

You must be logged in to GitHub in order to download Wine or Proton nightly builds.

## Wine nightly builds

- wine-staging patchset applied
- ntsync support added as needed

Wine | [Arch Linux](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/wine-arch.yml) | [Fedora](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/wine-fedora.yml) | [Ubuntu](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/wine-ubuntu.yml) |
-------------|--------|--------|-------|

Valve Wine | [Exp Bleeding Edge Arch Linux](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/wine-valvexbe-pacman.yml) | [Exp Bleeding Edge Other distro](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/wine-valvexbe.yml) |
-------------|--------|--------|

*The Exp Bleeding Edge Other distro versions are built on Ubuntu latest, which should work fine on most distros not using years old packages*

## Proton nightly builds

- wine-staging patchset applied
- wine master version is built against Arch current, making glibc 2.42+ a requirement
- valve exp be version is built against the sniper container
- ntsync support added as needed

Proton | [Valve Exp Bleeding Edge](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/proton-valvexbe-sniper.yml) | [Wine Master (hit or miss edition)](https://github.com/Frogging-Family/wine-tkg-git/actions/workflows/proton-arch-nopackage.yml) |
-------------|--------|--------|

(drop the extracted folder in `/$HOME/.steam/root/compatibilitytools.d/` or, for Ubuntu/Debian based, the `/$HOME/.steam/compatibilitytools.d/` dir)

## PLEASE DO NOT REPORT BUGS ENCOUNTERED WITH THIS AT WINEHQ OR VALVESOFTWARE, REPORT HERE INSTEAD !

Wine-tkg is a build-system aiming at easier custom wine builds creation. You can now easily get the "plain wine + pba + steam fix" build you've been dreaming about!

It can also make custom Proton builds with its wrapping script: https://github.com/Frogging-Family/wine-tkg-git/tree/master/proton-tkg

**By default, it'll pull current wine/wine-staging git versions. You can target a specific release or commit in the .cfg if needed.**

A comfortable selection of patches is available to you, with some of them being enabled by default for your convenience (see [this sample config file](https://github.com/Frogging-Family/wine-tkg-git/blob/master/wine-tkg-git/wine-tkg-profiles/sample-external-config.cfg) for the full list and details)

An ever evolving selection of staging, experimental and/or hacky patches are also available [in the community-patches](https://github.com/Frogging-Family/community-patches/tree/master/wine-tkg-git)

**Can be built with your own patches - See [README in wine-tkg-git/wine-tkg-userpatches](https://github.com/Frogging-Family/wine-tkg-git/blob/master/wine-tkg-git/wine-tkg-userpatches/README.md) for instructions**

### Generated Wine-tkg sources (staging-based):
 - Wine-tkg : https://github.com/Tk-Glitch/wine-tkg
 - Proton-tkg : https://github.com/Tk-Glitch/wine-proton-tkg

Wine : https://github.com/wine-mirror/wine

Wine-staging : https://github.com/wine-staging/wine-staging

Wine esync : https://github.com/zfigura/wine/tree/esync

Wine fsync : https://github.com/zfigura/wine/tree/fsync

Proton : https://github.com/ValveSoftware/Proton

Wine-pba (Only working correctly up to 3.18 - Force disabled on newer wine bases due to regressions) : https://github.com/acomminos/wine-pba

Thanks to @Firerat and @bobwya for their rebase work :
- https://gitlab.com/Firer4t/wine-pba
- https://github.com/bobwya/gentoo-wine-pba

For Gallium 9 support, use https://github.com/iXit/wine-nine-standalone (available from winetricks and AUR) - Legacy nine support can still be turned on if you're building a 4.1 base or older.
