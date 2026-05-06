I will now create a detailed business project for a PitStop management system, designed for 9 students. The system includes roles for cashiers, repair and wash masters with their teams, and warehouse keepers, built using two tech stacks. I'll also incorporate high-quality, production-ready frontend interfaces with a unique aesthetic.

First, I'll organize the project structure and define the business logic.

Project Structure:

text
pitstop-system/
├── stack1-php-react/          # PHP + React version
├── stack2-node-react/         # Node.js + React version
├── frontend-interfaces/       # Production-ready UI components
└── docs/
    ├── technical-spec.md
    ├── uml-diagrams/
    └── api-contracts.md
Now, let's start with the UML diagrams and the technical specification document.

Technical Specification (Technical Spec for all Developers)

1. System Architecture Overview

The PitStop Management System is a comprehensive web-based platform for managing an auto service (pit stop). It encompasses a retail store, an online store, a car wash area, a repair zone, a centralized warehouse, and three mini-warehouses. The system is

на сусском
Понял, перехожу на русский. Создам полный бизнес-проект на русском языке с техническим заданием, UML-схемами и описанием архитектуры в двух стеках.

Ниже — полный документ, который можно сразу использовать как ТЗ для команды из 9 студентов.

БИЗНЕС-ПРОЕКТ: PITSTOP MANAGEMENT SYSTEM
Автоматизированная система управления автосервисом
Техническое задание для команды из 9 разработчиков
Стек 1: PHP / Laravel + React + PostgreSQL
Стек 2: Node.js / Express + React + PostgreSQL

2025 г.

1. ОБЩЕЕ ОПИСАНИЕ ПРОЕКТА
Проект PitStop — многоуровневая веб-система управления автосервисом, включающая:

Магазин розничных продаж

Интернет-магазин

Участок мойки автомобилей

Ремонтный участок

Централизованный склад

Три мини-склада

Система разрабатывается командой из 9 студентов в двух параллельных вариантах:

Серверный на PHP/Laravel

Серверный на Node.js/Express

с единым React-фронтендом и PostgreSQL в качестве базы данных.

1.1 Цели системы
Автоматизация рабочих мест кассиров (магазин + интернет-магазин)

Управление задачами ремонтников и мойщиков через мастеров

Централизованный склад с выдачей на 2 склада и магазин

Дашборды аналитики по заказам, складам, зарплатам, KPI

Адаптивный интерфейс для всех ролей (смартфон, планшет, ПК)

1.2 Распределение команды (9 студентов)
#	Роль	Стек	Модуль	Ответственность
1	Тимлид / Архитектор	Оба	Архитектура + DevOps	Структура БД, API-контракт, деплой
2	Backend PHP-разработчик 1	PHP/Laravel	Auth + Orders	JWT-авторизация, заказы, кассиры
3	Backend PHP-разработчик 2	PHP/Laravel	Warehouse + Analytics	Склад, запросы, дашборды
4	Backend Node-разработчик 1	Node.js/Express	Auth + Orders	server.js, JWT, заказы
5	Backend Node-разработчик 2	Node.js/Express	Warehouse + Analytics	Склад, Express routes
6	Frontend-разработчик 1	React + Vite	Кассиры + Магазин	POS-интерфейс, интернет-магазин
7	Frontend-разработчик 2	React + Vite	Мастера + Рабочие	Дашборды мастеров, аккаунты
8	Frontend-разработчик 3	React + Vite	Склад + Дашборды	Интерфейс склада, аналитика
9	QA / DevOps	Все	Тестирование + CI/CD	Тесты, Docker, документация
2. РОЛИ ПОЛЬЗОВАТЕЛЕЙ И ИХ ИНТЕРФЕЙСЫ
2.1 Кассиры — 3 рабочих места
Интерфейс: POS-терминал + панель интернет-заказов. Адаптивный дизайн (планшет/ПК).

Функционал:

Создание и оформление заказа покупателя (физический магазин)

Обработка заказов из интернет-магазина (новые / в обработке / выданы)

Приём оплаты: наличные, карта, QR-код

Просмотр текущих остатков магазинного мини-склада

Печать чека / формирование электронного чека

Поиск товаров по артикулу, названию, штрихкоду

API-маршруты:

text
POST   /api/orders               — создать заказ
GET    /api/orders?type=online    — список интернет-заказов
PATCH  /api/orders/:id/status     — изменить статус заказа
GET    /api/products?search=...   — поиск товаров
POST   /api/payments              — оформить платёж
2.2 Мастера ремонта — 3 куратора
Каждый мастер курирует 4 ремонтников. Интерфейс: дашборд + список задач + зарплата.

Функционал:

Создание задания для ремонтника с описанием, фото, приоритетом

Назначение задания конкретному ремонтнику из своей группы

Мониторинг статусов заданий в реальном времени

Просмотр зарплатной ведомости своих подчинённых

Запрос запчастей со склада

Дашборд: выполнено / в работе / просрочено за период

API-маршруты:

text
POST   /api/tasks                 — создать задание
GET    /api/tasks?master_id=...   — мои задания
PATCH  /api/tasks/:id/assign      — назначить ремонтнику
GET    /api/salary?user_id=...    — зарплата сотрудников
POST   /api/warehouse/request     — запрос запчастей
2.3 Ремонтники — 12 аккаунтов (3 мастера × 4)
Упрощённый адаптивный интерфейс на смартфон/планшет. Только приём и выполнение заданий.

Функционал:

Личный кабинет: список назначенных заданий

Принятие задания в работу (кнопка «Принять»)

Изменение статуса: В работе → Завершено

Прикрепление фото результата (опционально)

Просмотр своей зарплаты и смен

API-маршруты:

text
GET    /api/tasks/my              — мои задания
PATCH  /api/tasks/:id/accept      — принять задание
PATCH  /api/tasks/:id/complete    — завершить задание
2.4 Мастера мойки — 4 куратора
Аналогична структуре мастеров ремонта. Каждый мастер управляет 4 мойщиками.

