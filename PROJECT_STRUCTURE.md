# Структура проекта

```
telegram-idle-game/
│
├── 📁 backend/                         # Python Backend
│   ├── 📁 bot/                         # Telegram Bot
│   │   ├── __init__.py                 # Экспорт router
│   │   ├── handlers.py                 # Обработчики команд (/start, статистика и т.д.)
│   │   └── keyboards.py                # Клавиатуры для бота
│   │
│   ├── 📁 config/                      # Конфигурация
│   │   ├── __init__.py                 # Экспорт settings
│   │   └── settings.py                 # Настройки из .env (Pydantic)
│   │
│   ├── 📁 database/                    # База данных
│   │   ├── __init__.py                 # Экспорт db singleton
│   │   ├── db.py                       # Database класс с методами
│   │   ├── schema.py                   # SQL схема и начальные данные
│   │   └── game.db                     # SQLite база (создается автоматически)
│   │
│   ├── 📁 game/                        # Игровая логика
│   │   ├── __init__.py                 # Экспорт game_engine
│   │   └── engine.py                   # GameEngine - расчеты, формулы
│   │
│   ├── 📁 webapp/                      # Web API
│   │   ├── __init__.py                 # Экспорт create_app
│   │   └── api.py                      # REST endpoints для Web App
│   │
│   ├── main.py                         # 🚀 Точка входа (запуск бота + API)
│   ├── .env.example                    # Пример конфигурации
│   └── .env                            # Ваша конфигурация (не в git)
│
├── 📁 frontend/                        # React Web App
│   ├── 📁 src/
│   │   ├── 📁 components/              # React компоненты (будут созданы)
│   │   │   ├── 📁 layout/              # Header, Footer, Tabs
│   │   │   ├── 📁 home/                # Главная страница
│   │   │   ├── 📁 upgrades/            # Магазин улучшений
│   │   │   ├── 📁 minigames/           # Мини-игры
│   │   │   ├── 📁 achievements/        # Достижения
│   │   │   └── 📁 leaderboard/         # Рейтинг
│   │   │
│   │   ├── 📁 store/                   # Zustand state management (будет создан)
│   │   │   ├── userStore.ts            # Состояние пользователя
│   │   │   └── gameStore.ts            # Игровое состояние
│   │   │
│   │   ├── 📁 api/                     # API клиент (будет создан)
│   │   │   └── client.ts               # Axios конфигурация
│   │   │
│   │   ├── 📁 types/                   # TypeScript типы (будет создан)
│   │   │   └── index.ts                # Интерфейсы данных
│   │   │
│   │   ├── 📁 utils/                   # Утилиты (будет создан)
│   │   │   └── format.ts               # Форматирование чисел, времени
│   │   │
│   │   ├── App.tsx                     # Главный компонент (будет создан)
│   │   ├── main.tsx                    # Точка входа (будет создан)
│   │   └── index.css                   # Стили
│   │
│   ├── 📁 public/                      # Статичные файлы
│   │   └── (иконки, изображения)
│   │
│   ├── index.html                      # HTML шаблон
│   ├── package.json                    # NPM зависимости
│   ├── tsconfig.json                   # TypeScript конфигурация
│   ├── vite.config.ts                  # Vite конфигурация
│   └── tailwind.config.js              # Tailwind CSS конфигурация
│
├── 📁 docs/                            # Документация
│   ├── ARCHITECTURE.md                 # Архитектура проекта
│   └── INSTALLATION.md                 # Руководство по установке
│
├── README.md                           # Описание проекта
├── requirements.txt                    # Python зависимости
└── .gitignore                          # Git ignore файл

```

## Файлы Backend (созданы)

### ✅ Конфигурация
- `backend/config/settings.py` - Настройки приложения
- `backend/.env.example` - Пример конфигурации

### ✅ База данных
- `backend/database/schema.py` - SQL схема с 8 таблицами
- `backend/database/db.py` - Database класс с ~30 методами
- Таблицы: users, user_progress, upgrades, user_upgrades, achievements, user_achievements, minigame_attempts, group_stats

### ✅ Игровая логика
- `backend/game/engine.py` - GameEngine класс
  - Расчет офлайн дохода
  - Расчет стоимости улучшений
  - Подсчет общего дохода
  - Награды за мини-игры
  - Проверка достижений
  - Форматирование чисел

### ✅ Telegram Bot
- `backend/bot/handlers.py` - 8 команд + callbacks
  - `/start` - Регистрация
  - `📊 Статистика` - Прогресс
  - `💰 Собрать доход` - Сбор денег
  - `🏆 Рейтинг` - Лидерборд
  - `🎯 Достижения` - Список
  - `ℹ️ Помощь` - Инструкция
- `backend/bot/keyboards.py` - 6 типов клавиатур

### ✅ Web API
- `backend/webapp/api.py` - 10 REST endpoints
  - GET `/api/health`
  - GET `/api/user/{id}/profile`
  - POST `/api/user/{id}/collect-income`
  - GET `/api/upgrades`
  - GET `/api/user/{id}/upgrades`
  - POST `/api/user/{id}/purchase-upgrade`
  - GET `/api/user/{id}/achievements`
  - POST `/api/user/{id}/minigame-result`
  - GET `/api/leaderboard`
  - GET `/api/user/{id}/rank`

### ✅ Главный файл
- `backend/main.py` - Запуск бота и API сервера

## Файлы Frontend (созданы)

### ✅ Конфигурация
- `frontend/package.json` - NPM зависимости
- `frontend/vite.config.ts` - Vite конфигурация
- `frontend/tsconfig.json` - TypeScript настройки
- `frontend/tailwind.config.js` - Tailwind CSS

### ✅ HTML/CSS
- `frontend/index.html` - HTML шаблон с Telegram WebApp SDK
- `frontend/src/index.css` - Основные стили + Tailwind

### ⏳ TODO: React компоненты
Нужно создать компоненты для:
- Home page (баланс, доход)
- Upgrades shop (магазин)
- Minigames (игры)
- Achievements (достижения)
- Leaderboard (рейтинг)

## Документация

### ✅ Созданные документы
- `docs/ARCHITECTURE.md` - Подробное описание архитектуры
- `docs/INSTALLATION.md` - Инструкция по установке

## Что готово к использованию

✅ **Backend полностью готов**
- База данных с полной структурой
- Telegram бот с командами
- Web API для взаимодействия
- Игровая логика

✅ **Frontend настроен**
- Конфигурация готова
- Зависимости определены
- Стили подготовлены

⏳ **Нужно создать**
- React компоненты
- Zustand stores
- API клиент
- TypeScript типы

## Размер проекта

- **Backend**: ~1500 строк кода
- **Frontend**: ~100 строк (конфигурация)
- **Документация**: ~800 строк
- **Всего**: ~2400 строк

## Основные технологии

**Backend:**
- Python 3.10
- aiogram 3.x
- aiosqlite
- aiohttp
- pydantic

**Frontend:**
- React 18
- TypeScript
- Vite
- Tailwind CSS
- Zustand
- Axios

**Database:**
- SQLite3
- 8 таблиц
- Foreign keys
- Индексы

## Следующие шаги разработки

1. ✅ Структура backend - готова
2. ✅ База данных - готова
3. ✅ Telegram bot - готов
4. ✅ Web API - готов
5. ⏳ Frontend компоненты - в разработке
6. ⏳ Мини-игры - в разработке
7. ⏳ Тестирование - в разработке
8. ⏳ Деплой - в разработке
