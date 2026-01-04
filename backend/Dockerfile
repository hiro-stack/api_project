FROM python:3.11-slim

WORKDIR /app

# mysqlclient ビルドに必要な依存を全て入れる
RUN apt update && apt install -y \
    gcc \
    build-essential \
    pkg-config \
    default-libmysqlclient-dev \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.lock ./

RUN pip install --upgrade pip \
    && pip install -r requirements.lock

COPY . .

CMD ["sh", "-c", "DJANGO_SETTINGS_MODULE=config.settings.development python manage.py runserver 0.0.0.0:8000"]
