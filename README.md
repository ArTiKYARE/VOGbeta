# ВОГВОЯЖ ✈️🌅

Одностраничный сайт шуточной авиакомпании «Вогвояж» — для съемки ролика и QR-интерактива в зале.

## Как запустить
Просто откройте `index.html` в браузере (или залейте папку на любой статический хостинг).

## Публикация на GitHub (пошагово)

### 1. Создать репозиторий
На GitHub нажмите **New repository** → имя, например `vogvoyazh` → **Public** → Create.
Или через CLI:
```bash
gh repo create vogvoyazh --public --source=. --push
```

### 2. Отправить код (обычный git)
```bash
cd /workspace
git checkout -b main            # если ещё не на main
git add .
git commit -m "feat: VOGVOYAZH pink airline site with QR boarding-pass interactive"
git remote add origin https://github.com/ВАШ_ЛОГИН/vogvoyazh.git
git push -u origin main
```
> Если GitHub просит пароль — используйте **Personal Access Token**
> (Settings → Developer settings → Tokens, scope `repo`) или `gh auth login`.

### 3. Включить GitHub Pages (бесплатный хостинг)
Репозиторий → **Settings → Pages → Source: Deploy from a branch → `main` / root → Save**.
Сайт будет доступен по адресу:
```
https://ВАШ_ЛОГИН.github.io/vogvoyazh/
```

### 4. Подготовить QR-код для зала
Откройте полученный адрес с суффиксом `#zal`, например:
```
https://ВАШ_ЛОГИН.github.io/vogvoyazh/#zal
```
Сгенерируйте QR для этой ссылки (например, на qr-code-generator.com, цвета: тёмный код `#2A0F1D` на белом фоне) и замените файл `assets/qr-vogvoyazh.svg`.

### Структура репозитория
```
├── index.html              # весь сайт (HTML + CSS + JS в одном файле)
├── assets/
│   └── qr-vogvoyazh.svg    # QR-placeholder → заменить на настоящий
│   └── vogvoyazh-ad.mp4          # ← сюда положить фоновый ролик для hero
│   └── vogvoyazh-commercial.mp4  # ← сюда положить рекламный ролик
└── README.md
```

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
