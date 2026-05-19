FROM python:3.10-slim

WORKDIR /app

# Установка системных зависимостей для psycopg2 и Pillow
RUN apt-get update && apt-get install -y --no-install-recommends libpq-dev gcc && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Копируем requirements и устанавливаем зависимости
COPY requirements.txt .
RUN pip install --upgrade pip && \
    pip install -r requirements.txt --no-cache-dir

# Копируем весь код проекта
COPY . .

# Команда для запуска Gunicorn (при продакшене)
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]