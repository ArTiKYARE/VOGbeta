# ВОГВОЯЖ ✈️🌅

Одностраничный сайт шуточной авиакомпании «Вогвояж» — для съемки ролика и QR-интерактива в зале.

## Как запустить
Просто откройте `index.html` в браузере (или залейте папку на любой статический хостинг).

## Что заменить перед продакшеном
| Что | Где |
|---|---|
| Фоновый ролик в hero | файл `/assets/vogvoyazh-ad.mp4` (пока — анимированный розовый placeholder) |
| Рекламный ролик | файл `/assets/vogvoyazh-commercial.mp4` |
| Настоящий QR-код | сгенерируйте по ссылке вида `https://ваш-домен/#zal` и положите в `/assets/qr-vogvoyazh.svg`, затем замените inline-SVG в секции `#qr` на `<img src="/assets/qr-vogvoyazh.svg">` |
| Real-time табло | в JS: `SUPABASE_URL` / `SUPABASE_KEY` + таблица `flights` (SQL в комментарии). Без ключей работает локальный демо-режим (localStorage) |

## Ссылки для зала
- Интерактив напрямую: `…/#zal` или `…/#qr-interactive`
- Табло ведущего: `…/#board`

## Технологии
Single-file HTML + CSS + vanilla JS. CDN: Playfair Display/Manrope, html2canvas (сохранение талона в PNG, fallback — печать), supabase-js (опционально). Mobile-first, glassmorphism, prefers-reduced-motion, print-стили только для талона.
