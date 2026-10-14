<p align="center">
  <img src="./VGuessTheBuild-banner.svg" alt="VGuessTheBuild — Vack Studio" width="100%">
</p>

# VGuessTheBuild | Vack Studio

A building and guessing minigame with six manually configured Minecraft arenas. Version **1.8.0**. The product name is consistently **VGuessTheBuild**; **VMusic** and **VPackEngine** remain separate companion plugins.

## Gameplay and entry

- Direct arena commands `/gb1` through `/gb6`, including `/gb2`; joining opens no general menu.
- Separate capacity queues through `/gb game 4`, `/gb game 8`, `/gb game 16` or `/gb game 4 2`. Default configured sizes are 4, 6, 8 and 16 with 75% start thresholds of 3, 5, 6 and 12.
- Random builder turns, chat topic selection, guesses, hints and scoring. The inventory interface is reserved for cosmetics.
- English and العربية, selected explicitly through `/gb language` or `/gb language en|ar`, with saved UUID preferences.
- Player state restoration, existing rewards and cosmetic transactions.
- Optional VMusic 1.7.0 native NBS waiting loop and cues; native audio fallback remains available.
- Existing worlds and manually positioned arenas. No map or world generation is supplied.

## VPackEngine integration

VGuessTheBuild uses VPackEngine's public service and guarded menu events. Its 1.1.0-preview.2 context API supports waiting/game profiles, per-arena overrides, a cosmetic profile, current-session resource readiness and removal of game-owned contexts on exit. Closing the cosmetic menu removes its higher-priority context. Delayed or superseded results cannot reopen a stale menu.

Cosmetics choose separate English/Arabic engine menus according to the game's saved language and reuse the existing purchases and prices. Missing engines, unavailable resources or menus use the standard cosmetic inventory. The older engine API can open already-ready menus, but does not automatically apply profiles that it cannot remove. Pack requirements remain administrator-configured in VPackEngine; the integration itself does not force downloads or create artwork.

## Requirements and setup

Target: **Paper 26.2 build 133 / Java 25**. Optional integrations: **VPackEngine 1.1.0-preview.2** for owned profiles, **VMusic 1.7.0** for its waiting track and **VHeads 1.0.1** for head management. Leaf, Folia and Bedrock compatibility are unverified.

Stand at each chosen location and run `/gb setwaiting <arena>`, `/gb setlobby <arena>`, `/gb setgame <arena>` and `/gb setspectator <arena>`. Use `/gb setpos1 <arena>` and `/gb setpos2 <arena>` for bounds. Administrative setup and `/gb pack` diagnostics require `gb.admin`. VPackEngine menus require `vpack.use`.

Configure profile/menu names under `integrations.vpackengine`, create those profiles in the engine and merge the supplied bilingual cosmetic menu examples into its existing configuration. Reload each plugin with arenas empty. Rewards, prices, SQLite data, UUID languages, snapshots and arena coordinates preserve their identities.

## Verification

Private Java 25 CI built the real plugin and passed **24 tests** with zero failures, errors or skips, including API compatibility, owned context removal operations, readiness/failure forwarding, UUID request isolation, supersession and lifecycle invalidation. JAR inspection confirms Java 25 bytecode, the VPackEngine soft dependency and no bundled Paper or VPackEngine API classes. Compilation/service checks do not prove real-client resource downloads, visual rendering, audible playback or multiplayer cleanup; those require two connected clients and the owner's plugin stack. No live server was modified in this update.

## العربية

**VGuessTheBuild** هو الاسم الموحّد للبلوجن من **Vack Studio**، وإصداره **1.8.0**. الدخول مباشر بـ`/gb2` أو `/gb game 4 2`، والـGUI مخصص للتجميل. لا يوجد ماب؛ تحدد مواقع الساحات الست بنفسك.

التكامل مع **VPackEngine** يربط بروفايلات باكات الانتظار واللعبة لكل ساحة، ويفتح قائمة التجميل بالعربية أو الإنجليزية حسب لغة اللاعب المحفوظة. يحتاج الربط الكامل إصدار المحرك **1.1.0-preview.2**. إذا الباك أو القائمة غير جاهزين تظهر القائمة العادية، وعند الخروج تُزال سياقات الباكات الخاصة باللعبة. الأسعار والجوائز وبيانات اللاعبين محفوظة كما هي.

اجتاز الإصدار 24 اختبارًا والبناء على Java 25. تجربة الباكات والشكل والصوت مع لاعبين متصلين ما زالت مطلوبة؛ اختبارات الكود لا تعني اكتمال اختبار اللعب الفعلي.

## Availability and rights

This repository is an introduction only. Source, plugin binaries, checksums and download releases are not published here. The owner supplies compiled files privately.

Copyright (c) Vack Studio. All rights reserved. Third-party components retain their own rights.
