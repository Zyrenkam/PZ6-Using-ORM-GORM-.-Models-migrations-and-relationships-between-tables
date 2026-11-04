# ПЗ №6 — Использование ORM (GORM): модели, миграции, связи

**Дисциплина:** Технологии создания программного обеспечения  
**Студент:** Мансуров Р.Ш.  
**Группа:** ПИМО-01-26  
**Дата:** 04.11.2026  
**Тема:** Использование ORM (GORM). Модели, миграции и связи между таблицами.

## Окружение

- **ОС:** Windows 10/11 (PowerShell)
- **Go:** 1.21+
- **PostgreSQL:** 18.6
- **ORM:** `gorm.io/gorm` + `gorm.io/driver/postgres`
- **HTTP-роутер:** `github.com/go-chi/chi/v5`

## Описание

Небольшой REST-сервис на Go с ORM GORM. Модели `User`, `Note`, `Tag` описывают связи 1:N (пользователь → заметки) и M:N (заметки ↔ теги через таблицу `note_tags`). Таблицы создаются автоматически через `AutoMigrate`. Ручки позволяют создать пользователя, создать заметку с тегами и получить заметку вместе с автором и тегами (`Preload`).

## Структура проекта
```bash
pz6-gorm/
├── cmd/
│ └── server/
│ └── main.go # точка входа: подключение, AutoMigrate, запуск сервера
├── internal/
│ ├── db/
│ │ └── postgres.go # подключение к PostgreSQL через GORM + настройка пула
│ ├── models/
│ │ └── models.go # модели User, Note, Tag и связи
│ └── httpapi/
│ ├── router.go # маршруты chi
│ └── handlers.go # обработчики CreateUser, CreateNote, GetNoteByID, Health
├── go.mod
├── go.sum
├── .env.example
├── .gitignore
└── README.md
```
