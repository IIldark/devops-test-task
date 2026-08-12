# DevOps Test Task

## Запуск проекта

```bash
docker-compose up --build -d
Проверка результата
bash
curl http://localhost
Ожидаемый ответ:

text
Hello from Effective Mobile!
Как работает схема
Nginx принимает запросы на порту 80

Nginx проксирует запросы на backend по имени сервиса backend:8080

Backend возвращает ответ "Hello from Effective Mobile!"

Структура
text
.
├── backend/
│   ├── Dockerfile
│   └── app.py
├── nginx/
│   └── nginx.conf
└── docker-compose.yml
