<div align="center">

# 🚀 DevOps Test Task

### Простое веб-приложение в Docker-контейнерах

[![Docker](https://img.shields.io/badge/Docker-20.10+-blue?style=for-the-badge&logo=docker)](https://www.docker.com/)
[![Python](https://img.shields.io/badge/Python-3.8-green?style=for-the-badge&logo=python)](https://www.python.org/)
[![Nginx](https://img.shields.io/badge/Nginx-alpine-purple?style=for-the-badge&logo=nginx)](https://nginx.org/)

</div>

---

## 📋 Описание

Приложение состоит из двух сервисов:

- **Backend** — HTTP-сервер на Python, отвечающий на запросы
- **Nginx** — reverse proxy, проксирующий запросы к backend

---

## ⚙️ Как это работает

1. Пользователь отправляет запрос на `http://localhost:80`
2. Nginx проксирует запрос на `backend:8080` по имени сервиса
3. Backend обрабатывает запрос и возвращает `"Hello from Effective Mobile!"`
4. Ответ передается пользователю через Nginx

---

## 🚀 Быстрый старт

### Требования

- Docker 20.10+
- Docker Compose 2.0+

### Установка и запуск

```bash
# Клонировать репозиторий
git clone https://github.com/IIldark/devops-test-task.git
cd devops-test-task

# Запустить проект
docker-compose up --build -d

# Проверить статус
docker ps

# Проверить работу
curl http://localhost
Ожидаемый ответ:

text
Hello from Effective Mobile!
📂 Структура проекта
text
.
├── backend/
│   ├── Dockerfile          # Сборка backend-образа
│   └── app.py              # HTTP-сервер на Python
├── nginx/
│   └── nginx.conf          # Конфигурация Nginx
├── docker-compose.yml      # Оркестрация сервисов
├── README.md               # Документация
└── .gitignore              # Исключаемые файлы
🛠️ Используемые технологии
Компонент	Технология	Версия
Backend	Python	3.8-alpine
Web Server	Nginx	alpine
Оркестрация	Docker Compose	2.0+
Контейнеризация	Docker	20.10+
✨ Особенности реализации
🔹 Backend (app.py)
Встроенный HTTP-сервер на http.server

Эндпоинт / возвращает "Hello from Effective Mobile!"

Порт 8080 (не опубликован наружу)

Запуск от non-root пользователя (appuser)

Healthcheck каждые 30 секунд

🔹 Nginx (nginx.conf)
Reverse proxy для backend-сервиса

Порт 80 опубликован на хост

Проксирование всех запросов на backend:8080

Передача заголовков: Host, X-Real-IP, X-Forwarded-For, X-Forwarded-Proto

🔹 Docker Compose
Два сервиса: backend и nginx

Отдельная bridge-сеть app-network

Имена контейнеров: effective-mobile-backend и effective-mobile-nginx

Только порт 80 проброшен наружу

🔒 Безопасность
✅	Мера безопасности
✅	Non-root пользователь в backend-контейнере
✅	Минималистичные Alpine-образы
✅	Backend-порт не доступен с хоста
✅	Read-only volume для конфига Nginx
✅	Изолированная Docker-сеть
✅	Отсутствие секретов в репозитории
🧪 Проверка работоспособности
bash
# Проверка основной функциональности
curl http://localhost

# Проверка статуса контейнеров
docker ps

# Проверка non-root пользователя
docker exec effective-mobile-backend whoami

# Просмотр логов
docker logs effective-mobile-backend
docker logs effective-mobile-nginx
📋 Полезные команды
bash
# Запуск в фоновом режиме
docker-compose up --build -d

# Остановка
docker-compose down

# Остановка с удалением томов
docker-compose down -v

# Логи backend
docker logs effective-mobile-backend

# Логи nginx
docker logs effective-mobile-nginx

# Зайти в контейнер
docker exec -it effective-mobile-backend sh