Функционал:

Создание задания на мойку (тип, авто, время)

Назначение задания мойщику

Дашборд: загрузка по слотам времени, статистика за день

Зарплатная ведомость своей группы

API-маршруты:

text
POST   /api/wash-tasks            — задание на мойку
GET    /api/wash-tasks?master=... — задания мастера
PATCH  /api/wash-tasks/:id/assign — назначить мойщику
2.5 Мойщики — 16 аккаунтов (4 мастера × 4)
Функционал:

Приём задания на мойку

Изменение статуса: В очереди → Выполняется → Завершено

Просмотр своей зарплаты

API-маршруты:

text
GET    /api/wash-tasks/my         — мои задания
PATCH  /api/wash-tasks/:id/start  — начать
PATCH  /api/wash-tasks/:id/done   — завершить
2.6 Кладовщики — 2 аккаунта (центральный склад)
Управляют центральным складом. Принимают запросы от 2 мини-складов и магазина, выдают товар.

Функционал:

Просмотр входящих запросов (от кого, что, сколько)

Одобрение / отклонение запроса с комментарием

Списание товара с центрального склада

Приём нового товара на центральный склад

Дашборд: остатки по позициям, топ-запросы, история движения

CRUD товаров: добавление, удаление, корректировка количества и цены

API-маршруты:

text
GET    /api/warehouse/requests    — входящие запросы
PATCH  /api/warehouse/requests/:id/approve  — одобрить
POST   /api/warehouse/products   — добавить товар
PATCH  /api/warehouse/products/:id          — обновить
DELETE /api/warehouse/products/:id          — удалить
GET    /api/warehouse/dashboard  — аналитика склада
3. СКЛАДСКАЯ СИСТЕМА И ДАШБОРДЫ
3.1 Структура складов
Склад	Пользователи	Интерфейс	Источник данных
Центральный склад	2 кладовщика	Полный CRUD + дашборд	Прямой ввод
Мини-склад 1 (ремонт)	1 ответственный	Просмотр + запросы	Центральный склад
Мини-склад 2 (мойка)	1 ответственный	Просмотр + запросы	Центральный склад
Магазин	Кассиры (3)	Просмотр остатков	Центральный склад
3.2 Дашборд мини-склада
Каждый из 3 мини-складов (включая магазин) имеет собственный дашборд:

Таблица текущих позиций: артикул, название, количество, ед. изм., минимальный остаток

Кнопка «Запросить» — отправить запрос на центральный склад

Фильтры: по категории, по статусу (в наличии / заканчивается / отсутствует)

История поступлений: дата, количество, статус запроса

Визуальный индикатор уровня остатков (цвет: зелёный/жёлтый/красный)

3.3 Дашборд кладовщика (центральный склад)
Сводная таблица всех позиций с фильтрами по складу-получателю

Панель входящих запросов с возможностью одобрения/отклонения

Диаграмма движения товара за период (поступления / выдачи)

CRUD-таблица товаров: добавление, редактирование inline, удаление с подтверждением

Экспорт в CSV/Excel

3.4 Дашборд мастера
Текущая загрузка: сколько заданий в работе / в ожидании

Статус каждого подчинённого (онлайн / в задании / свободен)

Зарплатная ведомость: выработка, ставка, итого за месяц

История заданий с фильтрами: по дате, по статусу, по ремонтнику

KPI-плашки: среднее время выполнения, % в срок

4. ТЕХНИЧЕСКИЙ СТЕК 1 — PHP / LARAVEL + REACT + POSTGRESQL
4.1 Серверная часть (PHP)
Технологии:

PHP 8.2+

Laravel 11 (MVC, Eloquent ORM, Sanctum для JWT)

PostgreSQL 16 (основная БД)

Redis (кэш сессий, очереди задач)

Laravel Queues (фоновые задачи, уведомления)

Composer (менеджер зависимостей)

Структура директорий:

text
app/
  Http/Controllers/Api/
    AuthController.php
    OrderController.php
    TaskController.php
    WashTaskController.php
    WarehouseController.php
    DashboardController.php
  Models/
    User.php, Order.php, Task.php
    Product.php, Warehouse.php
  Services/
    WarehouseService.php
    SalaryService.php
routes/api.php
database/migrations/
4.2 Аутентификация (PHP)
Используется Laravel Sanctum. Каждый пользователь имеет роль в таблице users.role:

cashier — кассир

repair_master — мастер ремонта

repair_worker — ремонтник

wash_master — мастер мойки

wash_worker — мойщик

warehouse_keeper — кладовщик

admin — администратор

text
POST /api/auth/login   — логин, возвращает token
POST /api/auth/logout  — логаут
GET  /api/auth/me      — текущий пользователь + роль
4.3 Схема БД PostgreSQL
Таблица	Ключевые поля	Описание
users	id, name, email, password, role, master_id	Все пользователи системы
orders	id, type, status, total, cashier_id, created_at	Заказы магазина и онлайн
order_items	id, order_id, product_id, qty, price	Позиции заказа
products	id, sku, name, category, price, unit	Справочник товаров
tasks	id, type, title, status, master_id, worker_id, due_at	Задания (ремонт/мойка)
warehouses	id, name, type (central/mini), location	Склады
warehouse_stocks	id, warehouse_id, product_id, qty, min_qty	Остатки на складе
warehouse_requests	id, from_wh, to_wh, product_id, qty, status	Запросы между складами
salary_records	id, user_id, period, amount, calculated_at	Расчёт зарплаты
payments	id, order_id, method, amount, paid_at	Платежи
4.4 Frontend (React — Стек 1)
Технологии:

React 18 + Vite + TypeScript

React Router v6 (роутинг по ролям)

Axios (HTTP-клиент)

Zustand или Redux Toolkit (глобальный стейт)

Recharts (графики дашбордов)

Tailwind CSS (адаптивная вёрстка)

React Query (кэширование запросов)

Структура src/:

