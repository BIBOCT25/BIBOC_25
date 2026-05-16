# 🏎️ PITSTOP MANAGEMENT SYSTEM

## Автоматизированная система управления автосервисом

### Техническое задание для команды из 9 разработчиков

**Стек 1:** `PHP 8.2` + `Laravel 11` + `React 18` + `PostgreSQL 16`  
**Стек 2:** `Node.js 20` + `Express 4` + `React 18` + `PostgreSQL 16`  

---

## 📑 СОДЕРЖАНИЕ

- [1. Общее описание проекта](#1-общее-описание-проекта)
  - [1.1 Цели системы](#11-цели-системы)
  - [1.2 Распределение команды (9 студентов)](#12-распределение-команды-9-студентов)
- [2. Роли пользователей и их интерфейсы](#2-роли-пользователей-и-их-интерфейсы)
  - [2.1 Кассиры — 3 рабочих места](#21-кассиры--3-рабочих-места)
  - [2.2 Мастера ремонта — 3 куратора](#22-мастера-ремонта--3-куратора)
  - [2.3 Ремонтники — 12 аккаунтов](#23-ремонтники--12-аккаунтов)
  - [2.4 Мастера мойки — 4 куратора](#24-мастера-мойки--4-куратора)
  - [2.5 Мойщики — 16 аккаунтов](#25-мойщики--16-аккаунтов)
  - [2.6 Кладовщики — 2 аккаунта](#26-кладовщики--2-аккаунта)
  - [2.7 Эвакуаторы — 3 аккаунта](#27-эвакуаторы--3-аккаунта)
  - [2.8 Выездной шиномонтаж и ходовая — 5 бригад](#28-выездной-шиномонтаж-и-ходовая--5-бригад)
  - [2.9 Мастера кузовного ремонта и покраски — 4 мастера](#29-мастера-кузовного-ремонта-и-покраски--4-мастера)
  - [2.10 Эксперты и страховые агенты — 2 аккаунта](#210-эксперты-и-страховые-агенты--2-аккаунта)
  - [2.11 Адвокатская контора — 2 аккаунта](#211-адвокатская-контора--2-аккаунта)
  - [2.12 Кафе, гостиница и клининг — 4 аккаунта](#212-кафе-гостиница-и-клининг--4-аккаунта)
  - [2.13 Транспортная логистика и грузоперевозки — 6 аккаунтов](#213-транспортная-логистика-и-грузоперевозки--6-аккаунтов)
  - [2.14 CRM, B2B и Бухгалтерия — 5 аккаунтов](#214-crm-b2b-и-бухгалтерия--5-аккаунтов)
  - [2.15 Автопрокат, СТО и Авторазбор — 5 аккаунтов](#215-автопрокат-сто-и-авторазбор--5-аккаунтов)
- [3. Складская система и дашборды](#3-складская-система-и-дашборды)
  - [3.1 Структура складов](#31-структура-складов)
  - [3.2 Дашборд мини-склада](#32-дашборд-мини-склада)
  - [3.3 Дашборд кладовщика](#33-дашборд-кладовщика)
  - [3.4 Дашборд мастера](#34-дашборд-мастера)
- [4. Технический стек 1 — PHP / Laravel](#4-технический-стек-1--php--laravel)
  - [4.1 Серверная часть](#41-серверная-часть-php)
  - [4.2 Аутентификация](#42-аутентификация-php)
  - [4.3 Схема БД PostgreSQL](#43-схема-бд-postgresql)
  - [4.4 Frontend (React)](#44-frontend-react--стек-1)
- [5. Технический стек 2 — Node.js / Express](#5-технический-стек-2--nodejs--express)
  - [5.1 Серверная часть](#51-серверная-часть-serverjs--express)
  - [5.2 Пример server.js](#52-пример-serverjs)
  - [5.3 Middleware авторизации](#53-middleware-авторизации-node)
  - [5.4 Prisma Schema](#54-prisma-schema-фрагмент)
- [6. Технические задания по разработчикам](#6-технические-задания-по-разработчикам)
- [7. Требования к адаптивному интерфейсу](#7-требования-к-адаптивному-интерфейсу)
- [8. Дорожная карта разработки](#8-дорожная-карта-разработки-8-недель)
- [9. Сравнение двух стеков](#9-сравнение-двух-стеков)
- [10. UML-диаграммы](#10-uml-диаграммы)
  - [10.1 Use Case диаграмма](#101-use-case-диаграмма)
  - [10.2 Диаграмма компонентов](#102-диаграмма-компонентов)
  - [10.3 Диаграмма последовательности](#103-диаграмма-последовательности)
  - [10.4 ER-диаграмма базы данных](#104-er-диаграмма-базы-данных)
  - [10.5 Диаграмма развёртывания](#105-диаграмма-развёртывания)
- [11. API-контракт (OpenAPI/Swagger)](#11-api-контракт-openapiswagger)
- [12. Лицензия](#12-лицензия)

---

## 1. ОБЩЕЕ ОПИСАНИЕ ПРОЕКТА

Проект **PitStop** — многоуровневая веб-система управления автосервисом, включающая:

| Компонент | Описание |
|-----------|----------|
| 🏪 Магазин | Розничные продажи автозапчастей и расходников |
| 🌐 Интернет-магазин | Онлайн-заказы с выдачей в магазине |
| 🔧 Ремонтный участок | 3 мастера × 4 ремонтника = 12 рабочих |
| 🧽 Участок мойки | 4 мастера × 4 мойщика = 16 рабочих |
| 📦 Центральный склад | 2 кладовщика, выдача на мини-склады |
| 🗄️ Мини-склады | 3 склада (ремонт, мойка, магазин) |
| 🚚 Эвакуаторы | 3 круглосуточных эвакуатора с онлайн-отслеживанием |
| 🚐 Выездной сервис | Круглосуточный мобильный шиномонтаж и ходовая (5 бригад) |
| 🎨 Кузовной цех | Кузовной ремонт, рихтовка и покрасочные камеры |
| 🛡️ Страхование | Оценка ДТП независимым экспертом и оформление страховок |
| ⚖️ Адвокаты | Юридическая помощь при ДТП и спорных ситуациях |
| ☕ Кафе и Отель | Зона ожидания, кафе, гостиница и служба клининга |
| 🚛 Логистика | Грузоперевозки (город, межгород, РФ) разным транспортом |
| 🤝 CRM и B2B | Управление лояльностью, рассылки, обслуживание юрлиц |
| 📊 Бухгалтерия | Финансовый учет, налоги, кадровое администрирование |
| ♻️ Прокат и Разбор | Выдача подменных авто, прокат, скупка и разборка битых авто |
| 📝 Техосмотр | Выдача диагностических карт и интеграция с ЕАИСТО |

Система разрабатывается в двух параллельных вариантах с единым React-фронтендом и PostgreSQL.

### 1.1 Цели системы

- ✅ Автоматизация рабочих мест **кассиров** (магазин + интернет-магазин)
- ✅ Управление задачами **ремонтников** и **мойщиков** через мастеров
- ✅ **Служба эвакуации** и **круглосуточный выездной сервис** (шиномонтаж)
- ✅ Участок **кузовного ремонта и покраски автомобилей**
- ✅ Модули **страхования, независимой экспертизы** и **адвокатской помощи**
- ✅ Управление сопутствующими услугами: **кафе, гостиница, клининг**
- ✅ Подсистема **транспортной логистики** (городские, междугородние и всероссийские рейсы)
- ✅ Модули **CRM, B2B, Бухгалтерии** и **Управления персоналом**
- ✅ Экосистема **Автопроката, Разборки авто** и **Станции техосмотра (СТО)**
- ✅ **Централизованный склад** с выдачей на 2 склада и магазин
- ✅ **Дашборды аналитики** по заказам, складам, зарплатам, KPI
- ✅ **Адаптивный интерфейс** для всех ролей (📱 смартфон, 📋 планшет, 🖥️ ПК)

### 1.2 Распределение команды (25 студентов)

| # | Роль разработчика | Стек | Модуль | Ответственность |
|---|-------------------|------|--------|-----------------|
| **1** | Тимлид / Архитектор | Оба стека | Архитектура + DevOps | Структура БД, API-контракт, Docker, CI/CD, деплой |
| **2** | Backend PHP-разработчик 1 | PHP / Laravel | Auth + Orders | JWT-авторизация, заказы, кассиры, платежи |
| **3** | Backend PHP-разработчик 2 | PHP / Laravel | Warehouse + Analytics | Склад, запросы, дашборды, зарплаты |
| **4** | Backend Node-разработчик 1 | Node.js / Express | Auth + Orders | server.js, JWT, заказы, middleware |
| **5** | Backend Node-разработчик 2 | Node.js / Express | Warehouse + Analytics | Prisma schema, склад, задания, аналитика |
| **6** | Frontend-разработчик 1 | React + Vite | Кассиры + Магазин | POS-интерфейс, интернет-магазин, оплаты |
| **7** | Frontend-разработчик 2 | React + Vite | Мастера + Рабочие | Дашборды мастеров, аккаунты рабочих |
| **8** | Frontend-разработчик 3 | React + Vite | Склад + Дашборды | Интерфейс склада, аналитика, графики |
| **9** | QA / DevOps | Все | Тестирование + CI/CD | Unit/E2E тесты, Docker, документация |
| **10** | Backend-разработчик 3 | Любой стек | Выездной сервис | API эвакуаторов, мобильный шиномонтаж, трекинг |
| **11** | Backend-разработчик 4 | Любой стек | Кузовной цех | Сметы ремонта, бронь покрасочных камер, детализация |
| **12** | Frontend-разработчик 4 | React + Vite | Новые направления | UI навигаторов, интерактивные карты, кузовные сметы |
| **13** | Backend-разработчик 5 | Любой стек | Юриспруденция | Интеграция страховых компаний, ЭДО для адвокатов |
| **14** | Backend-разработчик 6 | Любой стек | HoReCa + Клининг | Система бронирования номеров, меню кафе, график уборки |
| **15** | Frontend-разработчик 5 | React + Vite | Юр. и HoReCa | Дашборды экспертов/адвокатов, интерфейсы кафе и отеля |
| **16** | Backend-разработчик 7 | Любой стек | Логистика | Маршрутизация, путевые листы, расчет стоимости рейсов |
| **17** | Backend-разработчик 8 | Любой стек | Автопарк | Управление транспортом (от ГАЗелей до фур), ТО, топливо |
| **18** | Frontend-разработчик 6 | React + Vite | Транспорт | Интерактивные карты грузоперевозок, UI логиста и водителя |
| **19** | Backend-разработчик 9 | Любой стек | CRM и Маркетинг | Программы лояльности, рассылки, IP-телефония |
| **20** | Backend-разработчик 10 | Любой стек | Финансы и Кадры | Интеграция с 1С, зарплаты, графики смен, ЭДО |
| **21** | Backend-разработчик 11 | Любой стек | Автопрокат и Разбор | Управление подменными авто, штрафы, разбор битых машин |
| **22** | Backend-разработчик 12 | Любой стек | B2B и Техосмотр | Договоры с таксопарками, интеграция ЕАИСТО, диагностика |
| **23** | Frontend-разработчик 7 | React + Vite | CRM и Финансы | Дашборды маркетолога, бухгалтера, HR-специалиста |
| **24** | Frontend-разработчик 8 | React + Vite | Прокат и B2B | Интерфейсы автопроката, B2B-кабинет корпоративных клиентов |
| **25** | Fullstack-разработчик 1 | Любой стек | Обучение | Модуль корпоративного университета, тесты, онбординг |

---

## 2. РОЛИ ПОЛЬЗОВАТЕЛЕЙ И ИХ ИНТЕРФЕЙСЫ

### 2.1 Кассиры — 3 рабочих места

**Интерфейс:** POS-терминал + панель интернет-заказов. Адаптивный дизайн (планшет/ПК).

#### Функционал:

| Действие | Описание |
|----------|----------|
| 📝 Создание заказа | Оформление покупки в физическом магазине |
| 🌐 Онлайн-заказы | Обработка: новые → в обработке → выданы |
| 💳 Приём оплаты | Наличные, карта, QR-код |
| 📊 Остатки | Просмотр текущих остатков магазинного мини-склада |
| 🖨️ Чек | Печать чека / формирование электронного чека |
| 🔍 Поиск | Поиск товаров по артикулу, названию, штрихкоду |

#### API-маршруты:

```http
POST   /api/orders               # Создать заказ
GET    /api/orders?type=online    # Список интернет-заказов
PATCH  /api/orders/:id/status     # Изменить статус заказа
GET    /api/products?search=...   # Поиск товаров
POST   /api/payments              # Оформить платёж
```

### 2.2 Мастера ремонта — 3 куратора
Каждый мастер курирует 4 ремонтников. Интерфейс: дашборд + список задач + зарплата.

#### Функционал:
| Действие | Описание |
|---|---|
| 📋 Создание задания | Описание, фото, приоритет, дедлайн |
| 👤 Назначение | Выбор ремонтника из своей группы |
| 📡 Мониторинг | Статусы заданий в реальном времени |
| 💰 Зарплата | Ведомость по подчинённым |
| 📦 Запрос запчастей | Со склада для задания |
| 📊 Дашборд | Выполнено / в работе / просрочено |

#### API-маршруты:
```http
POST   /api/tasks                 # Создать задание
GET    /api/tasks?master_id=...   # Мои задания
PATCH  /api/tasks/:id/assign      # Назначить ремонтнику
GET    /api/salary?user_id=...    # Зарплата сотрудников
POST   /api/warehouse/request     # Запрос запчастей
```

### 2.3 Ремонтники — 12 аккаунтов (3 мастера × 4)
Упрощённый адаптивный интерфейс на смартфон/планшет. Только приём и выполнение заданий.

#### Функционал:

| Действие | Описание |
|---|---|
| 📋 Личный кабинет | Список назначенных заданий |
| ✅ Принятие | Кнопка «Принять» → статус «В работе» |
| ✔️ Завершение | Статус «Завершено» + фото результата |
| 💰 Зарплата | Просмотр своей зарплаты и смен |

#### API-маршруты:
```http
GET    /api/tasks/my              # Мои задания
PATCH  /api/tasks/:id/accept      # Принять задание
PATCH  /api/tasks/:id/complete    # Завершить задание
```

### 2.4 Мастера мойки — 4 куратора
Аналогична структуре мастеров ремонта. Каждый мастер управляет 4 мойщиками.

#### Функционал:

| Действие | Описание |
|---|---|
| 🧽 Создание задания | Тип мойки, авто, время |
| 👤 Назначение | Выбор мойщика |
| 📊 Дашборд | Загрузка по слотам, статистика за день |
| 💰 Зарплата | Ведомость своей группы |

#### API-маршруты:
```http
POST   /api/wash-tasks            # Задание на мойку
GET    /api/wash-tasks?master=... # Задания мастера
PATCH  /api/wash-tasks/:id/assign # Назначить мойщику
```

### 2.5 Мойщики — 16 аккаунтов (4 мастера × 4)
#### Функционал:

| Действие | Описание |
|---|---|
| 📋 Приём задания | Получение задачи на мойку |
| 🔄 Статусы | В очереди → Выполняется → Завершено |
| 💰 Зарплата | Просмотр своей зарплаты |

#### API-маршруты:
```http
GET    /api/wash-tasks/my         # Мои задания
PATCH  /api/wash-tasks/:id/start  # Начать
PATCH  /api/wash-tasks/:id/done   # Завершить
```

### 2.6 Кладовщики — 2 аккаунта (центральный склад)
Управляют центральным складом. Принимают запросы от мини-складов и магазина.

#### Функционал:

| Действие | Описание |
|---|---|
| 📥 Входящие запросы | Просмотр: от кого, что, сколько |
| ✅ Одобрение | Подтверждение или отклонение с комментарием |
| 📤 Списание | Списание товара с центрального склада |
| 📦 Приём товара | Добавление нового товара на склад |
| 📊 Дашборд | Остатки, топ-запросы, история движения |
| ✏️ CRUD товаров | Добавление, удаление, корректировка |

#### API-маршруты:
```http
GET    /api/warehouse/requests    # Входящие запросы
PATCH  /api/warehouse/requests/:id/approve  # Одобрить
POST   /api/warehouse/products   # Добавить товар
PATCH  /api/warehouse/products/:id          # Обновить
DELETE /api/warehouse/products/:id          # Удалить
GET    /api/warehouse/dashboard  # Аналитика склада
```

### 2.7 Эвакуаторы — 3 аккаунта
Водители эвакуаторов, работающие круглосуточно. Принимают экстренные вызовы и заказы на перевозку автомобилей клиентов.

#### Функционал:

| Действие | Описание |
|---|---|
| 📡 Геолокация | Передача GPS-координат в реальном времени |
| 📋 Приём вызовов | Получение точки А (откуда) и точки Б (сервис) |
| 📸 Фотофиксация | Осмотр автомобиля перед погрузкой (фиксация повреждений) |
| 💳 Оплата | Приём оплаты за эвакуацию (интеграция с кассовым модулем) |

#### API-маршруты:
```http
GET    /api/tow-requests/my       # Мои активные вызовы
PATCH  /api/tow-requests/:id/gps  # Обновить координаты
PATCH  /api/tow-requests/:id/done # Завершить эвакуацию
```

### 2.8 Выездной шиномонтаж и ходовая — 5 мобильных бригад
Круглосуточный мобильный сервис. Мастера работают на выезде на специализированных фургонах.

#### Функционал:

| Действие | Описание |
|---|---|
| 🚐 Выезд на точку | Получение координат клиента и описания поломки |
| 📦 Мини-склад (авто) | Списание расходников (жгуты, заплатки, балансировочные грузики) прямо из фургона |
| 💳 Оплата на месте | Выставление счёта и приём оплаты (интеграция с кассирами) |
| 📝 Отчётность | Формирование акта выполненных работ |

#### API-маршруты:
```http
GET    /api/mobile-service/requests # Вызовы на выезд
POST   /api/mobile-service/stocks   # Запрос материалов со склада в фургон
POST   /api/payments/mobile         # Проведение оплаты на месте
```

### 2.9 Мастера кузовного ремонта и покраски — 4 мастера
Специализированный участок со своими сметами, длительным циклом работ и покрасочными камерами.

#### Функционал:

| Действие | Описание |
|---|---|
| 📋 Смета ремонта | Создание подробной калькуляции (детали, краска, нормочасы) |
| 🎨 Заказ краски | Специфические запросы колористу/на склад (подбор цвета) |
| ⏳ Камеры покраски | Бронирование времени в сушильной камере |
| 📸 Процесс | Фотоотчёт до/в процессе/после для клиента |

#### API-маршруты:
```http
POST   /api/bodywork/estimates      # Создание сметы
POST   /api/bodywork/camera/book    # Бронь покрасочной камеры
PATCH  /api/bodywork/tasks/:id/step # Переход на следующий этап
```

### 2.10 Эксперты и страховые агенты — 2 аккаунта
Специалисты по оценке повреждений после ДТП и оформлению полисов (ОСАГО, КАСКО).

#### Функционал:

| Действие | Описание |
|---|---|
| 📋 Экспертиза | Формирование заключения независимой экспертизы |
| 🛡️ Страховки | Расчёт стоимости и оформление электронных полисов |
| 📑 ЭДО | Интеграция с базами РСА и страховых компаний |

#### API-маршруты:
```http
POST   /api/insurance/policies      # Оформление полиса
POST   /api/expert/assessments      # Заключение эксперта
```

### 2.11 Адвокатская контора — 2 аккаунта
Юридическая поддержка клиентов, попавших в ДТП, и представление их интересов.

#### Функционал:

| Действие | Описание |
|---|---|
| ⚖️ Ведение дел | Создание карточек судебных и досудебных дел |
| 📅 Планировщик | Расписание судебных заседаний и встреч с клиентами |
| 📄 Документы | Генерация типовых претензий, исков, доверенностей |

#### API-маршруты:
```http
GET    /api/law/cases               # Список юридических дел
POST   /api/law/documents/generate  # Генерация иска
```

### 2.12 Кафе, гостиница и клининг — 4 аккаунта
Обслуживание клиентов, ожидающих ремонт, и транзитных водителей.

#### Функционал:

| Действие | Описание |
|---|---|
| ☕ Меню кафе | Приём заказов, передача на кухню, расчёт столов |
| 🛏️ Бронь номеров | Шахматка номеров гостиницы при автосервисе |
| 🧹 Клининг | График уборки помещений (ремонтной зоны, кафе, номеров) |

#### API-маршруты:
```http
POST   /api/horeca/cafe/orders      # Заказ в кафе
POST   /api/horeca/hotel/book       # Бронь номера
GET    /api/cleaning/tasks          # Задачи для уборщиков
```

### 2.13 Транспортная логистика и грузоперевозки — 6 аккаунтов
Подразделение доставки и транспортных услуг. Включает диспетчеров-логистов и водителей различного грузового транспорта (малотоннажный по городу, фуры по России).

#### Функционал:

| Действие | Описание |
|---|---|
| 🗺️ Маршрутизация | Планирование рейсов: внутригородские, междугородние и по всей РФ |
| 🚚 Автопарк | Управление транспортом разного тоннажа (пикапы, ГАЗели, 20-тонники) |
| ⛽ Путевые листы | Учет расхода ГСМ, командировочных и амортизации транспортных средств |
| 📦 Доставка грузов | Оптимизация доставки запчастей или коммерческих грузов клиентов |

#### API-маршруты:
```http
POST   /api/logistics/routes        # Построение маршрута
GET    /api/logistics/fleet         # Статус транспортных средств
PATCH  /api/logistics/trips/:id/gps # Обновление местоположения груза
```

### 2.14 CRM, B2B и Бухгалтерия — 5 аккаунтов
Бэкофис предприятия: маркетологи, бухгалтеры, HR-специалисты и менеджеры по работе с корпоративными клиентами.

#### Функционал:

| Действие | Описание |
|---|---|
| 🤝 Лояльность | Управление бонусами, скидками, кэшбеком и рассылками |
| 💼 B2B договоры | Выставление счетов и актов сверок для автопарков |
| 📊 Учет | Сведение дебета/кредита, расчет сложных налогов |
| 👨‍💼 Кадры | Учет больничных, отпусков, графиков сменности |

#### API-маршруты:
```http
POST   /api/crm/campaigns           # Запуск маркетинговой рассылки
GET    /api/b2b/invoices            # Счета корпоративных клиентов
GET    /api/hr/schedule             # График смен персонала
```

### 2.15 Автопрокат, СТО и Авторазбор — 5 аккаунтов
Смежные автомобильные направления: прокат машин, официальный техосмотр и утилизация битых автомобилей.

#### Функционал:

| Действие | Описание |
|---|---|
| 🚗 Прокат | Выдача авто клиентам, контроль пробега и штрафов ПДД |
| ♻️ Авторазбор | Дефектовка битого авто, оприходование Б/У деталей |
| 📝 Техосмотр | Проведение инструментального контроля, связь с ЕАИСТО |
| 🎓 Обучение | Прохождение внутренних тестов механиками и диагностами |

#### API-маршруты:
```http
POST   /api/rent/contracts          # Оформление договора аренды
POST   /api/recycle/parts           # Оприходование Б/У запчасти
POST   /api/inspection/eaisto       # Отправка данных техосмотра
```

## 3. СКЛАДСКАЯ СИСТЕМА И ДАШБОРДЫ
### 3.1 Структура складов

| Склад | Пользователи | Интерфейс | Пополнение |
|---|---|---|---|
| 📦 Центральный склад | 2 кладовщика | Полный CRUD + дашборд | Прямой ввод / поставщики |
| 🔧 Мини-склад 1 (ремонт) | 1 ответственный | Просмотр + запросы | Центральный склад |
| 🧽 Мини-склад 2 (мойка) | 1 ответственный | Просмотр + запросы | Центральный склад |
| 🏪 Магазин | Кассиры (3) | Просмотр остатков | Центральный склад |

Схема движения товаров:
```text
┌──────────────────────────────────────────────────────────────────┐
│                     ЦЕНТРАЛЬНЫЙ СКЛАД                             │
│                    (2 кладовщика)                                 │
│  ┌─────────────────────────────────────────────────────────────┐ │
│  │  • Приём товара от поставщиков                               │ │
│  │  • Полный CRUD справочника                                   │ │
│  │  • Обработка запросов от мини-складов                        │ │
│  │  • Дашборд: остатки, движение, топ-запросы                   │ │
│  └─────────────────────────────────────────────────────────────┘ │
└──────────────┬────────────────────────┬──────────────────────────┘
               │                        │
               ▼                        ▼
┌──────────────────────────┐  ┌──────────────────────────┐
│   МИНИ-СКЛАД 1 (ремонт)  │  │   МИНИ-СКЛАД 2 (мойка)   │
│   1 ответственный        │  │   1 ответственный        │
│  ┌──────────────────────┐│  │  ┌──────────────────────┐│
│  │• Просмотр остатков   ││  │  │• Просмотр остатков   ││
│  │• Запрос на пополнение││  │  │• Запрос на пополнение││
│  │• История поступлений ││  │  │• История поступлений ││
│  │• Индикатор уровня    ││  │  │• Индикатор уровня    ││
│  └──────────────────────┘│  │  └──────────────────────┘│
└──────────────────────────┘  └──────────────────────────┘
               │
               ▼
┌──────────────────────────┐
│   МАГАЗИН                │
│   Кассиры (3)            │
│  ┌──────────────────────┐│
│  │• Просмотр остатков   ││
│  │• Оформление продаж   ││
│  │• Интернет-заказы     ││
│  └──────────────────────┘│
└──────────────────────────┘
```

### 3.2 Дашборд мини-склада

| Элемент | Описание |
|---|---|
| 📋 Таблица позиций | Артикул, название, количество, ед. изм., мин. остаток |
| 🔴🟡🟢 Индикатор | Цветовой уровень остатков (красный/жёлтый/зелёный) |
| 📤 Кнопка «Запросить» | Отправка запроса на центральный склад |
| 🔍 Фильтры | По категории, по статусу (в наличии / заканчивается / отсутствует) |
| 📜 История | Дата поступления, количество, статус запроса |

### 3.3 Дашборд кладовщика (центральный склад)

| Элемент | Описание |
|---|---|
| 📊 Сводная таблица | Все позиции с фильтрами по складу-получателю |
| 📥 Панель запросов | Входящие запросы с кнопками одобрения/отклонения |
| 📈 Диаграмма | Движение товара за период (поступления / выдачи) |
| ✏️ CRUD-таблица | Inline-редактирование, удаление с подтверждением |
| 📥 Экспорт | CSV / Excel |

### 3.4 Дашборд мастера

| Элемент | Описание |
|---|---|
| 📊 Загрузка | Сколько заданий: в работе / в ожидании / завершено |
| 👥 Статус бригады | Онлайн / в задании / свободен для каждого подчинённого |
| 💰 Зарплата | Выработка, ставка, итого за месяц |
| 📜 История заданий | Фильтры: по дате, статусу, исполнителю |
| 🎯 KPI-плашки | Среднее время выполнения, % выполненных в срок |
## 4. ТЕХНИЧЕСКИЙ СТЕК 1 — PHP / LARAVEL
### 4.1 Серверная часть (PHP)

| Технология | Версия | Назначение |
|---|---|---|
| PHP | 8.2+ | Язык программирования |
| Laravel | 11 | MVC-фреймворк, Eloquent ORM, Sanctum (JWT) |
| PostgreSQL | 16 | Основная база данных |
| Redis | 7+ | Кэш сессий, очереди задач |
| Laravel Queues | — | Фоновые задачи, уведомления |
| Composer | 2+ | Менеджер зависимостей |
Структура директорий:
```text
laravel-project/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   └── Api/
│   │   │       ├── AuthController.php          # JWT-авторизация
│   │   │       ├── OrderController.php         # CRUD заказов
│   │   │       ├── TaskController.php          # Задания (ремонт)
│   │   │       ├── WashTaskController.php      # Задания (мойка)
│   │   │       ├── WarehouseController.php     # Складской учёт
│   │   │       └── DashboardController.php     # Аналитика, дашборды
│   │   └── Middleware/
│   │       └── RoleMiddleware.php              # RBAC по ролям
│   ├── Models/
│   │   ├── User.php                            # Пользователи
│   │   ├── Order.php                           # Заказы
│   │   ├── OrderItem.php                       # Позиции заказа
│   │   ├── Product.php                         # Товары
│   │   ├── Task.php                            # Задания
│   │   ├── Warehouse.php                       # Склады
│   │   ├── WarehouseStock.php                  # Остатки
│   │   ├── WarehouseRequest.php                # Запросы
│   │   ├── SalaryRecord.php                    # Зарплаты
│   │   └── Payment.php                         # Платежи
│   └── Services/
│       ├── WarehouseService.php                # Бизнес-логика склада
│       └── SalaryService.php                   # Расчёт зарплат
├── routes/
│   └── api.php                                 # API-маршруты
├── database/
│   └── migrations/                             # Миграции БД
├── config/
│   └── sanctum.php                             # Настройки JWT
└── composer.json
```

### 4.2 Аутентификация (PHP)
Используется Laravel Sanctum. Роли в таблице users.role:

| Роль | Значение | Описание |
|---|---|---|
| cashier | Кассир | Работа с заказами и оплатами |
| repair_master | Мастер ремонта | Управление бригадой ремонтников |
| repair_worker | Ремонтник | Выполнение заданий |
| wash_master | Мастер мойки | Управление бригадой мойщиков |
| wash_worker | Мойщик | Выполнение заданий |
| warehouse_keeper | Кладовщик | Управление складом |
| admin | Администратор | Полный доступ |
```http
POST   /api/auth/login          # Логин → { token, user }
POST   /api/auth/logout         # Логаут (инвалидация токена)
GET    /api/auth/me             # Текущий пользователь + роль
POST   /api/auth/refresh        # Обновление токена
```

### 4.3 Схема БД PostgreSQL
Таблицы:

| Таблица | Ключевые поля | Индексы | Описание |
|---|---|---|---|
| users | id, name, email, password, role, master_id | email (UNIQUE), role, master_id (FK) | Все пользователи системы |
| orders | id, type, status, total, cashier_id, customer_name, created_at | type, status, cashier_id (FK) | Заказы магазина и онлайн |
| order_items | id, order_id, product_id, qty, price | order_id (FK), product_id (FK) | Позиции заказа |
| products | id, sku, name, category, price, unit, barcode | sku (UNIQUE), barcode, category | Справочник товаров |
| tasks | id, type, title, description, status, master_id, worker_id, priority, due_at | master_id (FK), worker_id (FK), status, due_at | Задания (ремонт/мойка) |
| warehouses | id, name, type, location | type | Склады |
| warehouse_stocks | id, warehouse_id, product_id, qty, min_qty | warehouse_id (FK), product_id (FK) | Остатки на складе |
| warehouse_requests | id, from_wh, to_wh, product_id, qty, status, comment | from_wh (FK), to_wh (FK), product_id (FK) | Запросы между складами |
| salary_records | id, user_id, period, amount, hours_worked, rate, calculated_at | user_id (FK), period | Расчёт зарплаты |
| payments | id, order_id, method, amount, paid_at | order_id (FK) | Платежи |
SQL-схема (ключевые таблицы):
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role VARCHAR(50) NOT NULL CHECK (role IN (
        'cashier', 'repair_master', 'repair_worker',
        'wash_master', 'wash_worker', 'warehouse_keeper', 'admin',
        'tow_driver', 'mobile_mechanic', 'bodywork_master', 'painter',
        'expert', 'insurance_agent', 'lawyer', 'cafe_manager', 'cleaner',
        'logistics_dispatcher', 'truck_driver',
        'marketer', 'accountant', 'hr_manager', 'b2b_manager', 'inspector'
    )),
    master_id INTEGER REFERENCES users(id) ON DELETE SET NULL,
    phone VARCHAR(50),
    avatar_url VARCHAR(500),
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_users_role ON users(role);
CREATE INDEX idx_users_master_id ON users(master_id);

CREATE TABLE tasks (
    id SERIAL PRIMARY KEY,
    type VARCHAR(20) NOT NULL CHECK (type IN ('repair', 'wash', 'tow', 'mobile', 'bodywork', 'paint')),
    title VARCHAR(500) NOT NULL,
    description TEXT,
    status VARCHAR(30) NOT NULL DEFAULT 'pending' CHECK (status IN (
        'pending', 'assigned', 'in_progress', 'completed', 'cancelled'
    )),
    priority VARCHAR(10) NOT NULL DEFAULT 'medium' CHECK (priority IN (
        'low', 'medium', 'high', 'urgent'
    )),
    master_id INTEGER NOT NULL REFERENCES users(id),
    worker_id INTEGER REFERENCES users(id),
    vehicle_info JSONB,
    photo_urls JSONB DEFAULT '[]',
    due_at TIMESTAMP,
    completed_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_tasks_master ON tasks(master_id);
CREATE INDEX idx_tasks_worker ON tasks(worker_id);
CREATE INDEX idx_tasks_status ON tasks(status);
```

### 4.4 Frontend (React — Стек 1)

| Технология | Назначение |
|---|---|
| React 18 | UI-библиотека |
| Vite | Сборщик |
| TypeScript | Типизация |
| React Router v6 | Роутинг по ролям |
| Axios | HTTP-клиент |
| Zustand | Глобальный стейт |
| Recharts | Графики дашбордов |
| Tailwind CSS | Адаптивная вёрстка |
| React Query (TanStack) | Кэширование запросов |
Структура src/:
```text
src/
├── pages/
│   ├── Cashier/                  # POS + интернет-заказы
│   │   ├── CashierPOS.tsx        # Терминал продаж
│   │   ├── OnlineOrders.tsx      # Интернет-заказы
│   │   └── PaymentModal.tsx      # Модальное окно оплаты
│   ├── RepairMaster/             # Дашборд мастера ремонта
│   │   ├── RepairDashboard.tsx   # Основной дашборд
│   │   ├── TaskCreate.tsx        # Создание задания
│   │   ├── TaskList.tsx          # Список заданий
│   │   └── SalaryView.tsx        # Зарплатная ведомость
│   ├── WashMaster/               # Дашборд мастера мойки
│   │   ├── WashDashboard.tsx
│   │   └── WashTaskCreate.tsx
│   ├── Worker/                   # Аккаунт рабочего
│   │   ├── WorkerTasks.tsx       # Список заданий
│   │   └── WorkerSalary.tsx      # Моя зарплата
│   ├── Warehouse/                # Интерфейс склада
│   │   ├── CentralWarehouse.tsx  # Центральный склад
│   │   └── MiniWarehouse.tsx     # Мини-склад
│   └── Admin/                    # Административная панель
│       └── AdminDashboard.tsx
├── components/
│   ├── Dashboard/                # Компоненты дашбордов
│   ├── Tables/                   # Таблицы
│   ├── Forms/                    # Формы
│   └── Charts/                   # Графики
├── hooks/                        # Кастомные хуки
├── store/                        # Zustand сторы
├── api/                          # API-клиенты (Axios)
└── types/                        # TypeScript типы
```

## 5. ТЕХНИЧЕСКИЙ СТЕК 2 — NODE.JS / EXPRESS
### 5.1 Серверная часть (server.js / Express)

| Технология | Версия | Назначение |
|---|---|---|
| Node.js | 20 LTS | Среда выполнения |
| Express.js | 4 | REST API фреймворк |
| Prisma ORM | 5+ | Работа с PostgreSQL |
| jsonwebtoken | 9+ | JWT-токены |
| bcryptjs | 2+ | Хеширование паролей |
| Multer | 1+ | Загрузка файлов/фото |
| dotenv | 16+ | Переменные окружения |
| cors | 2+ | CORS-политика |
| helmet | 7+ | Заголовки безопасности |
| npm | 10+ | Менеджер пакетов |
Структура проекта:
```text
node-project/
├── server/
│   ├── server.js                 # Точка входа Express
│   ├── prisma/
│   │   └── schema.prisma         # Схема БД (Prisma)
│   ├── routes/
│   │   ├── auth.routes.js        # Авторизация
│   │   ├── orders.routes.js      # Заказы
│   │   ├── tasks.routes.js       # Задания
│   │   ├── warehouse.routes.js   # Склад
│   │   └── dashboard.routes.js   # Дашборды
│   ├── controllers/
│   │   ├── auth.controller.js
│   │   ├── orders.controller.js
│   │   ├── tasks.controller.js
│   │   └── warehouse.controller.js
│   ├── middleware/
│   │   ├── auth.middleware.js     # Проверка JWT
│   │   └── role.middleware.js     # RBAC по ролям
│   └── utils/
│       ├── salary.util.js         # Расчёт зарплаты
│       └── dashboard.util.js      # Агрегация данных
├── package.json
└── .env
```

### 5.2 Пример server.js
```javascript
const express = require('express');
const cors = require('cors');
const helmet = require('helmet');
const morgan = require('morgan');
const { PrismaClient } = require('@prisma/client');

const prisma = new PrismaClient();
const app = express();

// Middleware
app.use(cors({ origin: process.env.FRONTEND_URL }));
app.use(helmet());
app.use(express.json({ limit: '10mb' }));
app.use(morgan('combined'));

// Делаем prisma доступным в запросах
app.use((req, res, next) => {
    req.prisma = prisma;
    next();
});

// Маршруты
app.use('/api/auth',      require('./routes/auth.routes'));
app.use('/api/orders',    require('./routes/orders.routes'));
app.use('/api/tasks',     require('./routes/tasks.routes'));
app.use('/api/warehouse', require('./routes/warehouse.routes'));
app.use('/api/dashboard', require('./routes/dashboard.routes'));

// Обработка ошибок
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(err.status || 500).json({
        error: {
            message: err.message || 'Внутренняя ошибка сервера',
            ...(process.env.NODE_ENV === 'development' && { stack: err.stack })
        }
    });
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
    console.log(`🚀 PitStop API запущен на порту ${PORT}`);
});
```

### 5.3 Middleware авторизации (Node)
```javascript
// middleware/auth.middleware.js
const jwt = require('jsonwebtoken');

const authMiddleware = (req, res, next) => {
    const token = req.headers.authorization?.split(' ')[1];

    if (!token) {
        return res.status(401).json({
            error: 'Требуется авторизация',
            code: 'NO_TOKEN'
        });
    }

    try {
        const decoded = jwt.verify(token, process.env.JWT_SECRET);
        req.user = decoded;
        next();
    } catch (error) {
        if (error.name === 'TokenExpiredError') {
            return res.status(401).json({
                error: 'Токен истёк',
                code: 'TOKEN_EXPIRED'
            });
        }
        return res.status(401).json({
            error: 'Недействительный токен',
            code: 'INVALID_TOKEN'
        });
    }
};

module.exports = authMiddleware;
```

```javascript
// middleware/role.middleware.js
const roleMiddleware = (...allowedRoles) => {
    return (req, res, next) => {
        if (!req.user) {
            return res.status(401).json({ error: 'Требуется авторизация' });
        }

        if (!allowedRoles.includes(req.user.role)) {
            return res.status(403).json({
                error: 'Недостаточно прав',
                code: 'FORBIDDEN',
                required: allowedRoles,
                current: req.user.role
            });
        }

        next();
    };
};

module.exports = roleMiddleware;

// Использование:
// router.post('/api/tasks', authMiddleware, roleMiddleware('repair_master', 'admin'), createTask);
```

### 5.4 Prisma Schema (фрагмент)
```prisma
// prisma/schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

enum Role {
  CASHIER
  REPAIR_MASTER
  REPAIR_WORKER
  WASH_MASTER
  WASH_WORKER
  WAREHOUSE_KEEPER
  TOW_DRIVER
  MOBILE_MECHANIC
  BODYWORK_MASTER
  PAINTER
  EXPERT
  INSURANCE_AGENT
  LAWYER
  CAFE_MANAGER
  CLEANER
  LOGISTICS_DISPATCHER
  TRUCK_DRIVER
  MARKETER
  ACCOUNTANT
  HR_MANAGER
  B2B_MANAGER
  INSPECTOR
  ADMIN
}

model User {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  password  String
  name      String
  role      Role
  phone     String?
  avatarUrl String?
  isActive  Boolean  @default(true)

  masterId  Int?
  master    User?    @relation("MasterWorkers", fields: [masterId], references: [id])
  workers   User[]   @relation("MasterWorkers")

  createdTasks  Task[] @relation("MasterTasks")
  assignedTasks Task[] @relation("WorkerTasks")

  salaryRecords SalaryRecord[]

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}

model Task {
  id          Int      @id @default(autoincrement())
  type        String   // "repair", "wash", "tow", "mobile", "bodywork", "paint"
  title       String
  description String?
  status      String   @default("pending")
  priority    String   @default("medium")
  vehicleInfo Json?

  masterId    Int
  master      User     @relation("MasterTasks", fields: [masterId], references: [id])

  workerId    Int?
  worker      User?    @relation("WorkerTasks", fields: [workerId], references: [id])

  photoUrls   Json     @default("[]")
  dueAt       DateTime?
  completedAt DateTime?

  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt

  @@index([masterId])
  @@index([workerId])
  @@index([status])
}

model Warehouse {
  id       Int    @id @default(autoincrement())
  name     String
  type     String // "central" или "mini"
  location String?

  stocks   WarehouseStock[]
}

model WarehouseStock {
  id          Int @id @default(autoincrement())
  warehouseId Int
  warehouse   Warehouse @relation(fields: [warehouseId], references: [id])
  productId   Int
  product     Product   @relation(fields: [productId], references: [id])
  qty         Int @default(0)
  minQty      Int @default(10)

  @@unique([warehouseId, productId])
}

model Product {
  id       Int      @id @default(autoincrement())
  sku      String   @unique
  name     String
  category String
  price    Decimal  @db.Decimal(10, 2)
  unit     String   @default("шт")
  barcode  String?  @unique

  stocks   WarehouseStock[]
}
```

## 6. ТЕХНИЧЕСКИЕ ЗАДАНИЯ ПО РАЗРАБОТЧИКАМ
### 👑 Разработчик 1 — Тимлид / Архитектор
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Репозиторий | Создать Git-репозиторий, настроить ветки: main, dev, feature/*, hotfix/* |
| 2 | Схема БД | Разработать полную схему PostgreSQL (все таблицы, индексы, внешние ключи, ограничения) |
| 3 | API-спецификация | Составить OpenAPI/Swagger 3.0 спецификацию всех эндпоинтов |
| 4 | Docker Compose | Настроить: PostgreSQL, Redis, PHP-FPM/Nginx (стек 1), Node.js (стек 2) |
| 5 | Seed-данные | Написать скрипты для заполнения тестовыми данными (все роли, товары, задания) |
| 6 | CI/CD | Настроить GitHub Actions: lint, тесты, сборка, деплой |
Deliverable:

docker-compose.yml

database/schema.sql

docs/openapi.yaml

.github/workflows/ci.yml

### 🔧 Разработчик 2 — Backend PHP (Auth + Orders)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Laravel Sanctum | Регистрация, логин, логаут, /me, refresh token |
| 2 | RBAC Middleware | Проверка ролей для всех эндпоинтов |
| 3 | CRUD заказов | Создание, изменение статуса, история, фильтрация |
| 4 | Модуль платежей | Принять оплату: наличные, карта, QR; учёт суммы |
| 5 | Интернет-заказы | Список, фильтры (новые/в обработке/выданы), изменение статуса |
Deliverable:

AuthController.php

OrderController.php

PaymentController.php

Миграции для orders, order_items, payments

PHPUnit тесты

### 📦 Разработчик 3 — Backend PHP (Warehouse + Analytics)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Модуль склада | CRUD товаров, остатки, запросы между складами |
| 2 | Обработка запросов | Одобрение/отклонение, списание товара |
| 3 | Модуль аналитики | Дашборд кладовщика, дашборд мастеров (KPI) |
| 4 | Расчёт зарплаты | SalaryService: выработка × ставка × коэффициент |
| 5 | Экспорт CSV | Генерация отчётов для скачивания |
Deliverable:

WarehouseController.php

DashboardController.php

SalaryService.php

Миграции для warehouses, warehouse_stocks, warehouse_requests, salary_records

PHPUnit тесты

### 🟢 Разработчик 4 — Backend Node.js (Auth + Orders)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | server.js | Базовая настройка Express, cors, helmet, morgan |
| 2 | JWT авторизация | Регистрация, логин, логаут, /me, refresh token |
| 3 | Маршруты auth | auth.routes.js + auth.controller.js |
| 4 | Маршруты orders | Полная реализация Orders API |
| 5 | Middleware | auth.middleware.js, role.middleware.js |
Deliverable:

server.js

auth.routes.js, auth.controller.js

orders.routes.js, orders.controller.js

auth.middleware.js, role.middleware.js

Jest тесты

### 🟡 Разработчик 5 — Backend Node.js (Warehouse + Analytics)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Prisma schema | Все модели + миграции |
| 2 | Маршруты warehouse | Запросы, CRUD, выдача товара |
| 3 | Маршруты tasks | Задания ремонт + мойка |
| 4 | Маршруты dashboard | Агрегация данных для дашбордов |
| 5 | salary.util.js | Расчёт зарплаты |
Deliverable:

prisma/schema.prisma

warehouse.routes.js, warehouse.controller.js

tasks.routes.js, tasks.controller.js

dashboard.routes.js

salary.util.js

Jest тесты

### 🎨 Разработчик 6 — Frontend React (Кассиры + Магазин)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Страница кассира | Поиск товара (поисковая строка + сканер штрихкода), корзина |
| 2 | POS-компонент | Кнопки быстрых товаров, расчёт сдачи, кнопки оплаты |
| 3 | Онлайн-заказы | Список, фильтры по статусу, изменение статуса, уведомления |
| 4 | Модальное окно оплаты | Выбор метода, ввод суммы, печать чека |
| 5 | Адаптивная вёрстка | Планшет 768px+ (2 колонки), ПК 1024px+ (полный интерфейс) |
| 6 | Интеграция с API | Axios-клиент, React Query для кэширования |
Deliverable:

pages/Cashier/CashierPOS.tsx

pages/Cashier/OnlineOrders.tsx

components/POS/

hooks/useOrders.ts

hooks/useProducts.ts

### 👥 Разработчик 7 — Frontend React (Мастера + Рабочие)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Дашборд мастера ремонта | Статистика, статус бригады, список заданий |
| 2 | Создание задания | Форма: описание, авто, приоритет, фото, дедлайн |
| 3 | Список заданий | Таблица с фильтрами, назначение исполнителя |
| 4 | Аккаунт ремонтника | Список заданий, кнопка «Принять»/«Завершить» |
| 5 | Дашборд мастера мойки | Аналогично ремонту |
| 6 | Аккаунт мойщика | Список заданий, статусы |
| 7 | Зарплатная ведомость | Таблица с расчётами за период |
| 8 | Push-уведомления | Уведомление о новом задании (WebSocket опционально) |
Deliverable:

pages/RepairMaster/

pages/WashMaster/

pages/Worker/

components/TaskForm/

components/SalaryTable/

### 📊 Разработчик 8 — Frontend React (Склад + Дашборды)
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Страница кладовщика | Таблица позиций, inline CRUD, обработка запросов |
| 2 | Страница мини-склада | Остатки, кнопка запроса, история поступлений, индикаторы |
| 3 | Общий дашборд | Графики Recharts, KPI-плашки, сводная аналитика |
| 4 | Компонент фильтров | По дате, категории, складу, статусу |
| 5 | Экспорт CSV | Кнопка скачивания данных таблицы |
| 6 | Цветовые индикаторы | Зелёный/жёлтый/красный для уровня остатков |
Deliverable:

pages/Warehouse/CentralWarehouse.tsx

pages/Warehouse/MiniWarehouse.tsx

pages/Admin/AdminDashboard.tsx

components/Charts/

components/Filters/

### 🧪 Разработчик 9 — QA / DevOps
**Задачи:**

| # | Задача | Детали |
|---|---|---|
| 1 | Unit-тесты | Jest для Node.js, PHPUnit для PHP |
| 2 | E2E тесты | Playwright или Cypress: критические пути |
| 3 | Dockerfile | Для каждого сервиса (PHP, Node, React, PostgreSQL, Redis) |
| 4 | docker-compose.yml | Dev и prod конфигурации |
| 5 | README.md | Инструкция по запуску, архитектура, API-документация |
| 6 | Нагрузочное тестирование | k6 или Artillery для ключевых эндпоинтов |
| 7 | Логирование | Настройка Winston (Node) / Monolog (PHP) |
Deliverable:

tests/unit/, tests/e2e/

Dockerfile.php, Dockerfile.node, Dockerfile.react

docker-compose.yml, docker-compose.prod.yml

README.md

k6/load-test.js

## 7. ТРЕБОВАНИЯ К АДАПТИВНОМУ ИНТЕРФЕЙСУ
Все интерфейсы должны корректно отображаться на устройствах:

| Устройство | Ширина экрана | Роли | Особенности |
|---|---|---|---|
| 📱 Смартфон | 320–767px | Ремонтник, мойщик | Крупные кнопки касания (min 44px), минимум текста, свайп-жесты |
| 📋 Планшет | 768–1023px | Кассир, кладовщик | Таблицы в 2 колонки, боковая панель (сворачиваемая) |
| 🖥️ ПК/Ноутбук | 1024px+ | Мастера, кладовщик, админ | Полный дашборд, графики, многоколоночные макеты |
Контрольные точки (breakpoints):
```css
/* Tailwind CSS */
sm:  640px   /* Смартфон (landscape) */
md:  768px   /* Планшет */
lg:  1024px  /* Ноутбук */
xl:  1280px  /* Десктоп */
```

Принципы адаптивности:

| Принцип | Описание |
|---|---|
| 📐 Mobile First | Базовые стили для мобильных, медиа-запросы для расширения |
| 👆 Touch-friendly | Минимальная область касания 44×44px |
| 📏 Относительные единицы | rem, %, vw/vh вместо фиксированных px |
| 🖼️ Адаптивные изображения | srcset, sizes, lazy loading |
| 📋 Адаптивные таблицы | Горизонтальный скролл на мобильных, карточки вместо строк |
## 8. ДОРОЖНАЯ КАРТА РАЗРАБОТКИ (8 НЕДЕЛЬ)
| Неделя | Backend | Frontend | DevOps / QA | Контрольные точки |
|---|---|---|---|---|
| 1–2 | БД: схема, миграции, seed | Роутинг, Layout, авторизация UI | Docker, CI, seed data | ✅ Авторизация работает в обоих стеках |
| 3–4 | API: Auth, Orders, Tasks | Кассир UI, рабочий UI | Unit-тесты Auth | ✅ Можно создать заказ и задание |
| 5–6 | API: Warehouse, Salary, Analytics | Мастера UI, склад UI | Интеграционные тесты | ✅ Полный цикл: заказ → склад → запрос |
| 7 | Оптимизация запросов, экспорт CSV | Дашборды, графики, фильтры | E2E тесты, нагрузка | ✅ Дашборды отображают реальные данные |
| 8 | Финальный review, багфикс | Адаптивность, полировка UI | Деплой, документация | ✅ Продукт готов к демонстрации |
Спринт 1–2 (MVP):
```text
✅ Пользователь может залогиниться
✅ Кассир может создать заказ
✅ Мастер может создать задание
✅ Рабочий может принять задание
✅ Кладовщик видит остатки
```

Спринт 5–6 (Полный функционал):
```text
✅ Работают запросы между складами
✅ Работает расчёт зарплаты
✅ Отображаются дашборды аналитики
✅ Все роли имеют свои интерфейсы
```

## 9. СРАВНЕНИЕ ДВУХ СТЕКОВ

| Критерий | Стек 1: PHP + Laravel | Стек 2: Node.js + Express |
|---|---|---|
| Язык | PHP 8.2 | JavaScript / Node.js 20 |
| Фреймворк | Laravel 11 | Express.js 4 |
| ORM | Eloquent | Prisma |
| Авторизация | Laravel Sanctum (JWT) | jsonwebtoken + bcryptjs |
| Валидация | Form Requests | express-validator / Joi |
| Очереди | Laravel Queue + Redis | Bull + Redis |
| Тестирование | PHPUnit | Jest + Supertest |
| Логирование | Monolog | Winston / Pino |
| Деплой | Apache/Nginx + PHP-FPM | PM2 + Nginx |
| Миграции БД | Laravel Migrations | Prisma Migrate |
| Пакетный менеджер | Composer | npm |

Преимущества каждого стека:

| Стек 1 (PHP/Laravel) | Стек 2 (Node.js/Express) |
|---|---|
| ✅ Встроенная экосистема (Sanctum, Queues, Validation) | ✅ Единый язык (JS) на фронте и бэкенде |
| ✅ Строгая структура проекта (MVC) | ✅ Высокая производительность I/O |
| ✅ Богатая документация на русском | ✅ Лёгкий вход для JS-разработчиков |
| ✅ Стабильность и предсказуемость | ✅ Гибкость архитектуры |
## 10. UML-ДИАГРАММЫ

### 10.1 Use Case диаграмма
```text
┌──────────────────────────────────────────────────────────────────────────┐
│                        PITSTOP MANAGEMENT SYSTEM                          │
│                                                                           │
│  ┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐        │
│  │  Кассир  │     │  Мастер  │     │  Мастер  │     │Кладовщик │        │
│  │   (3)    │     │ ремонта  │     │  мойки   │     │   (2)    │        │
│  │          │     │   (3)    │     │   (4)    │     │          │        │
│  └────┬─────┘     └────┬─────┘     └────┬─────┘     └────┬─────┘        │
│       │                │                │                │               │
│       ▼                ▼                ▼                ▼               │
│  ┌─────────┐     ┌─────────┐     ┌─────────┐     ┌─────────┐            │
│  │Создание │     │Создание │     │Создание │     │Управле- │            │
│  │ заказа  │     │задания  │     │задания  │     │ние скла-│            │
│  │         │     │         │     │         │     │дом      │            │
│  └────┬────┘     └────┬────┘     └────┬────┘     └────┬────┘            │
│       │               │               │               │                  │
│       ▼               ▼               ▼               ▼                  │
│  ┌─────────┐     ┌─────────┐     ┌─────────┐     ┌─────────┐            │
│  │Приём    │     │Назначе- │     │Назначе- │     │Обработка│            │
│  │оплаты   │     │ние исп. │     │ние исп. │     │запросов │            │
│  └─────────┘     └────┬────┘     └────┬────┘     └─────────┘            │
│                       │               │                                  │
│                       ▼               ▼                                  │
│                  ┌─────────┐     ┌─────────┐                             │
│                  │Ремонтник│     │ Мойщик  │                             │
│                  │  (12)   │     │  (16)   │                             │
│                  └────┬────┘     └────┬────┘                             │
│                       │               │                                  │
│                       ▼               ▼                                  │
│                  ┌─────────┐     ┌─────────┐                             │
│                  │Приём    │     │Приём    │                             │
│                  │задания  │     │задания  │                             │
│                  └─────────┘     └─────────┘                             │
│                                                                           │
│  ┌──────────┐                                                            │
│  │  Админ   │                                                            │
│  │   (1)    │                                                            │
│  └────┬─────┘                                                            │
│       │                                                                   │
│       ▼                                                                   │
│  ┌─────────────────────────────────────────────────────────────────┐     │
│  │                      ДАШБОРДЫ АНАЛИТИКИ                           │     │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐        │     │
│  │  │ Заказы   │  │ Склад    │  │Зарплаты  │  │  KPI     │        │     │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘        │     │
│  └─────────────────────────────────────────────────────────────────┘     │
└──────────────────────────────────────────────────────────────────────────┘
```

### 10.2 Диаграмма компонентов
```text
┌──────────────────────────────────────────────────────────────────────────┐
│                        FRONTEND LAYER                                     │
│                        React 18 + Vite                                    │
│                                                                            │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐ │
│  │  CashierApp  │  │ RepairMaster │  │  WashMaster  │  │  Warehouse   │ │
│  │  (POS + Web) │  │   Dashboard  │  │   Dashboard  │  │   App        │ │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘ │
│         │                 │                 │                 │          │
│  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────┴───────┐ │
│  │  WorkerApp   │  │  AdminApp    │  │  AuthModule  │  │  Shared UI   │ │
│  │  (Mobile)    │  │  (Analytics) │  │  (Login/Reg) │  │  Components  │ │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────────────┘ │
│         │                 │                 │                             │
└─────────┼─────────────────┼─────────────────┼─────────────────────────────┘
          │                 │                 │
          ▼                 ▼                 ▼
┌──────────────────────────────────────────────────────────────────────────┐
│                        API GATEWAY LAYER                                  │
│                        REST API (JSON)                                    │
│                                                                            │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐ │
│  │  Auth        │  │  Orders      │  │  Tasks       │  │  Warehouse   │ │
│  │  Service     │  │  Service     │  │  Service     │  │  Service     │ │
│  │              │  │              │  │              │  │              │ │
│  │ • login      │  │ • CRUD       │  │ • CRUD       │  │ • CRUD       │ │
│  │ • logout     │  │ • status     │  │ • assign     │  │ • requests   │ │
│  │ • refresh    │  │ • payments   │  │ • complete   │  │ • approve    │ │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘ │
│         │                 │                 │                 │          │
│  ┌──────┴─────────────────┴─────────────────┴─────────────────┴───────┐ │
│  │                        RBAC Middleware                               │ │
│  │  Проверка ролей: cashier | master | worker | keeper | admin         │ │
│  └─────────────────────────────────────────────────────────────────────┘ │
└─────────┬─────────────────┬─────────────────┬─────────────────────────────┘
          │                 │                 │
          ▼                 ▼                 ▼
┌──────────────────────────────────────────────────────────────────────────┐
│                        DATA LAYER                                         │
│                                                                            │
│  ┌──────────────────────────────┐  ┌──────────────────────────────┐      │
│  │        PostgreSQL 16         │  │         Redis 7               │      │
│  │                              │  │                              │      │
│  │  users          orders       │  │  • JWT blacklist             │      │
│  │  tasks          products     │  │  • Session cache             │      │
│  │  warehouses     payments     │  │  • Queue jobs (Bull)         │      │
│  │  stocks         salary       │  │  • Real-time status          │      │
│  └──────────────────────────────┘  └──────────────────────────────┘      │
└──────────────────────────────────────────────────────────────────────────┘
```

### 10.3 Диаграмма последовательности
Создание и выполнение задания (ремонт):
```text
Мастер         Frontend         API Gateway        БД           Ремонтник
  │                │                 │              │                │
  │  Создать       │                 │              │                │
  │  задание       │                 │              │                │
  │───────────────>│                 │              │                │
  │                │  POST /tasks    │              │                │
  │                │────────────────>│              │                │
  │                │                 │  INSERT      │                │
  │                │                 │─────────────>│                │
  │                │                 │<─────────────│                │
  │                │  { task }       │              │                │
  │                │<────────────────│              │                │
  │  Назначить     │                 │              │                │
  │  исполнителя   │                 │              │                │
  │───────────────>│                 │              │                │
  │                │  PATCH /tasks/  │              │                │
  │                │   :id/assign    │              │                │
  │                │────────────────>│              │                │
  │                │                 │  UPDATE      │                │
  │                │                 │─────────────>│                │
  │                │                 │<─────────────│                │
  │                │<────────────────│              │                │
  │                │                 │              │  Уведомление   │
  │                │                 │──────────────┼───────────────>│
  │                │                 │              │  (WebSocket)   │
  │                │                 │              │                │
  │                │                 │              │  Принять       │
  │                │                 │              │  задание       │
  │                │                 │  PATCH /tasks │<──────────────│
  │                │                 │  /:id/accept  │               │
  │                │                 │<──────────────│               │
  │                │                 │  UPDATE       │               │
  │                │                 │─────────────>│               │
  │                │                 │<─────────────│               │
  │  Статус        │                 │              │               │
  │  обновлён      │  { status:      │              │               │
  │<───────────────│   in_progress } │              │               │
  │                │                 │              │               │
  │                │                 │              │  Завершить    │
  │                │                 │  PATCH /tasks │<──────────────│
  │                │                 │  /:id/complete│               │
  │                │                 │<──────────────│               │
  │                │                 │  UPDATE +     │               │
  │                │                 │  completed_at │               │
  │                │                 │─────────────>│               │
  │                │                 │<─────────────│               │
  │  Задание       │                 │              │               │
  │  выполнено     │  { status:      │              │               │
  │<───────────────│   completed }   │              │               │
```

### 10.4 ER-диаграмма базы данных
```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                           PITSTOP DATABASE SCHEMA                            │
│                                                                              │
│  ┌──────────┐         ┌──────────┐         ┌──────────────┐                 │
│  │  users   │ 1──────┐│  orders  │ 1──────┐│ order_items  │                 │
│  │          │        ││          │        ││              │                 │
│  │ id (PK)  │        ││ id (PK)  │        ││ id (PK)      │                 │
│  │ name     │        ││ type     │        ││ order_id(FK) │                 │
│  │ email    │        ││ status   │        ││ product_id   │                 │
│  │ password │        ││ total    │        ││ qty          │                 │
│  │ role     │        ││ cashier──┼────────││ price        │                 │
│  │ master───┼──┐     ││ created  │        │└──────┬───────┘                 │
│  └──────────┘  │     │└──────────┘        │      │                          │
│       │        │     │       │            │      │                          │
│       │        │     │       │            │      ▼                          │
│       │        │     │       │     ┌──────┴───────────┐                     │
│       │        │     │       │     │   products       │                     │
│       │        │     │       │     │                  │                     │
│       │        │     │       │     │ id (PK)          │                     │
│       │        │     │       │     │ sku (UNIQUE)     │                     │
│       │        │     │       │     │ name             │                     │
│       │        │     │       │     │ category         │                     │
│       │        │     │       │     │ price            │                     │
│       │        │     │       │     │ unit             │                     │
│       │        │     │       │     │ barcode          │                     │
│       │        │     │       │     └──────────────────┘                     │
│       │        │     │       │                                              │
│       ▼        │     │       ▼                                              │
│  ┌──────────┐  │     │  ┌──────────┐                                        │
│  │  tasks   │  │     │  │ payments │                                        │
│  │          │  │     │  │          │                                        │
│  │ id (PK)  │  │     │  │ id (PK)  │                                        │
│  │ type     │  │     │  │ order──┼─┘                                        │
│  │ title    │  │     │  │ method   │                                        │
│  │ status   │  │     │  │ amount   │                                        │
│  │ master───┼──┘     │  │ paid_at  │                                        │
│  │ worker───┼────────┘  └──────────┘                                        │
│  │ due_at   │                                                                │
│  └──────────┘                                                                │
│                                                                              │
│  ┌──────────────┐     ┌──────────────────┐     ┌──────────────────────┐     │
│  │  warehouses  │     │ warehouse_stocks │     │ warehouse_requests   │     │
│  │              │ 1──┐│                  │     │                      │     │
│  │ id (PK)      │    ││ id (PK)          │     │ id (PK)              │     │
│  │ name         │    ││ warehouse_id(FK) │     │ from_wh_id (FK)      │     │
│  │ type         │    ││ product_id (FK)  │     │ to_wh_id (FK)        │     │
│  │ location     │    ││ qty              │     │ product_id (FK)      │     │
│  └──────────────┘    ││ min_qty          │     │ qty                  │     │
│                      │└──────────────────┘     │ status               │     │
│                      │                         │ comment              │     │
│                      │                         └──────┬───────────────┘     │
│                      │                                │                      │
│                      └────────────────────────────────┘                      │
│                                                                              │
│  ┌──────────────────┐                                                       │
│  │  salary_records  │                                                       │
│  │                  │                                                       │
│  │ id (PK)          │                                                       │
│  │ user_id (FK) ────┼───> users                                             │
│  │ period           │                                                       │
│  │ amount           │                                                       │
│  │ hours_worked     │                                                       │
│  │ rate             │                                                       │
│  │ calculated_at    │                                                       │
│  └──────────────────┘                                                       │
└─────────────────────────────────────────────────────────────────────────────┘

Условные обозначения:
────►  Связь один-ко-многим (FK)
 PK    Первичный ключ
 FK    Внешний ключ
```

### 10.5 Диаграмма развёртывания
```text
┌──────────────────────────────────────────────────────────────────────────────┐
│                        PRODUCTION DEPLOYMENT                                  │
│                                                                               │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │                        NGINX (порт 80/443)                                │ │
│  │  • Статические файлы React (/_next, /static)                              │ │
│  │  • Проксирование API → /api/*                                             │ │
│  │  • SSL-терминация (Let's Encrypt)                                         │ │
│  │  • Rate limiting                                                          │ │
│  └───────────────────────┬─────────────────────────────────────────────────┘ │
│                          │                                                    │
│         ┌────────────────┼────────────────┐                                   │
│         │                │                │                                   │
│         ▼                ▼                ▼                                   │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐                              │
│  │  React     │  │  PHP-FPM   │  │  Node.js   │                              │
│  │  (Vite)    │  │  (Laravel) │  │  (Express) │                              │
│  │            │  │            │  │            │                              │
│  │  :3000     │  │  :9000     │  │  :5000     │                              │
│  └────────────┘  └─────┬──────┘  └─────┬──────┘                              │
│                        │                │                                      │
│                        └───────┬────────┘                                      │
│                                │                                               │
│                                ▼                                               │
│                    ┌────────────────────┐                                      │
│                    │    PostgreSQL 16   │                                      │
│                    │    (порт 5432)     │                                      │
│                    │                    │                                      │
│                    │  • Основная БД     │                                      │
│                    │  • Все таблицы     │                                      │
│                    │  • Индексы         │                                      │
│                    └────────────────────┘                                      │
│                                │                                               │
│                                ▼                                               │
│                    ┌────────────────────┐                                      │
│                    │    Redis 7         │                                      │
│                    │    (порт 6379)     │                                      │
│                    │                    │                                      │
│                    │  • Кэш сессий      │                                      │
│                    │  • Очереди (Queue) │                                      │
│                    │  • Pub/Sub         │                                      │
│                    └────────────────────┘                                      │
│                                                                               │
│  Docker Compose:                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐    │
│  │  services:                                                             │    │
│  │    nginx:       ports: ["80:80", "443:443"]                            │    │
│  │    react:       build: ./frontend    ports: ["3000:3000"]              │    │
│  │    php-api:     build: ./stack1-php  ports: ["9000:9000"]              │    │
│  │    node-api:    build: ./stack2-node ports: ["5000:5000"]              │    │
│  │    postgres:    image: postgres:16   ports: ["5432:5432"]              │    │
│  │    redis:       image: redis:7       ports: ["6379:6379"]              │    │
│  └──────────────────────────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────────────────────────┘
```

## 11. API-КОНТРАКТ (OpenAPI/Swagger)
```yaml
openapi: 3.0.3
info:
  title: PitStop Management API
  version: 1.0.0
  description: API для системы управления автосервисом PitStop
  contact:
    name: PitStop Dev Team
    email: dev@pitstop.local

servers:
  - url: http://localhost:5000/api
    description: Node.js (стек 2)
  - url: http://localhost:8000/api
    description: PHP/Laravel (стек 1)

components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT

  schemas:
    User:
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
        email:
          type: string
          format: email
        role:
          type: string
          enum: [cashier, repair_master, repair_worker, wash_master, wash_worker, warehouse_keeper, admin]
        phone:
          type: string
          nullable: true
        isActive:
          type: boolean

    Task:
      type: object
      properties:
        id:
          type: integer
        type:
          type: string
          enum: [repair, wash]
        title:
          type: string
        description:
          type: string
          nullable: true
        status:
          type: string
          enum: [pending, assigned, in_progress, completed, cancelled]
        priority:
          type: string
          enum: [low, medium, high, urgent]
        masterId:
          type: integer
        workerId:
          type: integer
          nullable: true
        vehicleInfo:
          type: object
          nullable: true
        dueAt:
          type: string
          format: date-time
          nullable: true
        createdAt:
          type: string
          format: date-time

    Order:
      type: object
      properties:
        id:
          type: integer
        type:
          type: string
          enum: [retail, online]
        status:
          type: string
          enum: [new, processing, ready, completed, cancelled]
        total:
          type: number
          format: float
        cashierId:
          type: integer
        items:
          type: array
          items:
            $ref: '#/components/schemas/OrderItem'
        createdAt:
          type: string
          format: date-time

    Error:
      type: object
      properties:
        error:
          type: string
        code:
          type: string

security:
  - bearerAuth: []

paths:
  /auth/login:
    post:
      summary: Авторизация пользователя
      tags: [Auth]
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required: [email, password]
              properties:
                email:
                  type: string
                  format: email
                password:
                  type: string
      responses:
        '200':
          description: Успешная авторизация
          content:
            application/json:
              schema:
                type: object
                properties:
                  token:
                    type: string
                  user:
                    $ref: '#/components/schemas/User'

  /auth/me:
    get:
      summary: Получить текущего пользователя
      tags: [Auth]
      security:
        - bearerAuth: []
      responses:
        '200':
          description: Данные пользователя
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'

  /tasks:
    post:
      summary: Создать задание
      tags: [Tasks]
      security:
        - bearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required: [type, title, priority]
              properties:
                type:
                  type: string
                  enum: [repair, wash]
                title:
                  type: string
                description:
                  type: string
                priority:
                  type: string
                  enum: [low, medium, high, urgent]
                vehicleInfo:
                  type: object
                dueAt:
                  type: string
                  format: date-time
      responses:
        '201':
          description: Задание создано
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Task'

  /tasks/{id}/assign:
    patch:
      summary: Назначить исполнителя
      tags: [Tasks]
      security:
        - bearerAuth: []
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: integer
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              required: [workerId]
              properties:
                workerId:
                  type: integer
      responses:
        '200':
          description: Исполнитель назначен

  /warehouse/requests:
    get:
      summary: Получить входящие запросы склада
      tags: [Warehouse]
      security:
        - bearerAuth: []
      parameters:
        - name: status
          in: query
          schema:
            type: string
            enum: [pending, approved, rejected]
      responses:
        '200':
          description: Список запросов
          content:
            application/json:
              schema:
                type: array
                items:
                  type: object
```

## 12. ЛИЦЕНЗИЯ
```text
MIT License (Лицензия MIT)

Copyright (c) 2025 PitStop Dev Team

Данная лицензия разрешает лицам, получившим копию данного программного 
обеспечения и сопутствующей документации (в дальнейшем именуемыми «Программное 
Обеспечение»), безвозмездно использовать Программное Обеспечение без ограничений, 
включая неограниченное право на использование, копирование, изменение, слияние, 
публикацию, распространение, сублицензирование и/или продажу копий Программного 
Обеспечения, а также лицам, которым предоставляется данное Программное 
Обеспечение, при соблюдении следующих условий:

Указанное выше уведомление об авторском праве и данные условия должны быть 
включены во все копии или значимые части данного Программного Обеспечения.

ДАННОЕ ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ ПРЕДОСТАВЛЯЕТСЯ «КАК ЕСТЬ», БЕЗ КАКИХ-ЛИБО 
ГАРАНТИЙ, ЯВНО ВЫРАЖЕННЫХ ИЛИ ПОДРАЗУМЕВАЕМЫХ, ВКЛЮЧАЯ ГАРАНТИИ ТОВАРНОЙ 
ПРИГОДНОСТИ, СООТВЕТСТВИЯ ПО ЕГО КОНКРЕТНОМУ НАЗНАЧЕНИЮ И ОТСУТСТВИЯ 
НАРУШЕНИЙ, НО НЕ ОГРАНИЧИВАЯСЬ ИМИ.
```

## 📚 ПОЛЕЗНЫЕ ССЫЛКИ
| Ресурс | Ссылка |
|---|---|
| Laravel Документация | https://laravel.com/docs/11.x |
| Express.js Guide | https://expressjs.com/ru/ |
| Prisma Docs | https://www.prisma.io/docs |
| React Docs | https://react.dev |
| Tailwind CSS | https://tailwindcss.com/docs |
| PostgreSQL Docs | https://www.postgresql.org/docs/16/ |
| Redis Docs | https://redis.io/docs/ |
| Docker Docs | https://docs.docker.com |
| OpenAPI Spec | https://swagger.io/specification/ |

<div align="center">
PITSTOP MANAGEMENT SYSTEM

Комплексная информационная система управления автосервисом

Техническое задание для 9 разработчиков • 2025 г.

https://img.shields.io/badge/PHP-8.2-777BB4?logo=php
https://img.shields.io/badge/Laravel-11-FF2D20?logo=laravel
https://img.shields.io/badge/Node.js-20-339933?logo=node.js
https://img.shields.io/badge/React-18-61DAFB?logo=react
https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql
https://img.shields.io/badge/Redis-7-DC382D?logo=redis
https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker

</div>

---

## 13. ТЕМЫ ДИПЛОМНЫХ РАБОТ И ТЕХНИЧЕСКОЕ ЗАДАНИЕ (ТЗ)

Ниже представлены 25 тем выпускных квалификационных (дипломных) работ, распределенных между членами команды разработчиков, с индивидуальным техническим заданием (ТЗ) для каждого студента.

### 🎓 1. Разработчик 1 (Тимлид / Архитектор)
**Тема:** «Проектирование архитектуры, базы данных и DevOps-инфраструктуры распределенной информационной системы управления автосервисом»

**Техническое задание:**
1. Спроектировать ER-модель реляционной базы данных PostgreSQL для хранения информации о пользователях, заказах, складах и заданиях.
2. Разработать единую спецификацию REST API (OpenAPI/Swagger) для взаимодействия между фронтендом и двумя вариантами бекенда.
3. Спроектировать UML-диаграммы системы (диаграммы прецедентов, компонентов, последовательности и развертывания).
4. Разработать и настроить инфраструктуру контейнеризации (Docker, Docker Compose) для унифицированного запуска проектов.
5. Настроить CI/CD пайплайны для автоматического тестирования и деплоя компонентов системы.

---

### 🎓 2. Разработчик 2 (Backend PHP 1 — Auth & Orders)
**Тема:** «Разработка модуля обработки онлайн-заказов, платежей и системы аутентификации на базе фреймворка Laravel»

**Техническое задание:**
1. Разработать систему защищенной авторизации пользователей на базе JSON Web Tokens (Laravel Sanctum) с поддержкой обновления токенов.
2. Реализовать программный слой проверки прав доступа (RBAC Middleware) для 7 различных ролей системы.
3. Разработать REST API для модуля заказов: создание, обновление статусов, фильтрация и история покупок.
4. Спроектировать и реализовать модуль фиксации платежей (наличные, карта) с привязкой к конкретным заказам и кассирам.
5. Написать модульные тесты (PHPUnit) для проверки бизнес-логики оформления интернет-заказов.

---

### 🎓 3. Разработчик 3 (Backend PHP 2 — Warehouse & Analytics)
**Тема:** «Автоматизация складского учета и системы расчета заработной платы автосервиса средствами PHP и Laravel»

**Техническое задание:**
1. Разработать серверное API для управления справочником товаров (CRUD), категорий и штрихкодов.
2. Реализовать бизнес-логику движения товаров: запросы на пополнение мини-складов, одобрение запросов и списание остатков.
3. Спроектировать сервис агрегации данных для генерации аналитических дашбордов (загруженность, движение товара).
4. Разработать алгоритм автоматического расчета сдельной заработной платы сотрудников на основе выполненных заданий и коэффициентов.
5. Реализовать функцию генерации и выгрузки складских отчетов в формате CSV.

---

### 🎓 4. Разработчик 4 (Backend Node.js 1 — Auth & Orders)
**Тема:** «Реализация подсистемы аутентификации и обработки заказов автосервиса с использованием платформы Node.js и Express»

**Техническое задание:**
1. Спроектировать базовую архитектуру REST-сервера на Express с настройкой политик CORS и безопасности (Helmet).
2. Реализовать механизмы выпуска и верификации JWT-токенов для авторизации пользователей.
3. Написать Middleware-функции для защиты маршрутов и проверки ролевого доступа.
4. Разработать контроллеры и маршруты для оформления клиентских заказов, управления корзиной и статусами продаж.
5. Покрыть разработанное API интеграционными тестами с использованием связки Jest + Supertest.

---

### 🎓 5. Разработчик 5 (Backend Node.js 2 — Warehouse & Analytics)
**Тема:** «Разработка модуля маршрутизации заданий и складской аналитики с применением Node.js и Prisma ORM»

**Техническое задание:**
1. Описать схему реляционной базы данных с использованием Prisma Schema и настроить систему миграций.
2. Разработать API для создания, назначения и мониторинга заданий для ремонтников и мойщиков.
3. Реализовать программные интерфейсы для учета складских остатков и движения запасных частей.
4. Разработать высокопроизводительные эндпоинты для сбора статистических данных и отображения KPI мастеров.
5. Написать модули-хелперы для выполнения математических расчетов выработки бригад.

---

### 🎓 6. Разработчик 6 (Frontend React 1 — Cashiers & Shop)
**Тема:** «Проектирование и разработка адаптивного POS-интерфейса рабочего места кассира автомагазина (SPA на React)»

**Техническое задание:**
1. Разработать эргономичный пользовательский интерфейс POS-терминала с корзиной и функцией быстрого поиска товаров (по артикулу и штрихкоду).
2. Спроектировать компонент управления интернет-заказами (канбан-доска или таблица с фильтрацией статусов).
3. Реализовать интерактивное модальное окно принятия оплаты и формирования электронных чеков.
4. Разработать адаптивную верстку (Tailwind CSS) с поддержкой работы на планшетах (768px+) и широкоформатных мониторах.
5. Настроить взаимодействие с REST API сервера с применением React Query для кэширования ответов.

---

### 🎓 7. Разработчик 7 (Frontend React 2 — Masters & Workers)
**Тема:** «Разработка интерактивных рабочих кабинетов и дашбордов управления персоналом автосервиса на React»

**Техническое задание:**
1. Разработать графический интерфейс личных кабинетов для рядовых сотрудников (ремонтников и мойщиков), оптимизированный под мобильные устройства (смартфоны).
2. Спроектировать дашборд мастера с возможностью создания заданий, назначения исполнителей и изменения приоритетов.
3. Реализовать функционал загрузки изображений (фотографий выполненных работ) и просмотра деталей заказов-нарядов.
4. Разработать компоненты для отображения расчётных листков (зарплат) сотрудников.
5. Интегрировать механизмы клиентской валидации форм с использованием React Hook Form.

---

### 🎓 8. Разработчик 8 (Frontend React 3 — Warehouse & Dashboards)
**Тема:** «Создание графического интерфейса системы складского учета и визуализации бизнес-аналитики предприятия»

**Техническое задание:**
1. Разработать интерфейсы управления центральным и мини-складами (просмотр остатков, создание запросов на пополнение).
2. Реализовать интерактивные CRUD-таблицы (добавление, редактирование, удаление) для справочника товаров с клиентской пагинацией.
3. Спроектировать панель кладовщика для обработки и подтверждения заявок со смежных складов.
4. Интегрировать библиотеку построения графиков (Recharts/Chart.js) для визуализации движения товаров и финансовых потоков.
5. Настроить систему визуальных уведомлений (toast-нотификаций) при изменении статусов товаров.

---

### 🎓 9. Разработчик 9 (QA Engineer / DevOps)
**Тема:** «Автоматизация процессов тестирования, развертывания и обеспечения качества программного обеспечения информационной системы»

**Техническое задание:**
1. Разработать тестовую стратегию и тест-планы для основных пользовательских сценариев (кассир, мастер, кладовщик).
2. Написать E2E (End-to-End) тесты интерфейса с использованием современных фреймворков (Cypress или Playwright).
3. Настроить процессы статического анализа кода (ESLint, Prettier, PHP CodeSniffer) в рамках пайплайнов.
4. Обеспечить непрерывную интеграцию (CI/CD) в GitHub Actions для сборки клиентской и серверной частей.
5. Подготовить эксплуатационную документацию и сценарии восстановления системы после сбоев.

---

### 🎓 10. Разработчик 10 (Backend — Выездной сервис и эвакуаторы)
**Тема:** «Проектирование и разработка модулей круглосуточной службы эвакуации и мобильного выездного сервиса автосервиса»

**Техническое задание:**
1. Разработать систему трекинга эвакуаторов в реальном времени (обработка потока GPS-координат).
2. Реализовать алгоритмы маршрутизации и приёма экстренных вызовов для водителей эвакуаторов.
3. Разработать API для выездного шиномонтажа, включая логику создания "виртуального склада" (фургона) и списания запчастей на месте.
4. Спроектировать модуль генерации актов выполненных работ и маршрутных листов.
5. Реализовать интеграцию с мобильными платежными терминалами (проведение оплаты на месте поломки).

---

### 🎓 11. Разработчик 11 (Backend — Кузовной ремонт и покраска)
**Тема:** «Автоматизация бизнес-процессов участка кузовного ремонта, малярных работ и калькуляции смет»

**Техническое задание:**
1. Разработать сложный модуль калькуляции смет для ремонта после ДТП (учет запчастей, лакокрасочных материалов, норм времени).
2. Реализовать систему управления расписанием и бронированием покрасочных (сушильных) камер во избежание накладок.
3. Создать API для специфических запросов на склад (подбор цвета автоэмали колористом).
4. Разработать систему поэтапной фотофиксации кузовного ремонта с возможностью предоставления отчета клиенту.
5. Настроить интеграцию с основным финансовым модулем для учета стоимости длительных ремонтных циклов.

---

### 🎓 12. Разработчик 12 (Frontend React 4 — Мобильные бригады и кузовной цех)
**Тема:** «Разработка специализированных пользовательских интерфейсов для выездных сервисных бригад и мастеров кузовного ремонта на базе React»

**Техническое задание:**
1. Спроектировать мобильный интерфейс (PWA/Responsive) для водителей эвакуаторов и мастеров выездного шиномонтажа с крупными элементами управления.
2. Интегрировать картографические сервисы (Yandex Maps / Google Maps API) для отображения маршрутов и локаций клиентов.
3. Разработать десктопный/планшетный интерфейс конструктора смет кузовного ремонта с возможностью добавления позиций и автоподсчета сумм.
4. Создать визуальный календарь-планировщик (Gantt или таймлайн) для управления загрузкой покрасочных камер.
5. Реализовать модуль загрузки, обработки и галерейного просмотра фотографий автомобилей до и после ремонта.

---

### 🎓 13. Разработчик 13 (Backend — Юриспруденция и Экспертиза)
**Тема:** «Проектирование и разработка модулей независимой автоэкспертизы, страхования и адвокатского сопровождения»

**Техническое задание:**
1. Разработать систему ЭДО (электронного документооборота) для генерации страховых полисов и юридических исков.
2. Создать API-шлюз для интеграции с внешними системами страховых компаний (симуляция РСА).
3. Реализовать модуль ведения дел (Case Management System) для адвокатов.
4. Спроектировать базу данных для хранения актов независимой оценки с привязкой к сметному модулю кузовного цеха.
5. Настроить строгий контроль доступа (RBAC) к конфиденциальной юридической информации клиентов.

---

### 🎓 14. Разработчик 14 (Backend — HoReCa и Клининг)
**Тема:** «Автоматизация сопутствующих бизнес-процессов автосервиса: гостиничного комплекса, кафе и службы клининга»

**Техническое задание:**
1. Разработать бэкенд системы бронирования (шахматки) гостиничных номеров для клиентов автосервиса.
2. Реализовать логику работы POS-терминала кафе (управление меню, технологическими картами, заказами столов).
3. Разработать алгоритм автоматического назначения задач службе клининга при выселении из номера или по расписанию цехов.
4. Интегрировать финансовые операции кафе и отеля в общую кассовую систему предприятия.
5. Настроить сбор метрик и формирование отчетов о прибыльности не-автомобильных направлений.

---

### 🎓 15. Разработчик 15 (Frontend React 5 — Юр. блок и HoReCa)
**Тема:** «Разработка пользовательских интерфейсов для юридического отдела, кафе и гостиничного комплекса на базе React»

**Техническое задание:**
1. Спроектировать интерфейс "шахматки" для наглядного управления бронированием номеров гостиницы.
2. Разработать touch-интерфейс кассы кафе для быстрого формирования заказов.
3. Создать строгий корпоративный интерфейс для адвокатов: карточки дел, таймлайны судов, конструктор документов.
4. Разработать форму-визард для проведения независимой экспертизы автомобиля и оформления электронного полиса.
5. Создать мобильное PWA-приложение для сотрудников клининга (чек-листы уборки, отметки о выполнении).

---

### 🎓 16. Разработчик 16 (Backend — Логистика и Маршрутизация)
**Тема:** «Разработка алгоритмов маршрутизации и управления грузоперевозками в масштабах города, региона и страны»

**Техническое задание:**
1. Разработать ядро системы распределения заказов на перевозку в зависимости от габаритов груза и расстояния.
2. Интегрировать API картографических сервисов для автоматического расчета километража и времени в пути (с учетом пробок).
3. Создать модуль генерации транспортных накладных (ТТН) и путевых листов.
4. Разработать алгоритм динамического ценообразования (расчет стоимости фрахта по РФ).
5. Настроить API-шлюз для получения GPS-данных с трекеров, установленных на транспортных средствах.

---

### 🎓 17. Разработчик 17 (Backend — Управление автопарком)
**Тема:** «Автоматизация учета, технического обслуживания и топливной аналитики транспортного парка»

**Техническое задание:**
1. Разработать структуру БД для учета транспортных средств различного класса (от легких коммерческих автомобилей до магистральных тягачей).
2. Реализовать модуль контроля сроков действия документов (ОСАГО, КАСКО, ДОПОГ, диагностические карты).
3. Разработать подсистему учета расхода горюче-смазочных материалов (ГСМ) и интеграцию с топливными картами.
4. Создать сервис автоматического планирования планового ТО для фур и грузовиков (интеграция с ремонтными мастерскими проекта).
5. Написать аналитический модуль для расчета рентабельности каждого автомобиля в автопарке.

---

### 🎓 18. Разработчик 18 (Frontend React 6 — Логистика и Транспорт)
**Тема:** «Проектирование диспетчерских дашбордов и мобильных интерфейсов водителей магистральных тягачей на базе React»

**Техническое задание:**
1. Разработать интерактивный экран диспетчера-логиста с визуализацией всех активных рейсов по России на интерактивной карте.
2. Спроектировать мобильный интерфейс (PWA) для дальнобойщиков: получение путевого листа, отметка точек погрузки/выгрузки, чат с диспетчером.
3. Реализовать интерфейс управления автопарком (таблицы с фильтрацией по статусам: в рейсе, на ремонте, свободен).
4. Создать дашборды финансовой аналитики транспортного подразделения (графики расходов на топливо, выручки с рейсов).
5. Интегрировать систему push-уведомлений для оповещения диспетчеров о внештатных ситуациях на трассе.

---

### 🎓 19. Разработчик 19 (Backend — CRM, Маркетинг и Лояльность)
**Тема:** «Разработка CRM-подсистемы и инструментов удержания клиентов в рамках ERP автосервиса»

**Техническое задание:**
1. Разработать движок программы лояльности (начисление/списание бонусов, реферальные ссылки).
2. Настроить API-интеграцию с SMS/Email/Push шлюзами для триггерных рассылок.
3. Разработать систему интеграции с IP-телефонией (всплывающие карточки клиентов).
4. Создать серверную часть личного кабинета (мобильного приложения) автовладельца.
5. Настроить систему сегментации клиентской базы (RFM-анализ).

---

### 🎓 20. Разработчик 20 (Backend — Бухгалтерия и Кадры)
**Тема:** «Проектирование модулей финансового учета, интеграции с 1С и кадрового администрирования»

**Техническое задание:**
1. Создать API для двусторонней синхронизации документов с 1С:Бухгалтерией.
2. Реализовать сложную систему учета дебиторской и кредиторской задолженности.
3. Спроектировать модуль управления кадрами (графики сменности, больничные, отпуска).
4. Разработать алгоритм расчета KPI и премий для 15 различных должностей.
5. Автоматизировать генерацию расчетных листков и кадровых приказов.

---

### 🎓 21. Разработчик 21 (Backend — Автопрокат и Авторазбор)
**Тема:** «Автоматизация процессов аренды подменных автомобилей и утилизации запчастей»

**Техническое задание:**
1. Разработать систему биллинга и управления договорами посуточной аренды автомобилей.
2. Интегрировать API ГИБДД для автоматической проверки и перевыставления штрафов клиентам.
3. Создать модуль дефектовки битых автомобилей (превращение 1 авто в 1000 Б/У запчастей).
4. Разработать функционал генерации уникальных штрихкодов для Б/У деталей.
5. Настроить экспорт каталога Б/У запчастей на внешние площадки (Авито, Дром) через XML-фиды.

---

### 🎓 22. Разработчик 22 (Backend — B2B и СТО)
**Тема:** «Программный комплекс по работе с корпоративными автопарками и автоматизации техосмотра»

**Техническое задание:**
1. Реализовать логику ведения договоров с таксопарками и курьерскими службами.
2. Разработать систему массового выставления счетов и актов выполненных работ (ЭДО).
3. Создать модуль проведения техосмотра (СТО) с фиксацией показаний приборов.
4. Настроить защищенное соединение с государственной базой ЕАИСТО для выдачи диагностических карт.
5. Спроектировать систему хранения медиафайлов (фото/видео процесса техосмотра).

---

### 🎓 23. Разработчик 23 (Frontend React 7 — CRM, B2B и Финансы)
**Тема:** «Проектирование аналитических дашбордов и рабочих мест для административно-управленческого персонала на базе React»

**Техническое задание:**
1. Разработать сложный финансовый дашборд (P&L, Cash Flow) с использованием продвинутых графиков.
2. Создать рабочее место маркетолога для визуального построения воронок продаж и сегментов.
3. Разработать B2B-кабинет для корпоративных клиентов (просмотр актов, счетов, истории ремонтов парка).
4. Спроектировать интерфейс HR-менеджера (диаграммы Ганта для отпусков, табели учета рабочего времени).
5. Реализовать табличные интерфейсы с глубокой фильтрацией и экспортом в Excel/PDF.

---

### 🎓 24. Разработчик 24 (Frontend React 8 — Прокат, Разбор и СТО)
**Тема:** «Разработка графических интерфейсов для смежных автомобильных сервисов (прокат, утилизация, техосмотр)»

**Техническое задание:**
1. Разработать интерфейс "шахматки" для управления автопарком проката (занято/свободно/ремонт).
2. Спроектировать интерфейс дефектовщика с удобным добавлением фотографий Б/У запчастей с веб-камеры.
3. Создать форму проведения техосмотра с валидацией обязательных полей по стандартам ГИБДД.
4. Разработать клиентское мобильное PWA-приложение (личный кабинет автовладельца, онлайн-запись).
5. Настроить сканирование QR-кодов и штрихкодов деталей напрямую через браузер устройства.

---

### 🎓 25. Разработчик 25 (Fullstack — Корпоративный Университет)
**Тема:** «Разработка платформы внутреннего обучения, онбординга и аттестации сотрудников предприятия»

**Техническое задание:**
1. Спроектировать базу данных для хранения курсов, тестов, видеоматериалов и результатов.
2. Разработать REST API для прохождения тестирований с ограничением по времени.
3. Создать интерфейс конструктора тестов для администратора (разные типы вопросов, веса ответов).
4. Разработать личный кабинет сотрудника с прогрессом обучения (геймификация, ачивки).
5. Интегрировать модуль обучения в систему расчета KPI (допуск к сложным ремонтам только после сдачи теста).