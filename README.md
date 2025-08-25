# Академия Бэкенда — Java Edition <img src="images/image.png" style="height: 20px; object-fit: cover;"/>

Приветствую тебя, странник!

В этом репозитории собраны результаты моих pet-проектов/курсов/работ на **Java/Kotlin/Spring**.  
Каждый модуль — отдельный проект: чёткое описание того, **что делает код**, **какой стек**, **ключевые файлы/структура**, **как запустить (кратко)**, **подробности реализации** и **какие навыки демонстрирует**.  
Проекты идут от наиболее архитектурно насыщенных к более компактным.

<img src="images/image-1.png" style="width: 100%; object-fit: cover;"/>

<img align="right" src="https://visitor-badge.laobi.icu/badge?page_id=LanGraFyodor.portfolio-java-academy">

---

## Содержание
- [Модуль 1 — ecom-microservices](#модуль-1---ecom-microservices)  
- [Модуль 2 — WhatsApp-Clone](#модуль-2---whatsapp-clone)  
- [Модуль 3 — airbnb-clone](#модуль-3---airbnb-clone)  
- [Модуль 4 — ecommerce-app](#модуль-4---ecommerce-app)  
- [Модуль 5 — Microservice-Java](#модуль-5---microservice-java)  
- [Модуль 6 — book-social-network](#модуль-6---book-social-network)  
- [Модуль 7 — SpringBootCrashCourse](#модуль-7---springbootcrashcourse)  
- [Контакты](#контакты)

---

### Модуль 1 — **ecom-microservices**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=ecom-microservices&theme=dark)](https://github.com/LanGraFyodor/ecom-microservices)

**Коротко.** Комплект Spring Cloud микросервисов для e-commerce: Config Server, Eureka, API Gateway и бизнес-сервисы (user, product, order, notification). Демонстрация service discovery, централизованной конфигурации и маршрутизации.

**Что делает код.**  
Организует распределённую систему: регистрация/аутентификация пользователей, каталог продуктов, обработка заказов (checkout, статус), уведомления. Сервисы регистрируются в Eureka, конфигурация хранится в Config Server, трафик проходит через Gateway.

**Стек.** Java, Spring Boot, Spring Cloud (Eureka, Config, Gateway), Spring Data JPA, PostgreSQL (или указанная БД), Docker.

**Ключевые файлы / структура.**  
- `configserver/` — централизованная конфигурация.  
- `eureka/` — discovery server.  
- `gateway/` — маршрутизация и глобальные фильтры.  
- `user/`, `product/`, `order/`, `notification/` — бизнес-сервисы (контроллеры, сервисы, репозитории).  
- `deploy/` или `docker/` — контейнеризация/скрипты запуска.

**Как запустить (кратко).**  
Клонировать репо и поднять инфраструктуру (configserver → eureka → gateway → сервисы) через docker-compose или поочередно через IDE.

**Подробности реализации.**  
Архитектура соответствует шаблону Spring Cloud: конфигурация и discovery упрощают развёртывание; gateway используется для cross-cutting concerns. Сервисы взаимодействуют по HTTP/REST; данные хранятся в реляционной БД через JPA.

**Навыки, которые проект демонстрирует.**  
Мультисервисная архитектура, работа со Spring Cloud, контейнеризация и согласование конфигураций между сервисами.

---

### Модуль 2 — **WhatsApp-Clone**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=WhatsApp-Clone&theme=dark)](https://github.com/LanGraFyodor/WhatsApp-Clone)

**Коротко.** Full-stack клон мессенджера: backend на Spring Boot + frontend (Angular), аутентификация через Keycloak, real-time обмен сообщениями (WebSocket).

**Что делает код.**  
Обеспечивает управление пользователями и чатами, отправку/приём сообщений в реальном времени, хранение истории сообщений и работу с медиа. Аутентификация централизована через Keycloak.

**Стек.** Java, Spring Boot, WebSocket/STOMP, Keycloak (OAuth2), PostgreSQL, Angular (frontend), Docker.

**Ключевые файлы / структура.**  
- `backend/` — контроллеры REST и WebSocket, сервисы, репозитории.  
- `frontend/` — Angular приложение (чат, списки, компоненты).  
- `keycloak/` или контейнерные инструкции для запуска Keycloak.

**Как запустить (кратко).**  
Запустить Keycloak, поднять backend (mvn spring-boot:run / контейнер), запустить frontend (npm start) и подключиться через браузер.

**Подробности реализации.**  
Реализован WebSocket-канал для real-time обмена; Keycloak интегрирован со Spring Security для авторизации и защиты сокетов/REST эндпоинтов.

**Навыки, которые проект демонстрирует.**  
Интеграция внешнего провайдера авторизации, реал-тайм коммуникации, организация full-stack приложения.

---

### Модуль 3 — **airbnb-clone**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=airbnb-clone&theme=dark)](https://github.com/LanGraFyodor/airbnb-clone)

**Коротко.** Сервис бронирований: листинги, поиск по локации/дате, бронирование с блокировкой дат и управлением статусами брони.

**Что делает код.**  
Обрабатывает CRUD для листингов, поиск и фильтрацию, создание брони с проверкой пересечений дат и управление транзакциями при подтверждении брони.

**Стек.** Java, Spring Boot, Spring Data JPA, PostgreSQL (или выбранная БД).

**Ключевые файлы / структура.**  
- Пакеты `listing`, `booking`, `user` с контроллерами, сервисами и репозиториями.  
- Конфигурация JPA и миграции (если есть).

**Как запустить (кратко).**  
Клонировать репозиторий, прописать параметры БД в `application.properties`, запустить через Maven/IDE.

**Подробности реализации.**  
Ключевой момент — проверка availability и предотвращение overlapping bookings; используются транзакции и корректные JPA-запросы.

**Навыки, которые проект демонстрирует.**  
Работа с датами/диапазонами, моделирование availability и обеспечение консистентности при конкурентных запросах.

---

### Модуль 4 — **ecommerce-app**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=ecommerce-app&theme=dark)](https://github.com/LanGraFyodor/ecommerce-app)

**Коротко.** E-commerce backend: каталог товаров, корзина, оформление заказа, админские операции по управлению товарами.

**Что делает код.**  
Предоставляет REST API для управления продуктами, корзиной и заказами, реализует роли/разграничение доступа для админов, включает обработку стока.

**Стек.** Java, Spring Boot, Spring Data JPA (Hibernate), PostgreSQL, Docker (опционально).

**Ключевые файлы / структура.**  
- `controller/`, `service/`, `repository/` — стандартные слои приложения.  
- Конфигурация безопасности и ролей.

**Как запустить (кратко).**  
Запустить через Maven или Docker при наличии `docker-compose`, настроить переменные окружения для БД.

**Подробности реализации.**  
Фокус на корректной работе транзакций при оформлении заказа и на разделении прав доступа (user/admin).

**Навыки, которые проект демонстрирует.**  
Практические паттерны backend-разработки: DTO, mapping, транзакции, валидация.

---

### Модуль 5 — **Microservice-Java**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=Microservice-Java&theme=dark)](https://github.com/LanGraFyodor/Microservice-Java)

**Коротко.** Шаблон микросервиса: минимальный REST сервис с health-checks, конфигурацией и готовностью к контейнеризации.

**Что делает код.**  
Реализует базовый REST API, точки здоровья (health/readiness), простую конфигурацию и примеры взаимодействия с БД (если подключена).

**Стек.** Java, Spring Boot, Spring Actuator (опционально), Docker.

**Ключевые файлы / структура.**  
- `controller/`, `service/`, `repository/`, `application.yml`.

**Как запустить (кратко).**  
mvn spring-boot:run или собрать Docker-образ и запустить контейнер.

**Подробности реализации.**  
Проект служит шаблоном для быстрой генерации новых микросервисов с консистентной структурой и практиками observability.

**Навыки, которые проект демонстрирует.**  
Структурирование сервисов, health-endpoints, готовность к CI/CD.

---

### Модуль 6 — **book-social-network**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=book-social-network&theme=dark)](https://github.com/LanGraFyodor/book-social-network)

**Коротко.** Социальная платформа для книг: публикация объявлений о книгах, профили пользователей, взаимодействие между участниками.

**Что делает код.**  
Позволяет создавать объявления о книгах, просматривать профили, оставлять комментарии/оценки и вести переписку между пользователями (если предусмотрено).

**Стек.** Java, Spring Boot, Spring Data (Postgres/Mongo), REST API.

**Ключевые файлы / структура.**  
- `controllers/bookController`, `services`, `repositories`, модели сущностей книги/пользователя.

**Как запустить (кратко).**  
mvn spring-boot:run после настройки параметров БД.

**Подробности реализации.**  
Фокус на domain modelling для каталога книг и на связях между сущностями (владение, обмен, отзывы).

**Навыки, которые проект демонстрирует.**  
Проектирование доменной модели, реализация CRUD и связей между сущностями.

---

### Модуль 7 — **SpringBootCrashCourse**
[![pin](https://github-readme-stats.vercel.app/api/pin/?username=LanGraFyodor&repo=SpringBootCrashCourse&theme=dark)](https://github.com/LanGraFyodor/SpringBootCrashCourse)

**Коротко.** Набор упражнений и примеров на Spring Boot: базовый CRUD, работа с MongoDB/SQL, стартовые шаблоны для сервисов.

**Что делает код.**  
Примеры регистрации/логина, работа с заметками/записями, демонстрация Spring Data и простых контроллеров.

**Стек.** Java, Spring Boot, Spring Data (Mongo/SQL), тесты (JUnit).

**Ключевые файлы / структура.**  
- `UserController`, `NoteController`, `repositories`, `application.properties`.

**Как запустить (кратко).**  
mvn spring-boot:run или запустить через IDE; при необходимости поднять БД через Docker.

**Подробности реализации.**  
Образцовый проект для быстрого обучения Spring Boot и для проверки базовых концепций.

**Навыки, которые проект демонстрирует.**  
Основы Spring Boot, Spring Data, простая безопасность и конфигурация.

---

## Контакты
GitHub: https://github.com/LanGraFyodor

---
