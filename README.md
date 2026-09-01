# Audion Zapret Updater

<!-- audion:release -->
<p align="center">
  <a href="https://audion.dev/downloads/zapret-updater"><img alt="Windows" src="https://img.shields.io/badge/Windows-10%20%7C%2011-0b6db8?style=flat-square&logo=windows&logoColor=white"></a>
  <a href="https://github.com/Tensionix/zapret-updater/releases/latest"><img alt="Release" src="https://img.shields.io/github/v/release/Tensionix/zapret-updater?style=flat-square&label=release&color=e08a63"></a>
  <a href="https://github.com/Tensionix/zapret-updater/releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/Tensionix/zapret-updater/total?style=flat-square&label=downloads&color=5fd08a"></a>
  <a href="https://github.com/Tensionix/zapret-updater/blob/main/LICENSE"><img alt="License" src="https://img.shields.io/github/license/Tensionix/zapret-updater?style=flat-square&color=5fd08a&logo=apache&logoColor=white&cacheSeconds=3600"></a>
</p>

**Версия 1.0.2** · 2026-09-02 · 177 KB

- [Скачать напрямую](https://audion.dev/get/zapret-updater/1.0.2/Audion_Zapret_Updater_v1.0.2_Full.zip) — быстрая раздача, без ограничений
- [Страница проекта](https://audion.dev/downloads/zapret-updater) — все версии и установка

`SHA-256: 2ae81ae34d77abf8e63651b2340dc21b5315d08093c4fd850704ec6b2ce26635`

---

Проект набора **Audion** — издаёт [Tensionix](https://github.com/Tensionix).
<!-- /audion:release -->


[Русский](README_RU.md)

Installs and updates a traffic-filtering bypass tool with one click.

## Why It Exists

Updating such a tool is not "download the new version". You have to stop the
service, remove the driver, put the new build in place of the old, restore your
own domain lists, and start it back up. Miss a step and you have a broken setup
and an opaque error.

## The Rule

**A folder is there — update it. It is not — install from scratch.**

No questions, no mode selection: the program looks at what is already present and
does what is needed.

## What Is Preserved

**Your domain lists.** They are restored after the update — otherwise updating
would mean configuring everything again.

## Next

* Installation and running — one file, no parameters.