text
src/
  pages/
    Cashier/     — POS + интернет-заказы
    RepairMaster/ — дашборд мастера ремонта
    WashMaster/   — дашборд мастера мойки
    Worker/       — аккаунт рабочего
    Warehouse/    — интерфейс склада
    Admin/        — административная панель
  components/
    Dashboard/, Tables/, Forms/, Charts/
  hooks/
  store/
  api/
5. ТЕХНИЧЕСКИЙ СТЕК 2 — NODE.JS / EXPRESS + REACT + POSTGRESQL
5.1 Серверная часть (server.js / Express)
Технологии:

Node.js 20 LTS

Express.js 4 (REST API)

Prisma ORM (работа с PostgreSQL)

jsonwebtoken + bcryptjs (авторизация)

Multer (загрузка файлов/фото)

dotenv, cors, helmet (конфигурация и безопасность)

npm (менеджер пакетов)

Структура проекта:

text
server/
  server.js              — точка входа Express
  prisma/
    schema.prisma        — схема БД
  routes/
    auth.routes.js
    orders.routes.js
    tasks.routes.js
    warehouse.routes.js
    dashboard.routes.js
  controllers/
    auth.controller.js
    orders.controller.js
    tasks.controller.js
    warehouse.controller.js
  middleware/
    auth.middleware.js   — проверка JWT
    role.middleware.js   — RBAC по ролям
  utils/
    salary.util.js
    dashboard.util.js
5.2 Пример server.js
javascript
const express = require('express');
const cors    = require('cors');
const helmet  = require('helmet');
const app     = express();

app.use(cors({ origin: process.env.FRONTEND_URL }));
app.use(helmet());
app.use(express.json());

