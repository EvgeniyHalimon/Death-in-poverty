Senior Back-End Engineer: полный список навыков
Node.js / NestJS / TypeScript / MySQL
Как читать этот документ
• Только уровень Senior. Всего 56 навыков, из них 22 с меткой KEY. Lead, Middle и уровни ниже Senior убраны.
• Разделы идут в порядке матрицы, внутри раздела KEY стоят первыми.
• У каждого навыка три блока: что нужно знать, на что обратить внимание, и (для KEY) какие артефакты нужно предъявить.
• Результат KEY-навыков оценивается по артефактам: код, отчёты, документы и стандарты, принятые командой. Одного знания недостаточно, нужно оставить след в репозитории.
• Практика: вести всё в одном учебном NestJS-репозитории с MySQL, чтобы конфиги, гайдлайны и отчёты лежали в одном месте.
1. Язык (JavaScript / TypeScript, Node.js)
1. Apply methodology and best practices for language performance optimisation (KEY)
• Знать: профилирование (--inspect, clinic.js, 0x), event loop и блокирующие операции, сборка мусора и утечки памяти, горячие пути, лишние аллокации, микробенчмарки.
• Внимание: сначала измерять, потом оптимизировать; оптимизация без цифр до/после не засчитывается.
• Артефакты: код с оптимизациями, отчёты замеров, практики, принятые командой.
2. Build client-server applications using network protocols (KEY)
• Знать: TCP/UDP, HTTP/1.1 и HTTP/2, WebSocket, TLS, модули net / http / http2 в Node.js, keep-alive, таймауты, backpressure.
• Внимание: обрывы соединений, таймауты на всех уровнях, ограничения размера тела запроса, корректное закрытие сокетов.
• Артефакты: код клиента и сервера, документ с описанием протокола и решений.
3. Optimise application performance taking into account the complexity of the algorithms (KEY)
• Знать: Big O, выбор структуры данных (Map, Set, массив), сортировка и поиск, амортизированная сложность, N+1 как алгоритмическая проблема.
• Внимание: проверять на реальных объёмах данных, а не на тестовых десятках записей.
• Артефакты: рефакторинг с обоснованием сложности, отчёт до/после.
4. Secure network interaction using a programming language (KEY)
• Знать: TLS/HTTPS, сертификаты, mTLS, CORS, CSRF, helmet, JWT и сессии, rate limiting, валидация входных данных, OWASP Top 10.
• Внимание: не отключать проверку сертификатов, не хранить секреты в коде, следить за уязвимостями зависимостей (npm audit).
• Артефакты: защищённый код взаимодействия, документ с политикой безопасности, принятый командой.
5. Implement concurrency concepts by using language capabilities
• Знать: event loop, async/await, Promise.all / allSettled / race, worker_threads, cluster, AsyncLocalStorage.
• Внимание: race conditions в асинхронном коде, не блокировать event loop тяжёлыми вычислениями.
6. Manage advanced collections of data using language
• Знать: Map, Set, WeakMap, WeakSet, типизированные массивы, итераторы и генераторы, методы массивов.
• Внимание: сложность операций и расход памяти, выбор коллекции под задачу.
7. Manage and implement complex data structures
• Знать: деревья, графы, очереди, heap, trie, LRU-кэш; реализация с нуля и выбор готовой.
• Внимание: уметь объяснить сложность операций и границы применимости.
8. Synchronise concurrent operations by using language capabilities
• Знать: мьютексы и семафоры (async-mutex), Atomics и SharedArrayBuffer, очереди, блокировки на уровне БД, идемпотентность.
• Внимание: deadlock и порядок захвата блокировок, различие между синхронизацией в процессе и между процессами.
9. Use language metaprogramming techniques
• Знать: Proxy, Reflect, Symbol, декораторы TypeScript, reflect-metadata (на этом построен NestJS), геттеры и сеттеры.
• Внимание: метапрограммирование усложняет чтение и отладку и влияет на производительность; применять там, где оно окупается.
2. Библиотеки
10. Use libraries for logging (KEY)
• Знать: pino и nestjs-pino, winston, pino-http, morgan, express-winston; структурированные логи, уровни, request ID через AsyncLocalStorage или nestjs-cls, redact чувствительных данных.
• Внимание: не логировать секреты и персональные данные; одинаковый формат во всех модулях; делать и для NestJS, и для Express.
• Артефакты: структурированное логирование в модулях, рефакторинг уровней и форматов, документ с гайдлайнами логирования для команд, образцовые модули.
11. Configure bundlers for applications
• Знать: esbuild, tsup, webpack, rollup; target, sourcemaps, external, tree shaking.
• Внимание: нативные модули и зависимости, которые нельзя бандлить; проверять, что собранный артефакт реально запускается.
3. Фреймворк (NestJS)
12. Apply caching techniques to increase the performance of data retrieval (KEY)
• Знать: cache-aside, TTL, инвалидация, Redis (ioredis), @nestjs/cache-manager.
• Внимание: cache stampede, консистентность данных, продуманные ключи; кэш без правил инвалидации опаснее его отсутствия.
• Артефакты: кэш-слой в компонентах доступа к данным, рефакторинг получения данных с правилами инвалидации, документ со стратегией и гайдлайны, отчёт латентности до/после.
13. Apply performance optimization techniques using framework capabilities (KEY)
• Знать: профилирование (clinic.js, 0x), scopes провайдеров (Default и Request), Fastify-адаптер, lifecycle, нагрузочное тестирование (autocannon, k6), Prometheus и Grafana.
• Внимание: request-scoped провайдеры дороги и «заражают» зависимые; оптимизировать по замерам.
• Артефакты: оптимизированные компоненты, рефакторинг конфигурации и lifecycle, benchmark-отчёт до/после, дашборд мониторинга производительности.
14. Build real-time network APIs using a framework
• Знать: WebSocket Gateway, SSE, Socket.IO; авторизация соединений, масштабирование (Redis adapter).
• Внимание: переподключения, потеря сообщений, нагрузка при большом числе соединений.
15. Manage advanced communication protocols with a framework
• Знать: gRPC, транспорты microservices в NestJS (RabbitMQ, Redis pub/sub), GraphQL.
• Внимание: контракты и версионирование, обработка ошибок на границах сервисов.
16. Use framework to handle large datasets
• Знать: streams, курсорная пагинация, batch-обработка, backpressure.
• Внимание: не загружать весь набор данных в память; deep OFFSET-пагинация деградирует.
17. Use framework to perform high-performance computing tasks
• Знать: worker_threads, cluster, BullMQ, вынос CPU-bound задач из основного процесса.
• Внимание: накладные расходы на передачу данных между потоками, ограничение числа воркеров.
18. Work with process and environment using framework capabilities
• Знать: graceful shutdown (enableShutdownHooks, SIGTERM), @nestjs/config, process.env, сигналы, коды выхода.
• Внимание: корректное завершение с закрытием соединений и дренажем очередей.
4. Code-Based Testing
19. Configure and maintain code coverage reports (KEY)
• Знать: Jest --coverage, провайдеры v8 и babel, collectCoverageFrom, исключения, coverageThreshold, шаг в CI с отчётом артефактом, документ с правилами.
• Внимание: покрытие не равно качеству тестов; исключения должны быть обоснованы и описаны.
• Артефакты: coverage-конфиг в репозитории, автогенерация отчёта в билде, правила и исключения в конфигах, отчёты на регулярном ревью.
20. Configure test frameworks and tools for test execution (KEY)
• Знать: раздельные конфиги unit, integration и e2e, .env.test, Docker Compose или Testcontainers для MySQL, режимы local и CI, единый скрипт запуска, runbook.
• Внимание: изоляция и детерминизм тестов, независимость от порядка запуска.
• Артефакты: общий test-setup, переиспользуемые конфиг-модули, опубликованные гайдлайны, runbook. NEBo-таск «Configure a test execution environment»: изолированное окружение, 3–5 env-настроек, 5+ осмысленных тестов, два режима (local и CI), скрипт запуска, сохранённые отчёты, документация.
• Совет: делать вместе с coverage на одном проекте, ориентир — недели 1–2.
5. Application Design
21. Distribute and optimise responsibility between structures using design patterns (KEY)
• Знать: SOLID, GRASP, Strategy, Observer, Command, Chain of Responsibility, Mediator.
• Внимание: паттерн не самоцель, избегать over-engineering; фиксировать компромиссы.
• Артефакты: рефакторинг модулей с чёткими границами ответственности (удобно взять модуль своей ORM), ADR с trade-offs, гайдлайн по выбору паттернов, примеры из код-ревью.
22. Ensure efficient and flexible composition of structures using design patterns (KEY)
• Знать: Adapter, Decorator, Facade, Composite, Proxy, Bridge; композиция вместо наследования; DI и interceptors в NestJS.
• Внимание: цепочки декораторов усложняют отладку; композиция должна упрощать расширение.
• Артефакты: применение паттернов в нескольких компонентах, ADR, примеры из ревью.
23. Use methodologies and techniques to document design (KEY)
• Знать: C4, UML, Mermaid и PlantUML в репозитории, ADR, design doc, TSDoc.
• Внимание: документация лежит рядом с кодом и обновляется через PR; диаграммы должны отвечать на конкретные вопросы.
• Артефакты: структурированный design doc в репозитории, диаграммы компонентов, design review notes.
24. Evaluate and modify software design to ensure quality
• Знать: метрики coupling, cohesion, cyclomatic complexity, code smells, ESLint complexity, madge (циклические зависимости), SonarQube.
• Внимание: метрики подсказывают, где смотреть, но не заменяют суждение.
25. Use modeling techniques for requirements analysis
• Знать: use cases, user stories, BPMN, основы DDD.
• Внимание: выбирать модель под задачу, не рисовать диаграммы ради диаграмм.
26. Validate requirements using various methodologies and techniques
• Знать: ревью требований, BDD (Given-When-Then), трассируемость требований к тестам.
• Внимание: требования должны быть проверяемыми и измеримыми.
• Совет: ориентир по срокам — недели 3–5 паттерны, неделя 6 документация, недели 7–8 не-KEY навыки дизайна.
6. Процессы и DevOps
27. Configure contribution workflow using version control tools (KEY)
• Знать: GitHub Flow или trunk-based, Conventional Commits, branch protection, CODEOWNERS, шаблоны PR и issue, husky + lint-staged + commitlint, CONTRIBUTING.md.
• Внимание: правила должны проверяться автоматически, а не держаться на договорённостях; обязательные проверки перед merge.
• Артефакты: конфиги репозитория с правилами веток и ревью, автопроверки в VCS-workflow, документ contribution guidelines, audit trail.
28. Handle environment variables and secrets (KEY)
• Знать: 12-factor, @nestjs/config с валидацией схемы (Joi или zod), .env.example, gitleaks и trufflehog, secret scanning в CI, GitHub Actions secrets, Vault или AWS Secrets Manager.
• Внимание: секрет, попавший в git, считается скомпрометированным: его нужно перевыпустить, а не просто удалить из истории; конфиг падает на старте при отсутствии обязательных переменных.
• Артефакты: централизованный config-модуль для env и секретов, рефакторинг захардкоженных значений, гайдлайн по секретам, audit report рисков конфигурации.
29. Set up a code review process to ensure application quality (KEY)
• Знать: политика ревью с критериями и ролями, чеклист в PR-template, обязательный peer review, размер PR, тон комментариев.
• Внимание: ревью должно ловить дизайн и риски, а не только стиль (стиль закрывают линтеры); нужны метрики и обратная связь.
• Артефакты: политика ревью, чеклист-шаблон, workflow с обязательным peer review, сводный отчёт по находкам (разбор 5–10 чужих PR).
30. Configure a build process to produce deployable applications
• Знать: nest build, multi-stage Dockerfile, запуск не от root, healthcheck, публикация образа в GHCR.
• Внимание: воспроизводимая сборка, закреплённые версии, маленький образ без dev-зависимостей.
31. Configure ecosystem for application state monitoring
• Знать: @nestjs/terminus (health checks), prom-client, Prometheus и Grafana, алерты; Express-вариант.
• Внимание: различать liveness и readiness; алерты по симптомам, а не по каждой метрике.
32. Configure integration process using CI tools
• Знать: GitHub Actions: lint, typecheck, test, build, кэш зависимостей, MySQL service container.
• Внимание: быстрый пайплайн, детерминированные тесты, секреты только через secrets.
33. Control code quality with measurement tools
• Знать: ESLint, Prettier, пороги coverage, SonarQube или SonarCloud, quality gate в CI.
• Внимание: пороги должны блокировать merge, иначе они не работают.
34. Create custom plugins for bundlers
• Знать: плагины esbuild, webpack, rollup; хуки сборки; пример: плагин, который инъецирует build-info.
• Внимание: плагин должен быть простым и покрытым тестом.
35. Establish communication across applications via message brokers and message queues
• Знать: RabbitMQ и BullMQ, ack / nack, retry с backoff, DLQ, graceful shutdown консьюмера.
• Внимание: не терять сообщения при рестарте, ограничивать повторы, следить за размером очереди.
36. Handle data integrity in message brokers
• Знать: семантики доставки (at-least-once, at-most-once), идемпотентные консьюмеры, transactional outbox на MySQL, poison messages.
• Внимание: «ровно один раз» на практике достигается идемпотентностью, а не брокером.
• Практика: вести всё в одном учебном NestJS-репозитории, чтобы артефакты (конфиги, гайдлайны, отчёты) лежали в репо.
7. Cloud
37. Configure containers for a cloud deployment (KEY)
• Знать: Docker, multi-stage Dockerfile для NestJS, .dockerignore, non-root, HEALTHCHECK, graceful shutdown через enableShutdownHooks и SIGTERM, лимиты CPU и памяти и --max-old-space-size, docker-compose с MySQL, конфиг через env, деплой в одно облако (например AWS ECR + ECS Fargate или App Runner), пайплайн GitHub Actions: сборка, registry, деплой.
• Внимание: ориентир — 3–4 недели; конфиги должны быть стандартизированы и повторно использоваться другими сервисами.
• Артефакты: обновлённые конфиги контейнеров, инфраструктурные определения со стандартными настройками, конфиг деплой-пайплайна, гайдлайн по конфигурации контейнеров, принятый командами.
38. Manage and provision infrastructure through code
• Знать: Terraform, state, модули, окружения; каталог infra/ воспроизводит окружение с нуля; terraform plan в CI.
• Внимание: ориентир — 2–3 недели; хранить state безопасно, не коммитить секреты.
39. Use a solution to build serverless applications
• Знать: AWS Lambda и API Gateway (или аналог), один эндпоинт или задача на Node.js/TypeScript, триггеры (HTTP, очередь, расписание), описание через IaC.
• Внимание: ориентир — 2 недели; cold start, таймауты, лимиты; сравнить контейнер и serverless по цене, латентности и операционной сложности.
• Практика: делать на своём NestJS + MySQL проекте.
8. Требования и управление процессами
40. Create and maintain software requirements specification documentation (KEY)
• Знать: ISO/IEC/IEEE 29148, SRS в docs/srs/ в репо для одной реальной фичи, REQ-нумерация, нефункциональные требования с цифрами, traceability к задачам и тестам, шаблон SRS.
• Внимание: изменения требований идут через PR; документ должен быть принят командой, а не лежать у одного человека.
• Артефакты: SRS, шаблон, матрица трассируемости.
41. Establish or modify technical debt policy (KEY)
• Знать: квадрант техдолга Фаулера, реестр с impact, стоимостью и риском, тег tech-debt, лимит 10–20% спринта, метрики в CI (ESLint complexity, SonarQube, npm audit или Renovate), TODO только с тикетами.
• Внимание: политика без бюджета времени не работает; приоритизировать по риску.
• Артефакты: документ политики, реестр техдолга, настроенные метрики.
42. Establish or refine requirements elicitation processes (KEY)
• Знать: интервью, воркшопы, прототипы, user stories, Given/When/Then, Event Storming.
• Внимание: описать текущий процесс и найти в нём дыры; применить на 2–3 реальных задачах, иначе это бумага.
• Артефакты: описание процесса, чек-лист уточняющих вопросов, шаблон тикета, Definition of Ready.
43. Adjust estimation processes using data gathered from requirements elicitation
• Знать: PERT, story points, анализ факта против оценки по 10–20 задачам, чек-лист забываемых пунктов.
• Внимание: оценка калибруется по реальным данным, а не по ощущениям.
44. Contribute to risk management processes to detect and mitigate potential issues
• Знать: реестр рисков (вероятность × влияние), митигация, владелец риска.
• Внимание: у каждого риска есть владелец и дата пересмотра.
45. Contribute to standards selection processes
• Знать: выбор стандарта через ADR, критерии и альтернативы, внедрение одного стандарта в команде.
• Внимание: стандарт без внедрения и проверки — просто документ.
46. Improve application delivery by contributing to the release process
• Знать: SemVer, changelog, conventional commits + release-please или semantic-release, чек-лист релиза, rollback, feature flags.
• Внимание: любой релиз можно откатить; план отката проверен заранее.
47. Improve quality management processes by contributing to quality documentation
• Знать: Definition of Done, тестовая стратегия, quality gates, гайдлайн ревью.
• Внимание: документы должны ссылаться на реальные проверки в CI.
• Ориентир по срокам: недели 1–4 SRS и сбор требований, 5–6 техдолг, 7–8 оценка и риски, 9–10 стандарты и релизы, 11–12 документация качества. Практика — пройти весь цикл на одной реальной фиче.