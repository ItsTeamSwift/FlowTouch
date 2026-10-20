# FlowTouch

[Открыть сайт](https://itsteamswift.github.io/FlowTouch/) · [FlowTouch Studio](https://itsteamswift.github.io/FlowTouch/studio/)

Управление компьютером жестами. Отдельные страницы: лендинг `/`, студия `/studio/`.

## Запустить программу Windows

1. Скачайте [FlowTouch.exe](https://github.com/ItsTeamSwift/FlowTouch/raw/refs/heads/main/public/downloads/FlowTouch.exe).
2. Запустите файл — откроется локальная студия. Python не нужен.
3. Подключите камеру и нажмите **Начать управление Windows**.
4. Удерживайте жест до **100% прогресса**. Уверенность модели показана отдельно и не обязана быть 100%.

Кулак по умолчанию открывает YouTube. Можно выбрать Калькулятор, Блокнот или Проводник. Escape останавливает команды. Закрытие окна программы завершает работу.

В браузерной версии доступны распознавание и тренировка; запуск программ требует локальной версии. Видео обрабатывается локально. Звук выключен по умолчанию.

## Разработка

```sh
npm ci
npm run dev
npm test
npm run build
```

Для сборки EXE на Windows: `python -m pip install pyinstaller==6.16.0`, затем `python scripts/build_desktop.py`. Backend: `companion/flowtouch.py`.

32 команды: 12 поз, 4 свайпа, 16 связок. Краткая потеря распознавания до 220 мс не сбрасывает удержание. Связки выполняются отдельным режимом. Распознавание экспериментальное, качество зависит от света и положения кисти.

Vite, Tailwind, Motion, Three.js, MediaPipe. Модель руки: WebXR Input Profiles, MIT (public/models/HAND-LICENSE.md). Inter Tight: SIL OFL (public/fonts/OFL.txt). MediaPipe: Apache-2.0.

## GitHub Pages

Workflow `.github/workflows/deploy.yml` собирает и публикует сайт после push в `main`. В Settings → Pages нужно выбрать Source: **GitHub Actions**. Для локальной сборки используется `/`, в Pages — `/FlowTouch/`. Камера работает через HTTPS; запуск программ доступен в FlowTouch.exe.
