---
name: Онлайн-утилиты для разработки
overview: Краткий обзор стека message-server и подборка веб-сервисов по категориям (API, очереди, БД, WebSocket, телефония, безопасность, фронтенд), которые ускоряют отладку и проектирование такого проекта.
todos: []
isProject: false
---

# Онлайн-утилиты для разработки message-server

## Что за проект (для привязки инструментов)

По корневому [package.json](package.json) и [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md): монорепозиторий **npm workspaces**, сервисы на **Node.js + Express**, **MongoDB** (Mongoose), **Redis** + **BullMQ**, **RabbitMQ**, **WebSocket** (`ws`), внешние каналы (**Telegram**, **WhatsApp/WABA**, **MAX**, SMS), **Bitrix24**, телефония (**vpbx**), **STT**, UI на **AngularJS/Webpack** и отдельные пакеты на современном стеке. API документируется через **OpenAPI/Swagger** ([packages/chat-api/index.js](packages/chat-api/index.js), правило в [AGENTS.md](AGENTS.md): Swagger 2.0).

Ниже — не «обязательный стек», а **полезные веб-утилиты**, сгруппированные по задачам разработки.

---

## API, схемы и контракты

- **[Swagger Editor](https://editor.swagger.io/)** — правка и валидация **Swagger 2.0** перед/параллельно с `express-openapi`.
- **[Stoplight Studio](https://stoplight.io/)** (веб/десктоп) — дизайн и ревью OpenAPI, моки для фронта.
- **[Postman](https://www.postman.com/)** / **[Insomnia](https://insomnia.rest/)** (облако/коллекции) — сохранённые запросы к `chat-api`, `channels-api`, `auth`, заголовки JWT, окружения dev/stage.
- **[Hoppscotch](https://hoppscotch.io/)** — лёгкий браузерный REST + WebSocket-клиент без установки.
- **[JSON Crack](https://jsoncrack.com/)** / **[jsonformatter.org](https://jsonformatter.org/)** — разбор больших JSON-ответов от внешних API и внутренних сервисов.

---

## JWT, крипто, кодирование

- **[jwt.io](https://jwt.io/)** — декодирование/проверка структуры **JWT** (без доверия секретам в публичных полях).
- **[CyberChef](https://gchq.github.io/CyberChef/)** — Base64, hex, хэши, простые преобразования полезны при отладке webhook-пейлоадов и логов.

---

## WebSocket и потоковые протоколы

- Встроенный WebSocket в **Hoppscotch** или **[websocketking.com](https://websocketking.com/)** — ручная проверка событий к **ws-server** без написания клиента.

---

## Очереди и брокеры

- Облачные песочницы **CloudAMQP** (если нужен временный RabbitMQ без своего Docker) — для проверки публикации/подписки в стиле вашего **amqplib**-кода.
- Для **Redis/BullMQ**: онлайн-калькуляторы TTL и форматов ключей редки; обычно полезнее **Redis Insight** (не чисто веб, но есть облако) или **Upstash Redis Console** при использовании их облака — оставляю как опцию, если Redis в облаке.

---

## MongoDB и данные

- **[MongoDB Query Playground](https://mongoplayground.net/)** — быстрая проверка запросов/агрегаций на тестовых документах (аналогично логике Mongoose-пайплайнов).
- **[ObjectId generators / time extractors](https://observablehq.com/@hugodf/mongodb-objectid-timestamp)** (любой проверенный мини-сайт) — связь `ObjectId` ↔ время создания при разборе логов.

---

## Телефония и идентификаторы

- Учитывая **libphonenumber-js**: **[libphonenumber.appspot.com](https://libphonenumber.appspot.com/)** (Google demo) — валидация и формат номеров для SMS/WhatsApp-сценариев.

---

## Регулярные выражения, cron, даты

- **[regex101.com](https://regex101.com/)** — разбор парсинга логов и строковых форматов.
- **[crontab.guru](https://crontab.guru/)** — если появятся scheduled-джобы (BullMQ repeat, cron в инфраструктуре).

---

## Фронтенд (AngularJS + Webpack, отдельно Vue/TS UI)

- **[Can I use](https://caniuse.com/)** — совместимость браузеров для легаси-админки.
- **[Bundlephobia](https://bundlephobia.com/)** — оценка веса новых npm-зависимостей перед добавлением в webpack-сборки.

---

## Безопасность и приватность

- **[OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)** (справочник, не «утилита», но онлайн) — чеклисты для API с сессиями/JWT и загрузкой файлов (`express-fileupload`).
- **Pastebin с приватностью / внутренний paste** — обмен фрагментами логов без утечки токенов (важно: не светить секреты в публичных сервисах).

---

## Инфраструктура и совместная работа

- **[Excalidraw](https://excalidraw.com/)** / **[diagrams.net](https://app.diagrams.net/)** — схемы потоков «мессенджер → channels-api → RabbitMQ → worker» как в [ARCHITECTURE.md](docs/ARCHITECTURE.md).
- **[Mermaid Live Editor](https://mermaid.live/)** — те же диаграммы в виде кода (удобно для PR и docs).

---

## Резюме по приоритету для этого репозитория

Наибольшую отдачу обычно дают связка **Postman/Hoppscotch + Swagger Editor + jwt.io + WebSocket-клиент + Mongo Playground + libphonenumber** — они напрямую закрывают типичные точки отладки вашего стека без установки тяжёлых IDE-плагинов.

Если нужно, после согласования плана можно сузить список под одну роль (например, только backend-интеграции или только фронт).





----------------

1. swagger ui, editor
- 2. json viewer, beautifier
- 3. jwt parser, encoder
4. http request tools - post endpoint, get endpoint, request url
- 5. mermaid viewer
6. websocket server / client
7. unixtimestamp (converter)