app.use('/api/auth',      require('./routes/auth.routes'));
app.use('/api/orders',    require('./routes/orders.routes'));
app.use('/api/tasks',     require('./routes/tasks.routes'));
app.use('/api/warehouse', require('./routes/warehouse.routes'));
app.use('/api/dashboard', require('./routes/dashboard.routes'));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on ${PORT}`));
5.3 Middleware авторизации (Node)
javascript
// middleware/auth.middleware.js
const jwt = require('jsonwebtoken');

module.exports = (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1];
  if (!token) return res.status(401).json({ error: 'No token' });
  try {
    req.user = jwt.verify(token, process.env.JWT_SECRET);
    next();
  } catch { res.status(401).json({ error: 'Invalid token' }); }
};
5.4 Prisma Schema (фрагмент)
prisma
// prisma/schema.prisma
model User {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  password  String
  role      Role
  masterId  Int?
  master    User?    @relation("master", fields:[masterId], references:[id])
  workers   User[]   @relation("master")
  tasks     Task[]   @relation("worker")
}

enum Role {
  CASHIER REPAIR_MASTER REPAIR_WORKER
  WASH_MASTER WASH_WORKER WAREHOUSE ADMIN
}
6. ТЕХНИЧЕСКИЕ ЗАДАНИЯ ПО РАЗРАБОТЧИКАМ
Разработчик 1 — Тимлид / Архитектор
Задачи:

Создать репозиторий, настроить ветки (main/dev/feature/*)

Разработать схему БД PostgreSQL (все таблицы, индексы, FK)

Составить OpenAPI/Swagger спецификацию всех эндпоинтов

Настроить Docker Compose (PostgreSQL, Redis, PHP/Node, Nginx)

Написать seed-данные для тестирования всех ролей

Настроить CI/CD (GitHub Actions или GitLab CI)

Deliverable: docker-compose.yml, schema.sql, openapi.yaml

Разработчик 2 — Backend PHP (Auth + Orders)
Задачи:

Реализовать Laravel Sanctum: регистрация, логин, логаут, /me

RBAC middleware для всех ролей

CRUD заказов: создание, изменение статуса, история

Модуль платежей: принять оплату, тип, сумма

Интернет-заказы: получить список, изменить статус

Deliverable: AuthController, OrderController, PaymentController, migrations

Разработчик 3 — Backend PHP (Warehouse + Analytics)
Задачи:

Модуль склада: остатки, запросы между складами

CRUD товаров (центральный склад)

Модуль аналитики: дашборд кладовщика, дашборд мастеров

Расчёт зарплаты: SalaryService, выработка × ставка

Экспорт CSV (для отчётов)

Deliverable: WarehouseController, DashboardController, SalaryService

Разработчик 4 — Backend Node.js (Auth + Orders)
Задачи:

server.js с Express: базовая настройка, cors, helmet

JWT авторизация: login, logout, /me, refresh token

routes/auth.routes.js + controllers/auth.controller.js

routes/orders.routes.js — полная реализация Orders API

Middleware: auth.middleware.js, role.middleware.js

Deliverable: server.js, auth.routes.js, orders.routes.js + контроллеры

Разработчик 5 — Backend Node.js (Warehouse + Analytics)
Задачи:

Prisma schema + миграции (все модели)

routes/warehouse.routes.js — запросы, CRUD, выдача

routes/tasks.routes.js — задания ремонт + мойка

routes/dashboard.routes.js — агрегация данных для дашбордов

salary.util.js — расчёт зарплаты

Deliverable: prisma/schema.prisma, warehouse.routes.js, dashboard.routes.js

Разработчик 6 — Frontend React (Кассиры + Магазин)
Задачи:

Страница кассира: поиск товара, корзина, оформление заказа

POS-компонент: сканер штрихкода, кнопки оплаты

Страница онлайн-заказов: список, фильтры, изменение статуса

Адаптивная вёрстка (планшет 768px+, ПК 1024px+)

Интеграция с API: Axios + React Query

Deliverable: pages/Cashier/, components/POS/, hooks/useOrders.ts

Разработчик 7 — Frontend React (Мастера + Рабочие)
Задачи:

Страница мастера ремонта: создание задания, список, дашборд

Страница ремонтника: список своих заданий, кнопка принятия

Страница мастера мойки: аналогично

Страница мойщика: список заданий

Компонент зарплатной ведомости

Push-уведомление о новом задании (опционально)

Deliverable: pages/RepairMaster/, pages/Worker/, pages/WashMaster/

Разработчик 8 — Frontend React (Склад + Дашборды)
Задачи:

Страница кладовщика: таблица позиций, CRUD inline, запросы

Страница мини-склада: остатки, кнопка запроса, история

Общий дашборд: графики (Recharts), KPI-плашки

Компонент фильтров (по дате, категории, складу, статусу)

Экспорт таблицы в CSV

Deliverable: pages/Warehouse/, pages/Admin/, components/Charts/

Разработчик 9 — QA / DevOps
Задачи:

Написать unit-тесты (Jest для Node, PHPUnit для PHP)

E2E тесты (Playwright или Cypress)

Dockerfile для каждого сервиса

docker-compose.yml (dev + prod конфигурации)

README.md с инструкцией запуска

Нагрузочное тестирование ключевых эндпоинтов

Deliverable: tests/, Dockerfiles, docker-compose.yml, README.md

7. ТРЕБОВАНИЯ К АДАПТИВНОМУ ИНТЕРФЕЙСУ
Все интерфейсы должны корректно отображаться на устройствах:

Устройство	Ширина экрана	Роли	Особенности
Смартфон	320–767px	Ремонтник, мойщик	Крупные кнопки, минимум текста
Планшет	768–1023px	Кассир, кладовщик	Таблицы в 2 колонки, боковая панель
ПК/ноутбук	1024px+	Мастера, кладовщик, админ	Полный дашборд, графики
8. ДОРОЖНАЯ КАРТА РАЗРАБОТКИ (8 НЕДЕЛЬ)
Неделя	Backend	Frontend	DevOps / QA
1–2	БД, Auth, базовые модели	Роутинг, авторизация UI, Layout	Docker, CI, seed data
3–4	Orders, Tasks (ремонт+мойка)	Кассир UI, рабочий UI	Unit-тесты Auth
5–6	Warehouse, Salary, Analytics	Мастера UI, склад UI	Интеграционные тесты
7	Оптимизация, экспорт CSV	Дашборды, графики, фильтры	E2E тесты, нагрузка
8	Финальный review	Адаптивность, полировка UI	Деплой, документация
9. СРАВНЕНИЕ ДВУХ СТЕКОВ
Критерий	Стек 1: PHP + Laravel	Стек 2: Node.js + Express
Язык бэкенда	PHP 8.2	JavaScript / Node.js 20
Фреймворк	Laravel 11	Express.js 4
ORM	Eloquent	Prisma
Авторизация	Laravel Sanctum (JWT)	jsonwebtoken
Очереди задач	Laravel Queue + Redis	Bull + Redis
Архитектура API	REST, resource controllers	REST, route-controller
Тестирование	PHPUnit	Jest + Supertest
Frontend	React 18 + Vite	React 18 + Vite (идентично)
БД	PostgreSQL + Eloquent	PostgreSQL + Prisma
Деплой	Apache/Nginx + PHP-FPM	PM2 + Nginx
10. UML-СХЕМЫ
10.1 Диаграмма вариантов использования (Use Case)
text
┌──────────────────────────────────────────────────────────────────┐
│                    PITSTOP MANAGEMENT SYSTEM                      │
│                                                                   │
│  ┌──────────┐     ┌──────────┐     ┌──────────┐                 │
│  │  Кассир  │     │  Мастер  │     │  Мастер  │                 │
│  │   (3)    │     │ ремонта  │     │  мойки   │                 │
│  │          │     │   (3)    │     │   (4)    │                 │
│  └────┬─────┘     └────┬─────┘     └────┬─────┘                 │
│       │                │                │                         │
│       ▼                ▼                ▼                         │
│  ┌─────────┐     ┌─────────┐     ┌─────────┐                    │
│  │Создание │     │Создание │     │Создание │                    │
│  │ заказа  │     │задания  │     │задания  │                    │
│  └─────────┘     └─────────┘     └─────────┘                    │
│       │                │                │                         │
│       ▼                ▼                ▼                         │
│  ┌─────────┐     ┌─────────┐     ┌─────────┐                    │
│  │Приём    │     │Назначе- │     │Назначе- │                    │
│  │оплаты   │     │ние исп. │     │ние исп. │                    │
│  └─────────┘     └─────────┘     └─────────┘                    │
│                        │                │                         │
│                        ▼                ▼                         │
│                   ┌─────────┐     ┌─────────┐                    │
│                   │Ремонтник│     │ Мойщик  │                    │
│                   │  (12)   │     │  (16)   │                    │
│                   └─────────┘     └─────────┘                    │
│                        │                │                         │
│                        ▼                ▼                         │
│                   ┌─────────┐     ┌─────────┐                    │
│                   │Приём    │     │Приём    │                    │
│                   │задания  │     │задания  │                    │
│                   └─────────┘     └─────────┘                    │
│                                                                   │
│  ┌──────────┐              ┌──────────┐                          │
│  │Кладовщик │              │  Админ   │                          │
│  │   (2)    │              │          │                          │
│  └────┬─────┘              └────┬─────┘                          │
│       │                         │                                  │
│       ▼                         ▼                                  │
│  ┌─────────┐              ┌─────────┐                            │
│  │Управле- │              │Дашборды │                            │
│  │ние скла-│              │аналитики│                            │
│  │дом      │              │         │                            │
│  └─────────┘              └─────────┘                            │
└──────────────────────────────────────────────────────────────────┘
10.2 Диаграмма компонентов системы
text
┌─────────────────────────────────────────────────────────────────┐
│                     FRONTEND (React + Vite)                       │
│                                                                   │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐        │
│  │ Кассиры  │  │ Мастера  │  │Работники │  │Кладовщики│        │
│  │   3      │  │   3+4    │  │  12+16   │  │    2     │        │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘        │
│       │              │              │              │               │
└───────┼──────────────┼──────────────┼──────────────┼─────────────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────┐
│                      API Gateway (REST)                           │
│                                                                   │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐        │
│  │  Auth    │  │  Orders  │  │Warehouse │  │Analytics │        │
│  │ Service  │  │ Service  │  │ Service  │  │ Service  │        │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘        │
│       │              │              │              │               │
└───────┼──────────────┼──────────────┼──────────────┼─────────────┘
        │              │              │              │
        ▼              ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────┐
│                       DATA LAYER                                  │
│                                                                   │
│  ┌──────────┐  ┌──────────┐                                      │
│  │PostgreSQL│  │  Redis   │                                      │
│  │  (БД)    │  │ (Cache)  │                                      │
│  └──────────┘  └──────────┘                                      │
└─────────────────────────────────────────────────────────────────┘
10.3 Диаграмма последовательности (создание заказа)
text
Кассир          Frontend         API Gateway       БД
  │                │                 │              │
  │  Выбор товара  │                 │              │
  │───────────────>│                 │              │
  │                │  GET /products  │              │
  │                │────────────────>│              │
  │                │                 │  SELECT      │
  │                │                 │─────────────>│
  │                │                 │<─────────────│
  │                │<────────────────│              │
  │  Формирование  │                 │              │
  │  корзины       │                 │              │
  │───────────────>│                 │              │
  │                │  POST /orders   │              │
  │                │────────────────>│              │
  │                │                 │  INSERT      │
  │                │                 │─────────────>│
  │                │                 │<─────────────│
  │                │<────────────────│              │
  │  Оплата        │                 │              │
  │───────────────>│                 │              │
  │                │  POST /payments │              │
  │                │────────────────>│              │
  │                │                 │  INSERT      │
  │                │                 │─────────────>│
  │                │                 │<─────────────│
  │                │<────────────────│              │
  │  Чек           │                 │              │
  │<───────────────│                 │              │
11. СХЕМА РАСПРЕДЕЛЕНИЯ ЗАДАЧ (UML-ДИАГРАММА РОЛЕЙ)
text
┌──────────────────────────────────────────────────────────────────┐
│                    PITSTOP — РОЛИ И ЗАДАЧИ                         │
│                                                                   │
│                         ┌─────────┐                               │
│                         │  АДМИН  │                               │
│                         │    (1)  │                               │
│                         └────┬────┘                               │
│                              │                                    │
│         ┌────────────────────┼────────────────────┐              │
│         │                    │                    │              │
│         ▼                    ▼                    ▼              │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐        │
│  │  КАССИРЫ    │     │  МАСТЕРА    │     │ КЛАДОВЩИКИ  │        │
│  │    (3)      │     │ ремонта (3) │     │    (2)      │        │
│  │             │     │ мойки   (4) │     │             │        │
│  └──────┬──────┘     └──────┬──────┘     └──────┬──────┘        │
│         │                   │                   │                │
│         ▼                   ▼                   ▼                │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐        │
│  │ Магазин +   │     │  Рабочие    │     │Центральный  │        │
│  │ Интернет-   │     │ ремонт (12) │     │склад        │        │
│  │ магазин     │     │ мойка  (16) │     │             │        │
│  └─────────────┘     └─────────────┘     └──────┬──────┘        │
│                                                  │               │
│                                                  ▼               │
│                                           ┌─────────────┐        │
│                                           │ Мини-склады │        │
│                                           │    (3)      │        │
│                                           └─────────────┘        │
│                                                                   │
│  ┌─────────────────────────────────────────────────────────────┐ │
│  │                    ДАШБОРДЫ АНАЛИТИКИ                        │ │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │ │
│  │  │ Заказы   │  │ Склад    │  │Зарплаты  │  │  KPI     │   │ │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │ │
│  └─────────────────────────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────────────────┘
Документ разработан в рамках образовательного бизнес-проекта. Все технические решения носят рекомендательный характер и могут адаптироваться командой разработки.

Теперь создам производственный фронтенд-интерфейс с уникальным дизайном для дашборда мастера ремонта — одного из ключевых интерфейсов системы. Выбираю направление индустриальный/утилитарный стиль с элементами брутализма.

html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PitStop — Мастер ремонта | Дашборд</title>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Rubik+Mono+One&family=Chakra+Petch:wght@300;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-primary: #0d0f10;
            --bg-secondary: #141719;
            --bg-card: #1a1d20;
            --bg-elevated: #1f2327;
            --border: #2a2e33;
            --border-active: #4a5568;
            --text-primary: #e8edf2;
            --text-secondary: #8b959e;
            --text-muted: #5c656e;
            --accent-green: #3dd68c;
            --accent-green-dim: #1a3a2a;
            --accent-amber: #f5a623;
            --accent-amber-dim: #3a2a1a;
            --accent-red: #e5484d;
            --accent-red-dim: #3a1a1a;
            --accent-blue: #4dabf7;
            --accent-blue-dim: #1a2a3a;
            --accent-purple: #a78bfa;
            --font-mono: 'JetBrains Mono', monospace;
            --font-display: 'Rubik Mono One', sans-serif;
            --font-data: 'Chakra Petch', sans-serif;
            --radius-sm: 2px;
            --radius-md: 4px;
            --radius-lg: 8px;
            --shadow-card: 0 1px 0 0 var(--border), 0 4px 24px rgba(0,0,0,0.4);
            --shadow-elevated: 0 2px 0 0 var(--border-active), 0 8px 40px rgba(0,0,0,0.6);
            --transition-fast: 120ms cubic-bezier(0.4, 0, 0.2, 1);
            --transition-smooth: 250ms cubic-bezier(0.4, 0, 0.2, 1);
            --grain: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-mono);
            background-color: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            line-height: 1.5;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            background-image: var(--grain);
            background-repeat: repeat;
            background-size: 256px 256px;
        }

        /* ─── Scrollbar ─────────────────────────── */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg-secondary);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--border);
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--border-active);
        }

        /* ─── Layout Grid ───────────────────────── */
        .app-shell {
            display: grid;
            grid-template-columns: 260px 1fr;
            grid-template-rows: 56px 1fr;
            grid-template-areas:
                "sidebar header"
                "sidebar main";
            min-height: 100vh;
        }

        /* ─── Header ────────────────────────────── */
        .header {
            grid-area: header;
            background: var(--bg-secondary);
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 24px;
            z-index: 10;
        }
        .header-brand {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .header-logo {
            font-family: var(--font-display);
            font-size: 18px;
            letter-spacing: -0.5px;
            color: var(--accent-green);
            text-transform: uppercase;
        }
        .header-logo span {
            color: var(--text-primary);
        }
        .header-status {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 12px;
            color: var(--text-secondary);
        }
        .status-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: var(--accent-green);
            box-shadow: 0 0 8px var(--accent-green);
            animation: pulse-status 2s infinite;
        }
        @keyframes pulse-status {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        /* ─── Sidebar ───────────────────────────── */
        .sidebar {
            grid-area: sidebar;
            background: var(--bg-secondary);
            border-right: 1px solid var(--border);
            padding: 20px 0;
            display: flex;
            flex-direction: column;
        }
        .sidebar-nav {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 2px;
            padding: 0 12px;
        }
        .sidebar-link {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 14px;
            font-size: 13px;
            color: var(--text-secondary);
            text-decoration: none;
            border-radius: var(--radius-md);
            transition: all var(--transition-fast);
            letter-spacing: 0.3px;
            position: relative;
        }
        .sidebar-link:hover {
            color: var(--text-primary);
            background: var(--bg-elevated);
        }
        .sidebar-link.active {
            color: var(--accent-green);
            background: var(--accent-green-dim);
            font-weight: 500;
        }
        .sidebar-link.active::before {
            content: '';
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 3px;
            height: 20px;
            background: var(--accent-green);
            border-radius: 2px;
        }
        .sidebar-icon {
            width: 18px;
            height: 18px;
            opacity: 0.7;
            flex-shrink: 0;
        }
        .sidebar-link.active .sidebar-icon {
            opacity: 1;
        }
        .sidebar-badge {
            margin-left: auto;
            font-family: var(--font-data);
            font-size: 11px;
            font-weight: 600;
            padding: 2px 8px;
            border-radius: 10px;
            background: var(--accent-red-dim);
            color: var(--accent-red);
            min-width: 24px;
            text-align: center;
        }
        .sidebar-user {
            margin-top: auto;
            padding: 16px;
            border-top: 1px solid var(--border);
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .user-avatar {
            width: 36px;
            height: 36px;
            border-radius: var(--radius-sm);
            background: var(--accent-blue-dim);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 14px;
            color: var(--accent-blue);
            flex-shrink: 0;
        }
        .user-info {
            font-size: 12px;
            line-height: 1.3;
        }
        .user-name {
            color: var(--text-primary);
            font-weight: 500;
        }
        .user-role {
            color: var(--text-muted);
            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 0.6px;
        }

        /* ─── Main Content ──────────────────────── */
        .main-content {
            grid-area: main;
            padding: 24px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 24px;
        }

        /* ─── Stats Grid ────────────────────────── */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 16px;
        }
        .stat-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius-lg);
            padding: 20px;
            position: relative;
            overflow: hidden;
            transition: all var(--transition-smooth);
            cursor: default;
        }
        .stat-card:hover {
            border-color: var(--border-active);
            box-shadow: var(--shadow-card);
            transform: translateY(-1px);
        }
        .stat-card::after {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 4px;
            height: 100%;
        }
        .stat-card.urgent::after {
            background: var(--accent-red);
            box-shadow: 0 0 20px rgba(229, 72, 77, 0.3);
        }
        .stat-card.active::after {
            background: var(--accent-amber);
            box-shadow: 0 0 20px rgba(245, 166, 35, 0.3);
        }
        .stat-card.done::after {
            background: var(--accent-green);
            box-shadow: 0 0 20px rgba(61, 214, 140, 0.3);
        }
        .stat-card.pending::after {
            background: var(--accent-blue);
            box-shadow: 0 0 20px rgba(77, 171, 247, 0.3);
        }
        .stat-label {
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.8px;
            color: var(--text-muted);
            margin-bottom: 8px;
        }
        .stat-value {
            font-family: var(--font-data);
            font-size: 36px;
            font-weight: 700;
            line-height: 1;
            color: var(--text-primary);
        }
        .stat-delta {
            font-size: 12px;
            margin-top: 6px;
            color: var(--text-secondary);
        }
        .stat-delta.up {
            color: var(--accent-green);
        }
        .stat-delta.down {
            color: var(--accent-red);
        }

        /* ─── Panel / Card ──────────────────────── */
        .panel {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius-lg);
            overflow: hidden;
        }
        .panel-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 16px 20px;
            border-bottom: 1px solid var(--border);
            background: var(--bg-secondary);
        }
        .panel-title {
            font-family: var(--font-data);
            font-size: 14px;
            font-weight: 600;
            letter-spacing: 0.4px;
            color: var(--text-primary);
        }
        .panel-actions {
            display: flex;
            gap: 8px;
        }

        /* ─── Buttons ───────────────────────────── */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            padding: 6px 14px;
            font-family: var(--font-mono);
            font-size: 12px;
            font-weight: 500;
            letter-spacing: 0.3px;
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            background: var(--bg-elevated);
            color: var(--text-primary);
            cursor: pointer;
            transition: all var(--transition-fast);
            text-transform: uppercase;
            white-space: nowrap;
        }
        .btn:hover {
            border-color: var(--border-active);
            background: var(--bg-card);
            box-shadow: var(--shadow-card);
        }
        .btn-primary {
            background: var(--accent-green);
            border-color: var(--accent-green);
            color: #000;
            font-weight: 600;
        }
        .btn-primary:hover {
            background: #4de0a0;
            border-color: #4de0a0;
            box-shadow: 0 0 20px rgba(61, 214, 140, 0.3);
        }
        .btn-ghost {
            background: transparent;
            border-color: transparent;
            color: var(--text-secondary);
        }
        .btn-ghost:hover {
            border-color: var(--border);
            background: var(--bg-elevated);
            color: var(--text-primary);
        }
        .btn-icon {
            width: 32px;
            height: 32px;
            padding: 0;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            border-radius: var(--radius-sm);
        }

        /* ─── Table ─────────────────────────────── */
        .table-wrapper {
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 13px;
        }
        thead th {
            padding: 10px 16px;
            text-align: left;
            font-size: 10px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.8px;
            color: var(--text-muted);
            background: var(--bg-secondary);
            border-bottom: 1px solid var(--border);
            white-space: nowrap;
        }
        tbody td {
            padding: 12px 16px;
            border-bottom: 1px solid var(--border);
            color: var(--text-primary);
            font-size: 12px;
        }
        tbody tr {
            transition: background var(--transition-fast);
        }
        tbody tr:hover {
            background: var(--bg-elevated);
        }
        tbody tr:last-child td {
            border-bottom: none;
        }

        /* ─── Badge ─────────────────────────────── */
        .badge {
            display: inline-flex;
            align-items: center;
            padding: 3px 10px;
            font-size: 10px;
            font-weight: 600;
            letter-spacing: 0.5px;
            border-radius: 10px;
            text-transform: uppercase;
        }
        .badge-red {
            background: var(--accent-red-dim);
            color: var(--accent-red);
        }
        .badge-amber {
            background: var(--accent-amber-dim);
            color: var(--accent-amber);
        }
        .badge-green {
            background: var(--accent-green-dim);
            color: var(--accent-green);
        }
        .badge-blue {
            background: var(--accent-blue-dim);
            color: var(--accent-blue);
        }

        /* ─── Worker Status Cards ───────────────── */
        .worker-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
        }
        .worker-card {
            background: var(--bg-elevated);
            border: 1px solid var(--border);
            border-radius: var(--radius-md);
            padding: 16px;
            transition: all var(--transition-fast);
            cursor: pointer;
        }
        .worker-card:hover {
            border-color: var(--border-active);
            box-shadow: var(--shadow-card);
        }
        .worker-card-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
        }
        .worker-indicator {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            flex-shrink: 0;
        }
        .worker-indicator.online {
            background: var(--accent-green);
            box-shadow: 0 0 8px rgba(61, 214, 140, 0.5);
        }
        .worker-indicator.busy {
            background: var(--accent-amber);
            box-shadow: 0 0 8px rgba(245, 166, 35, 0.5);
            animation: pulse-busy 1.5s infinite;
        }
        @keyframes pulse-busy {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.4; }
        }
        .worker-indicator.offline {
            background: var(--text-muted);
        }
        .worker-name {
            font-weight: 500;
            font-size: 13px;
            color: var(--text-primary);
        }
        .worker-task {
            font-size: 11px;
            color: var(--text-muted);
            margin-top: 4px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }

        /* ─── Responsive ────────────────────────── */
        @media (max-width: 1024px) {
            .app-shell {
                grid-template-columns: 1fr;
                grid-template-areas:
                    "header"
                    "main";
            }
            .sidebar {
                display: none;
            }
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            .worker-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        @media (max-width: 600px) {
            .stats-grid {
                grid-template-columns: 1fr;
            }
            .worker-grid {
                grid-template-columns: 1fr;
            }
            .header {
                padding: 0 16px;
            }
            .main-content {
                padding: 16px;
            }
            .stat-value {
                font-size: 28px;
            }
        }

        /* ─── Decorative Grain Overlay ──────────── */
        .grain-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 999;
            opacity: 0.04;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
        }
    </style>
</head>
<body>
    <div class="grain-overlay"></div>

    <div class="app-shell">
        <!-- HEADER -->
        <header class="header">
            <div class="header-brand">
                <span class="header-logo">PIT<span>STOP</span></span>
                <span style="color: var(--text-muted); font-size: 12px;">v2.4.1</span>
            </div>
            <div class="header-status">
                <span class="status-dot"></span>
                <span>СИСТЕМА ONLINE</span>
                <span style="color: var(--text-muted);">|</span>
                <span>СМЕНА #142</span>
                <span style="color: var(--text-muted);">|</span>
                <span>12:34 MSK</span>
            </div>
        </header>

        <!-- SIDEBAR -->
        <aside class="sidebar">
            <nav class="sidebar-nav">
                <a href="#" class="sidebar-link active">
                    <svg class="sidebar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
                    Дашборд
                </a>
                <a href="#" class="sidebar-link">
                    <svg class="sidebar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 5H7a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2h-2"/><rect x="9" y="3" width="6" height="4" rx="1"/></svg>
                    Задания
                    <span class="sidebar-badge">7</span>
                </a>
                <a href="#" class="sidebar-link">
                    <svg class="sidebar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/></svg>
                    История
                </a>
                <a href="#" class="sidebar-link">
                    <svg class="sidebar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
                    Бригада
                </a>
                <a href="#" class="sidebar-link">
                    <svg class="sidebar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="1" x2="12" y2="23"/><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"/></svg>
                    Зарплата
                </a>
                <a href="#" class="sidebar-link">
                    <svg class="sidebar-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/></svg>
                    Склад
                </a>
            </nav>
            <div class="sidebar-user">
                <div class="user-avatar">МР</div>
                <div class="user-info">
                    <div class="user-name">Алексей Петров</div>
                    <div class="user-role">Мастер ремонта</div>
                </div>
            </div>
        </aside>

        <!-- MAIN -->
        <main class="main-content">
            <!-- Stats Row -->
            <div class="stats-grid">
                <div class="stat-card urgent">
                    <div class="stat-label">Срочные / Просрочено</div>
                    <div class="stat-value">3</div>
                    <div class="stat-delta down">▲ 2 за последний час</div>
                </div>
                <div class="stat-card active">
                    <div class="stat-label">В работе</div>
                    <div class="stat-value">8</div>
                    <div class="stat-delta">4 ремонтника заняты</div>
                </div>
                <div class="stat-card done">
                    <div class="stat-label">Выполнено за смену</div>
                    <div class="stat-value">23</div>
                    <div class="stat-delta up">▲ 15% к прошлой смене</div>
                </div>
                <div class="stat-card pending">
                    <div class="stat-label">Ожидают назначения</div>
                    <div class="stat-value">5</div>
                    <div class="stat-delta">Среднее время ожидания: 14 мин</div>
                </div>
            </div>

            <!-- Workers Status -->
            <div class="panel">
                <div class="panel-header">
                    <span class="panel-title">БРИГАДА — СТАТУС</span>
                    <div class="panel-actions">
                        <button class="btn btn-ghost">Все</button>
                        <button class="btn btn-ghost">Онлайн</button>
                        <button class="btn btn-ghost">Заняты</button>
                    </div>
                </div>
                <div style="padding: 16px;">
                    <div class="worker-grid">
                        <div class="worker-card">
                            <div class="worker-card-header">
                                <span class="worker-indicator busy"></span>
                                <span class="worker-name">Иван Соколов</span>
                            </div>
                            <div class="worker-task">Замена тормозных колодок — Ford Focus</div>
                        </div>
                        <div class="worker-card">
                            <div class="worker-card-header">
                                <span class="worker-indicator busy"></span>
                                <span class="worker-name">Дмитрий Волков</span>
                            </div>
                            <div class="worker-task">Диагностика двигателя — Toyota Camry</div>
                        </div>
                        <div class="worker-card">
                            <div class="worker-card-header">
                                <span class="worker-indicator online"></span>
                                <span class="worker-name">Артём Морозов</span>
                            </div>
                            <div class="worker-task">Свободен — ожидает задание</div>
                        </div>
                        <div class="worker-card">
                            <div class="worker-card-header">
                                <span class="worker-indicator online"></span>
                                <span class="worker-name">Сергей Кузнецов</span>
                            </div>
                            <div class="worker-task">Свободен — ожидает задание</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Tasks Table -->
            <div class="panel">
                <div class="panel-header">
                    <span class="panel-title">АКТИВНЫЕ ЗАДАНИЯ — РЕМОНТ</span>
                    <div class="panel-actions">
                        <button class="btn btn-primary">+ Новое задание</button>
                        <button class="btn btn-ghost">Фильтр</button>
                        <button class="btn btn-ghost btn-icon">
                            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
                        </button>
                    </div>
                </div>
                <div class="table-wrapper">
                    <table>
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Описание</th>
                                <th>Авто</th>
                                <th>Исполнитель</th>
                                <th>Приоритет</th>
                                <th>Статус</th>
                                <th>Дедлайн</th>
                                <th></th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td style="color: var(--text-muted);">#RT-284</td>
                                <td><strong>Замена масла и фильтров</strong></td>
                                <td>BMW X5</td>
                                <td>Иван Соколов</td>
                                <td><span class="badge badge-red">Высокий</span></td>
                                <td><span class="badge badge-amber">В работе</span></td>
                                <td style="color: var(--accent-red);">12:30</td>
                                <td><button class="btn btn-ghost btn-icon" style="font-size: 10px;">⋯</button></td>
                            </tr>
                            <tr>
                                <td style="color: var(--text-muted);">#RT-283</td>
                                <td><strong>Диагностика ходовой части</strong></td>
                                <td>Kia Sportage</td>
                                <td>Дмитрий Волков</td>
                                <td><span class="badge badge-blue">Средний</span></td>
                                <td><span class="badge badge-amber">В работе</span></td>
                                <td>14:00</td>
                                <td><button class="btn btn-ghost btn-icon" style="font-size: 10px;">⋯</button></td>
                            </tr>
                            <tr>
                                <td style="color: var(--text-muted);">#RT-282</td>
                                <td><strong>Замена лобового стекла</strong></td>
                                <td>Honda CR-V</td>
                                <td>—</td>
                                <td><span class="badge badge-red">Высокий</span></td>
                                <td><span class="badge badge-blue">Ожидание</span></td>
                                <td>13:15</td>
                                <td><button class="btn btn-ghost btn-icon" style="font-size: 10px;">⋯</button></td>
                            </tr>
                            <tr>
                                <td style="color: var(--text-muted);">#RT-281</td>
                                <td><strong>Шиномонтаж (комплект)</strong></td>
                                <td>Skoda Octavia</td>
                                <td>—</td>
                                <td><span class="badge badge-blue">Средний</span></td>
                                <td><span class="badge badge-blue">Ожидание</span></td>
                                <td>15:45</td>
                                <td><button class="btn btn-ghost btn-icon" style="font-size: 10px;">⋯</button></td>
                            </tr>
                            <tr>
                                <td style="color: var(--text-muted);">#RT-280</td>
                                <td><strong>Ремонт глушителя</strong></td>
                                <td>VAZ 2107</td>
                                <td>—</td>
                                <td><span class="badge badge-green">Низкий</span></td>
                                <td><span class="badge badge-green">Завершено</span></td>
                                <td>11:00</td>
                                <td><button class="btn btn-ghost btn-icon" style="font-size: 10px;">⋯</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </main>
    </div>
</body>
</html>
Этот интерфейс представляет собой дашборд мастера ремонта — одну из ключевых страниц системы PitStop. Дизайн выполнен в индустриально-утилитарном стиле с элементами брутализма: тёмная тема, моноширинные шрифты, зернистая текстура, жёсткие линии, неоновые акценты и минималистичные индикаторы состояния.

Ключевые особенности интерфейса:

Адаптивная сетка (4 колонки → 2 → 1 на мобильных)

Живые индикаторы состояния работников (онлайн/занят/офлайн)

Статистические карточки с цветовой кодировкой срочности

Таблица активных заданий с баджами приоритетов и статусов

Полнофункциональная боковая навигация

Зернистая текстовая оверлей для атмосферы

