# Zapret Updater

<!-- audion:release -->
<p align="center">
  <a href="https://audion.dev/downloads/zapret-updater"><img alt="Windows" src="https://img.shields.io/badge/Windows-10%20%7C%2011-0b6db8?style=flat-square&logo=windows&logoColor=white"></a>
  <a href="https://github.com/Tensionix/zapret-updater/releases/latest"><img alt="Release" src="https://img.shields.io/github/v/release/Tensionix/zapret-updater?style=flat-square&label=release&color=e08a63"></a>
  <a href="https://github.com/Tensionix/zapret-updater/releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/Tensionix/zapret-updater/total?style=flat-square&label=downloads&color=5fd08a"></a>
  <a href="https://github.com/Tensionix/zapret-updater/blob/main/LICENSE"><img alt="License" src="https://img.shields.io/github/license/Tensionix/zapret-updater?style=flat-square&color=5fd08a&logo=apache&logoColor=white&cacheSeconds=3600"></a>
</p>

**Version 1.0.0** · 2026-08-25 · 395 KB

- [Direct download](https://audion.dev/get/zapret-updater/1.0.0/Audion_Zapret_Updater_v1.0.0_Full.zip) — unmetered, no rate limits
- [Project page](https://audion.dev/downloads/zapret-updater) — every version and how to install

`SHA-256: 161d122a05ca87a25d52196e64bf603eaa0d17307022d4c957441106042b2a3f`

---

An **Audion** tool, published by [Tensionix](https://github.com/Tensionix).
<!-- /audion:release -->

Installs and updates [zapret-discord-youtube](https://github.com/Flowseal/zapret-discord-youtube)
in one press: it fetches the current release, removes the driver, puts the new
version in place of the old one and brings your domain lists back.

The rule is simple: **if a Zapret folder is next to it, update that one; if not,
install from scratch**. Nothing is asked.

## How to use it

If Zapret is already installed, place this folder beside it:

```
D:\Internet\
    zapret-discord-youtube\      ← Zapret itself
    Zapret Updater\              ← this folder
```

If Zapret is not there yet, simply put this folder wherever you want to keep it
and run it. The `zapret-discord-youtube` folder will appear beside it by itself.

Run **Обновить Zapret.cmd**. If Zapret happens to be running, Windows will ask
about administrator rights — without them the driver cannot be removed, and while
it is loaded the old files cannot be replaced. If Zapret is stopped, nothing is
asked.

There is nothing else to do. At the end the window reports what happened and
waits for a key press.

The Zapret folder is looked for nearby only: inside itself, among its neighbours
and one level up. It deliberately does not search further across the drives —
otherwise, instead of installing, you could accidentally update someone's
forgotten copy. Nothing is written down or remembered anywhere: the kit is
portable and decides by what lies beside it right now. If Zapret is off to one
side, name it at startup:
`Обновить Zapret.cmd -Path "D:\somewhere\zapret"`.

It installs the new folder **beside itself**, not inside: if the utility's folder
holds nothing but its own files, Zapret will appear one level up, as a neighbour.
Inside the updater it must not go — there the first folder replacement would
carry it away.

## What happens inside

1. It compares the version in your `service.bat` with the latest release on
   GitHub. If the version is the same, it says so and exits. If Zapret was not
   found, it installs a fresh one from scratch, and then the steps about the
   driver and the lists are simply skipped.
2. **The archive is downloaded first** — while Zapret is still running. Do it the
   other way round and GitHub may not open at all; that is what Zapret is there
   for.
3. It stops `winws.exe`, removes the `zapret` service and the WinDivert driver.
4. It unpacks the archive: inside is a folder with the version in its name
   (`zapret-discord-youtube-1.10.0`), and its contents go into your folder — under
   the previous name, without the version.
5. It carries the `lists\*-user.txt` files into the new version — the very ones
   your own domains are added to. The other lists arrive updated.
6. The previous contents of the folder are deleted entirely; no copies are left
   beside it.

> **The `zapret-discord-youtube` folder belongs to Zapret entirely.** Whatever
> lies in it will be wiped and replaced by the new release, except for the
> `lists\*-user.txt` lists. Do not keep anything of your own there.

That is deliberate: the folder can be empty, half-downloaded or chewed up by an
antivirus — Defender likes to remove `bin\winws.exe` as a "HackTool". There is no
point working out what exactly broke: a fresh release fixes any of these cases.

If the driver did not let go (which happens when another program holds it), the
replacement is deferred until the next Windows boot — it will substitute the
files itself, and nothing has to be run a second time.

## If Zapret was installed as a service

The service is removed during the update — otherwise the files cannot be
replaced. The script says so at the end; install it again through `service.bat`
if you use autostart.

## Switches, for those who need them

| Command | What it does |
| --- | --- |
| `Обновить Zapret.cmd` | the ordinary update |
| `Обновить Zapret.cmd -CheckOnly` | only compare the versions, touch nothing |
| `Обновить Zapret.cmd -Force` | install the same version again |
| `Обновить Zapret.cmd -Restart` | reboot right away if the driver is stuck |
| `Обновить Zapret.cmd -Path "D:\zapret"` | name the folder by hand |

It works both on the built-in PowerShell 5.1 and on PowerShell 7 — whichever is
present on the system.
